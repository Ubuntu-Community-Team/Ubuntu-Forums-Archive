---
title: "Send SSMTP Message From Script"
date: 2017-07-31
forum: General Help
---

### Post by brenneke on 2017-07-31
I have a Cron job that successfully calls a script, this works. I have ssmpt installed and configured with my gmail account - if I enter the following in terminal, I do get the email message, this works too.

```
/usr/sbin/ssmtp myemail@gmail.com </home/mybox/myscripts/msg.txt
```

I thought I could just add this same line in my Cron job script and when that script runs it would also send an email, but this does not work. How can I add a line in my Cron job script so this will work?

---

### Post by TheFu on 2017-07-31
cron doesn't provide much environment.  You need to figure out the difference between YOUR environment and what cron provides, then set the correct variables as needed manually.

Also, the cron job probably isn't using your normal userid at runtime, so don't just copy all the env settings. It could cause issues - especially if root is the effective userid for the cron job.

---

### Post by brenneke on 2017-07-31
I appreciate you helping TheFu but, I did not understand anything you said! I am sure this is really simple but I really have limited knowledge with this and am trying to learn. I have a cron job that runs a script and it all works. I have ssmtp setup and working with gmail. I have a message file that I can successfully send with ssmtp from terminal. I just need to know how to modify my functioning cron job script so it also sends this message file when it runs.

---

### Post by TheFu on 2017-07-31
We don't know what you know.  I assumed more knowledge than you currently have. Sorry. Not a big deal. We all weren't born knowing this stuff. ;)

```
$ env > /tmp/bash.env
```

What does that show?

Now, make the same program run from the the same crontab. 
```
env > /tmp/cron.env

```

See the difference in output?  There are probably a few things that ssmpt requires which aren't set correctly in your script.  Don't just set everything. Only set things that matter.

---

### Post by brenneke on 2017-07-31
When I enter first line in terminal I get command not found. When I enter the same without the dollar sign I get nothing, just returns me to the prompt.

---

### Post by TheFu on 2017-07-31
Did you look in the files created?

Unix has a method. Only when something bad happens, does it say anything.

$ - is a way of saying "run this as a normal user"
# - is a way of saying "run this with root privileges" - or use sudo.

Search for "The Linux Command Line" and read the first 150 pgs or so to gain an understanding of these basic things.

---

### Post by brenneke on 2017-07-31
I did try both as normal user and as root, both returned me back to the prompt:

```
/gw@GW:~$ env > /tmp/bash.env
gw@GW:~$ sudo env > /tmp/bash.env
[sudo] password for gw: 
gw@GW:~$
```


I really don't know what you are trying to say. Yes I will read more about this to learn but it sounds like you are missing the point that my script does run from crontab and and it works, just asking how to write a line(s) into an existing working script to send a message from a file that also works when run it from terminal. I just do not yet know enough about scripting to do this.  

Like I said in OP, if I type this is terminal, my message file sends successfully. I am sure one does not have to be a scripting genius to use this to run it from an already functioning script.

```
/usr/sbin/ssmtp myemail@gmail.com </home/mybox/myscripts/msg.txt
```

---

### Post by TheFu on 2017-07-31
I understand.

You are missing the point.

In short, the environment variables for cron don't include things that are needed. Those variables appear to be set in an interactive shell. That is why it works under a terminal, but not via cron. Comparing the environments is the logical step.  Make sense?

After you figure out the differences, you can set those variabled in the script that gets called by cron and everything will work.  This is a common thing for scripts run from cron.  ALL OF THEM have this issue, so understanding how to solve the problem in a general way is extremely useful.

Every program runs under an "environment."  There are environment variables which are set differently in an interactive terminal that do not get set with cron is used.  This is the same on Windows. This is the same on iOS, Android, Unix, OSX ... there are environment variables missing.

Maybe a ssmtp guide explains the required variables?  I don't know.  I don't use it and didn't google for the answer; assume you already did that.  ssmtp seems like a reasonable solution for your needs, I've just never used it.  I won't use google services.

---

