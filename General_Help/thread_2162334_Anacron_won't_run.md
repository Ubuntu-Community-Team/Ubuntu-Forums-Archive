---
title: "Anacron won't run??"
date: 2013-07-14
forum: General Help
---

### Post by Singtoh on 2013-07-14
Hello All,

I am having a problem getting anacron to run properly on ubuntu 13.04 64bit on a laptop. I have my backup script in cron.daily and can schedule a cron job with no problems and it all finishes ok. My backup script is called homebackup without the .sh as I read that the .sh can cause problems. The anacron does run at 07:30 every morning without problems but if my laptop isn't turned on at that time then I thought that whenever I turn the computer back on that anacron was suppose to run any job that hasn't been run yet?? This isn't happening for me, I can go all day and periodacally check if it did the backup and it allways never does?? The next morning at 07:30 anacron runs again, provided my computer is turned on?? I thought after a reboot it was suppose do do all unfinished jobs?? Any ideas?? and thanks in advance for any pointers on how to get anacron to run.

Cheers,

Singtoh

---

### Post by CaptainMark on 2013-07-14
It should work like you're expecting, check the file /etc/anacrontab and make sure you have the line "1	5	cron.daily	run-parts --report /etc/cron.daily" 
I doubt it's missing unless you've removed it accidentally but this could be a cause, also to further diagnose the problem check the file /var/spool/anacron/cron.daily which should tell you when anacron thinks it last run the cron.daily scripts, you need sudo just to read it and the format is YYYYMMDD.
Finally using```
ls -l /etc/cron.daily/
```Check your script is:
a) executable, by the owner
b) owned by root

---

### Post by Singtoh on 2013-07-14
> **CaptainMark said:**
> It should work like you're expecting, check the file /etc/anacrontab and make sure you have the line "1    5    cron.daily    run-parts --report /etc/cron.daily" 
I doubt it's missing unless you've removed it accidentally but this could be a cause, also to further diagnose the problem check the file /var/spool/anacron/cron.daily which should tell you when anacron thinks it last run the cron.daily scripts, you need sudo just to read it and the format is YYYYMMDD.
Finally using```
ls -l /etc/cron.daily/
```Check your script is:
a) executable, by the owner
b) owned by root

Hello CaptainMark,

Thanks for the reply:D i have checked all that you said to check and all seems to be in order /etc/anacrontab is as you wrote and sudo gedit /var/spool/anacron/cron.daily returns this: 20130714 which is today and here is the output of ls -l /etc/cron.daily: "rwxrwxr-x 1 root root   799 Jul 12 21:06 homebackup" the output is more than that but this is just for my backup script. I guess the permissions are ok, when I put the script in cron.daily I did a sudo chmod +x on it. I am at a loss here, I have been trying for a few days googling and haven't found the answer yet. And the system log says anacron[1197]: Anacron 2.3 started on 2013-07-14 and then anacron[1197]: Normal exit (0 jobs run) and thats after a reboot. Does the above look ok Mark??

Cheers,

Singtoh

---

### Post by CaptainMark on 2013-07-14
I found this old bug on launchpad [https://bugs.launchpad.net/ubuntu/+source/anacron/+bug/411796](https://bugs.launchpad.net/ubuntu/+source/anacron/+bug/411796) its a very odd one, but it could be the cause.

The next thing I would do in your case would be to place the simplest possible script in cron.daily and see if it runs, I usually go for this one```
#!/bin/bash

date > /home/mark/crontest
```If that runs okay by tomorrow it could be your script thats the problem, (although you think its probably ok, for example the main pitfall is that anacron runs as root so any instances of "~/" or "$HOME" will be expanded into "/root/" not your home folder)

If it all runs okay then I'm a bit stumped, to work around you could always move the script out of cron.daily and give the script its own anacron line "1    15    backup    /home/singtoh/homebackup" or something similar, or as a last alternative just use start-up applications (depending on your desktop environment) to run the script when ever you log in (or add a bit to the start of the script to exit if its already been run today)

Hope this helps
Mark

---

### Post by Singtoh on 2013-07-14
Ok Mark, I'll check it out when I get back to my computer later and post back. Thanks Mark,
Cheers,
Singtoh

---

### Post by Cheesehead on 2013-07-14
> **Singtoh said:**
> And the system log says anacron[1197]: Anacron 2.3 started on 2013-07-14 and then anacron[1197]: Normal exit (0 jobs run) and thats after a reboot.

That means anacron is working properly.
Anacron is clever - it won't run every job after a reboot. It tracks the jobs it runs.
The problem is with your script, not anacron.

CaptainMark is right: The #1 problem is incomplete pathnames in the script.
If that does not fix your problem, then post your script here. Use CODE tags, of course, to make it readable.

---

### Post by Singtoh on 2013-07-14
> **Cheesehead said:**
> That means anacron is working properly.
Anacron is clever - it won't run every job after a reboot. It tracks the jobs it runs.
The problem is with your script, not anacron.

CaptainMark is right: The #1 problem is incomplete pathnames in the script.
If that does not fix your problem, then post your script here. Use CODE tags, of course, to make it readable.

Hello Cheeshead,

Thanks for the reply. Just got back home to my computer. I guess it is running properly now, what I did was delete the timestamp(i guess that is wat it is) in /var/spool/anacron/cron.daily and did a reboot and after the 5 minute delay all the backup scripts in cron.daily ran thru with no problem other than this: singtoh-pc anacron[1224]:Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 255. I guess this mail error means that mail is not setup properly, not sure on that one?? Not really sure if deleting the timestamp was the problem though because I was assuming  that if a job didn't run, that at next boot it would run, but if the time  stamp says anacron ran that day already I guess it wouldn't run till  the next day at 07:30 or whenever the machine is booted?I guess the "mail error" isn't really a problem, I am just happy the anacron is doing what it's suppose to do. Thanks for the help and advice CaptainMark & Cheesehead, it's allways pretty cool when I can post and get some help on some of these things:D

Cheers,

Singtoh

---

### Post by CaptainMark on 2013-07-15
Your quite right, with anacron it counts running all scripts in cron.daily as one job, so if anacron runs the contents of cron.daily at 8am and then you add a script into cron.daily at 9am, that script wont run until earliest of midnight the following morning, as far as anacron thinks it's run cron.daily already today so it wont do anything with it until tomorrow

---

### Post by Singtoh on 2013-07-15
Ok, thanks for the help Mark and Cheesehead. It's working that's a good thing and now I can shut my computer down and know that my scripts will run after I start it again. I really appreciate the replies and help:)

Cheers,
Singtoh

---

### Post by Cheesehead on 2013-07-15
> **Singtoh said:**
> Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 255. I guess this mail error means that mail is not setup properly

Cron tries to e-mail errors to the sysadmin, and this error message is telling you why cron failed and why.
The sendmail error occurs because a smtp Mail Transport Agent (MTA) is not included with the default install of Ubuntu (for several very good reasons). 

You have three choices:
1) You can ignore the error. It won't harm your system.
2) You can install an MTA so you receive the cron emails (which can be very helpful). One example of how is at [http://thinkinginsoftware.blogspot.com/2011/10/cron-error-email-notification-in-ubuntu.html](http://thinkinginsoftware.blogspot.com/2011/10/cron-error-email-notification-in-ubuntu.html)
3) You can stop the email attempt by redirecting cron email to /dev/null. Example at [http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/](http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/)

---

### Post by Singtoh on 2013-07-15
Ok, thanks for the extra info CheeseHead, I'll set it so as to see any errors and such just for giggles I guess.  That will be a good thing I think.

Cheers and thanks again,
Singtoh

---

