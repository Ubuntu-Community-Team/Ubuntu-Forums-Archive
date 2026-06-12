---
title: "reminder script"
date: 2007-06-11
forum: General Help
---

### Post by Donnieb on 2007-06-11
I am fairly new to all of this but I got the crazy idea to make a script that sends an email to me at the start of each month reminding me to pay my bills, My idea is to set up the script to check against a database of websites/usernames and then send an email containing that information. Is this possible to do in bash script or will I have to use a higher scripting lanaguage like perl or php? Also, any pointers on where to go to research this?

---

### Post by strider1551 on 2007-06-11
Sounds like fun.  I've learned a lot myself by doing projects that I have no idea how to do at the start.

First off, I should say that I know very little bash but a lot more about python.  Nevertheless, my instincts on this one is to use a higher language like python.  It sounds like at the very least you will need to parse html files and send emails, which might be a little much for bash.  But like I said, I'm the last person who can really answer that question.

Secondly, have you thought about how to schedule the execution of the script?  If you use cron, and your computer happens to be turned off at the set time one month, you won't get the notice.  I suppose you could make the script a daemon and have it check if it ran for the current month every six hours or so...

If you're doing this in python, get comfortable with [smtplib]("http://docs.python.org/lib/module-smtplib.html") and [urllib2]("http://docs.python.org/lib/module-urllib2.html").  Whatever you decide to do, Google is your friend for research.  Think of the next step that you need to learn how to do, such as send email.  Google "nameoflanguage tutorial send email".

---

### Post by stylishpants on 2007-06-12
Not to discourage you from learning more about programming, but you will get a lot more value for your time using a good calendar site like google calendar or 30boxes.com.

This solves the "always on or the email doesn't get sent" problem, and also lets you add stuff through a nice and well-though out user interface, AND lets you access it from anywhere which is a huge benefit for a calendar program.

I get my visa bill in the mail on the 5th, I enter the amount on the day it's due in my 30boxes.com account, and I have an email reminder coming to me automatically the day before it's due.  I can pay it from work because whenever my paycheque comes through, the amount of the bill is available right there in my calendar.  

I have found this to quickly become as indispensable to me as email is.  

It's better than a planner because it emails me and I don't have to remember to carry it between home and work.

---

### Post by Mr. C. on 2007-06-12
man cron
man crontab

MrC

---

