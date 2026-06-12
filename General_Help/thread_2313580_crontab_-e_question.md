---
title: "crontab -e question"
date: 2016-02-13
forum: General Help
---

### Post by neil37 on 2016-02-13
Hi,

I'm using Ubunto 14.04 minimal.

I am trying to use crontab -e with the following...

@reboot sleep 40; /home/ts3user/vpnguard/bot.sh start

I have also tried ...

@reboot sleep 40 && /home/ts3user/vpnguard/bot.sh start

I've also tried replacing the sleep with wait.

But I cannot get either these to work.

If I run the script manually it works fine. So I know the script is working fine.
Can anyone spot what I'm doing wrong?

I need the script to wait for 40 seconds after the system boots up before it loads up.


thanks

---

### Post by ian-weisser on 2016-02-13
How do you know it doesn't work?
What kind of output indicates failure? What kind of output indicates succes?
What kind of output do you actually get?

---

### Post by neil37 on 2016-02-14
Hi,

Because after waiting the script does not launch.

Other than that I am unsure on how to check if it is working.
I'm quite new to linux so I don't know how to check for logging etc.

---

### Post by CaptainMark on 2016-02-14
I'm no cron expert but two tips for trouble shooting I have for you,

Firstly I've found cron to not handle either && or ; very well within the crontab itself, you should make a script containing these characters and have cron just run the script, I dont know if thats a definite problem but I've found cron to be unpredictable when using these in the tab

Secondly, add lots of debugging lines to your scripts so you can tell exactly where your commands are failing for example:

```

#!/bin/bash

echo "Script started $(date +%s)" >> ~/log.txt
command 1
echo "Command 1 finished $(date +%s)" >> ~/log.txt
command 2
echo "Script finished $(date +%s)" >> ~/log.txt
exit 0

```
This creates a log with time stamps along each step of the script and that way you can tell if you script is running at all, if it is running where its failing, I sometimes do this even if my script is one single line long, it still helps, a lot.

---

### Post by ian-weisser on 2016-02-14
> **neil37 said:**
> Because after waiting the script does not launch.
Right. How are you determining that the script did (or did not) launch?

It may seem like a silly question...but there are threads here where the answer turned out to be 'It's working just fine.'
There are other threads where the querant expected feedback on their display...which a @reboot cron job cannot do.
There are yet other thread where the querant typoed the cron job.
And others where the job launched properly, but crashed due to an entirely different issue (permissions, display, network-not-up, etc)....

The more information you can provide up front, the fewer blind alleys we will steer you down.

CaptainMark's advice on adding logging to your scripts on general principles is excellent; I do that too.

---

### Post by neil37 on 2016-02-14
Hi,

I've been looking around and from what I can see I need to put the script in the init.d folder?
I'm not sure how I would write a start up script.

Would this do the trick...
#!/bin/bash

echo "Script started $(date +%s)" >> ~/log.txt
sleep 40
echo "Command 1 finished $(date +%s)" >> ~/log.txt
./home/ts3user/vpnguard/bot.sh start
echo "Script finished $(date +%s)" >> ~/log.txt
exit 0

In the init.d folder I just CHMOD it to 755 and then call the script using
./etc/init.d/scriptname

Maybe the script does not even need to go in the init.d folder?

EDIT:
Sorry to be such a n00b.

---

### Post by ian-weisser on 2016-02-14
Did you make your script executable? If not, it won't execute.

There are *lots* of ways to trigger an action at boot.
@reboot is one way
/etc/init.d is a completely different and unrelated way.

If you wish to use @reboot, then your script can be anywhere in the filesystem. It need not be in /etc/init.d (indeed, that would be confusing).

If you wish to abandon the cron method and use init, then the release of Ubuntu matters.
Ubuntu 10.04, for example, used sysvinit. 12.04 and 14.04 use Upstart. 16.04 uses systemd.
sysvinit, Upstart, and systemd tasks all have diffent syntaxes, and are stored in different locations, and use different triggers. Each offers a level of sysvinit compatibility...but your script is not properly written for sysvinit yet anyway.

---

### Post by neil37 on 2016-02-14
Hi,

Does the script above look right?

I've just done that from what I think "looks" right based on what I've seen so far on forums and sites.

So would it be like this..


echo "Script started $(date +%s)" >> ~/log.txt
sleep 40
echo "Command 1 finished $(date +%s)" >> ~/log.txt
./home/ts3user/vpnguard/bot.sh start
echo "Script finished $(date +%s)" >> ~/log.txt
exit 0

And if I place that in..

/home/username/ folder then call that from crontab it should work?
I need to make the script 755 or 777 for it to work? I though 755 was ok?

---

### Post by CaptainMark on 2016-02-14
I recommend sticking with the @reboot option because it's an easy way launch scripts as a specific user at boot time. The permissions 755 will likely work best for you in this situation, unless you want other people to be able to modify your script.

---

### Post by neil37 on 2016-02-14
Will the above script example work? Does it look like it is going to work?

Where will the log file be placed?

Thanks

---

### Post by ian-weisser on 2016-02-14
Why not try it and find out?

Your logs will be placed where you told the script to put it....'~/log.txt'
'~' means in your home directory.

Why are you appending to the old log each time? That will get confusing quickly. Do you want to keep old debugging logs?

---

### Post by neil37 on 2016-02-14
> **ian-weisser said:**
> Why not try it and find out?

Your logs will be placed where you told the script to put it....'~/log.txt'
'~' means in your home directory.

Why are you appending to the old log each time? That will get confusing quickly. Do you want to keep old debugging logs?

The log reference you made was made by another user which I've taken on board and was going to try. The ~ means nothing to me
as I have no clue what it means.
As I have already explained I'm new. So I'm learning as I go.

---

### Post by ian-weisser on 2016-02-14
> **neil37 said:**
> As I have already explained I'm new. So I'm learning as I go.

We have people with a wide range of experiences and assumptions who describe themselves as 'new.' It can be difficult to gauge from a few lines of text what their experience and knowledge really is.

You have chosen a fairly steep first project for Ubuntu. It requires an understanding of how the system boots, how cron works, permissions, scripting, etc. 
We are trying to steer you in an appropriate direction without overwhelming you.

We cannot tell from here if your script will work and your bot will start. It *looks* fine from here, but we don't know if your script is executable. We don't know what strange haywiring you may have not mentioned or other assumptions you may have made. We don't know anything about your bot, nor what services it requires, nor why it failed when launched directly from cron. We can tell a lot from the error messages and log entries, so try it and show us the errors.

---

### Post by neil37 on 2016-02-14
> **ian-weisser said:**
> We have people with a wide range of experiences and assumptions who describe themselves as 'new.' It can be difficult to gauge from a few lines of text what their experience and knowledge really is.

You have chosen a fairly steep first project for Ubuntu. It requires an understanding of how the system boots, how cron works, permissions, scripting, etc. 
We are trying to steer you in an appropriate direction without overwhelming you.

We cannot tell from here if your script will work and your bot will start. It *looks* fine from here, but we don't know if your script is executable. We don't know what strange haywiring you may have not mentioned or other assumptions you may have made. We don't know anything about your bot, nor what services it requires, nor why it failed when launched directly from cron. We can tell a lot from the error messages and log entries, so try it and show us the errors.

Hi,

I know how to make it executable. I just needed to know if the script looked like it was going to work.

I will give it a try. Thanks for your help.

---

