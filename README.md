# A/B Testing


## Overview

A/B testing is a user research technique, which is used to test
whether the A or B version is a better design.

We'll be analyzing the following metrics to see which version performs better:  
* __Time to Completion:__	the time it takes to complete the desired task (in this case, put >$150 worth of cacti in your cart)  
* __Time to Click:__  		the time it takes for the first click to occur on the interface. 
* __Return Rate:__		the number of times a user returned to the page (e.g. if the user goes to the cart page, then back to the main shopping page)


## What does this project do?

This project does simple A/B testing of 2 versions of a website.
The metrics collected could then be used to see which version
among the baseline(A) or variant(B) performed better.

Next studio, you'll be acting as users for eachother's website, 
which will give you the data you need to perform the analysis. 
The users will be given the task "Add >$150 worth of cacti to 
your cart. You can see the total by clicking on the cart icon."
Keep this in mind when making your changes!


## Steps
1. Modify Version A and B of the website by editing the `A.html` and `B.html` files found in the `/templates` folder. Your changes do not have to be drastic, but think about how they will affect the above metrics. *Feel free to change the items from cacti to something else, but you must keep the ids the same.*
2. You can open the html files to check your changes, but since this is a flask app, the page naviagation will only work if you run the app locally using the following commands from your 1300ABTesting folder:  
`export FLASK_APP=app.py`  
`flask run`  
3. Deploy it on heroku following our [deployment guide](https://docs.google.com/document/d/10gUVRN74JkL6Iqw3w_XEPcAaQkZFqlXYTRX-XFk51yk/edit). Ignore the cs1300 template - you'll be deploying this git repo.
4. Verify that navigating to your URL will open version A 50% of the time, and version B the other 50%. Click around and check if the cart page is working.
5. Check if the logs are working properly. From the 1300ABTesting folder, run the following command to extract the logs into a text file `mylog.txt`.  
Mac: `heroku logs --app=<your-app-name> -n 1500 > mylog.txt`  
Windows: `heroku logs --app=<your-app-name> -n 1500 | Out-File mylog.txt`  
After you hit enter, you’ll see a blank line at the bottom of your terminal, which means that the command is running.
Once the command has finished, if you look at the created text file (`mylog.txt` in the above example), there’s a lot of information we don’t need. To get just the lines of data that we want for this project, run:  
Mac: `grep AB_TEST mylog.txt > myfilteredlog.txt`  
Windows: `Get-Content mylog.txt | Select-String -Pattern "AB_TEST" | Out-File myfilteredlog.txt`  
Open `myfilteredlog.txt` and verify that you have logs. They should look something like the sample output included below.  
6. __IMPORTANT:__ Fill out [this form](https://forms.gle/nc6TnRaZevUAQtzT9) with your deployed URL. 


## Important Notes
1. Do not copy and paste code between `A.html` and `B.html`, because this could interfere with logging and ruin your analysis!
2. Feel free to change the items from cacti to something else, but you must keep the ids the same.

## Sample output after hosting in heroku.
2017-09-22T04:15:05.318219+00:00 app[web.1]: AB_TESTING: A 1506053696735 1506053705304 mp1 1506053696475
2017-09-22T04:15:07.288130+00:00 app[web.1]: AB_TESTING: A 1506053696735 1506053707279 mp2 1506053696475
2017-09-22T04:15:08.353015+00:00 app[web.1]: AB_TESTING: A 1506053696735 1506053708343 mp2 1506053696475
2017-09-22T04:15:09.444328+00:00 app[web.1]: AB_TESTING: A 1506053696735 1506053709431 mp1 1506053696475
2017-09-22T04:15:14.822574+00:00 app[web.1]: AB_TESTING: B 1506053712624 1506053714784 ca1 1506053712526
2017-09-22T04:15:16.682459+00:00 app[web.1]: AB_TESTING: B 1506053712624 1506053716671 ca2 1506053712526
2017-09-22T04:15:17.769221+00:00 app[web.1]: AB_TESTING: B 1506053712624 1506053717759 ca1 1506053712526
