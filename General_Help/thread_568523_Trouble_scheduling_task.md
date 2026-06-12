---
title: "Trouble scheduling task"
date: 2007-10-05
forum: General Help
---

### Post by puffyzacd on 2007-10-05
Hey guys,

I'm kinda a newbie to linux, but I'm trying to figure everything out. I've been working for a while on this one thing and I'm not having much luck, maybe someone here can help!

I want to schedule the computer to be locked down every 2 days...So I tried to use anacron to run gnome-screensaver-command -l, no dice. I think this is because anacron runs everything as root, and the command needs to be run by me (it works from the terminal when I run "gnome-screensaver-command -l"). I tried using sudo -u to run it as my username, but this doesn't even work from the terminal. It says "Sorry, user zac is not allowed to execute '/usr/bin/gnome-screensaver-command' as zac on ubuntu." :confused:

Anyway, does anyone have some advice about this? Or an alternative method?

Thanks!

-Zac

---

### Post by dcstar on 2007-10-06
> **puffyzacd said:**
> Hey guys,

I'm kinda a newbie to linux, but I'm trying to figure everything out. I've been working for a while on this one thing and I'm not having much luck, maybe someone here can help!

I want to schedule the computer to be locked down every 2 days...So I tried to use anacron to run gnome-screensaver-command -l, no dice. I think this is because anacron runs everything as root, and the command needs to be run by me (it works from the terminal when I run "gnome-screensaver-command -l"). I tried using sudo -u to run it as my username, but this doesn't even work from the terminal. It says "Sorry, user zac is not allowed to execute '/usr/bin/gnome-screensaver-command' as zac on ubuntu." :confused:

Anyway, does anyone have some advice about this? Or an alternative method?

Thanks!

-Zac

You cannot run X commands from cron unless you have the actual X session screen to be used specified in the environment.

Do a search for running graphical X apps from cron, there should be numerous posts to solve the problem.

---

### Post by Herman on 2007-10-06
Yes puffyzacd, dcstar is right, you need the **export** variable, check this link out,  [crontab: How to run GUI programs with cron]("http://www.ubuntuforums.org/showthread.php?t=185993")

It works for me, my computer wakes me up every morning with Totem Movie Player playing a music file for me, I set it up with crontab.
I used to need to boot into KDE before that, for Kalarm.

Regards, Herman :)

---

### Post by puffyzacd on 2007-10-06
Thanks for the help both of you, I think this solved one of the problems I'm having.

However, I'm still having trouble running this job. I made a test crontab file which looks like this:

```
* * * * * export DISPLAY=:0 && /usr/bin/gnome-screensaver-command -l
```

As was suggested, I added the export DISPLAY=:0 part in order to run the GUI app from cron. The above runs every minute (according to the /var/log/syslog file), but my screen does not lock up. I wish I could provide more information, is there a way to debug the output from the commands cron runs?

Thanks again for your help!

-Zac

---

### Post by Herman on 2007-10-06
Well I have been trying for hours now and you're right, it runs fine from a regular terminal, but I can't seem to get it to run from crontab either.
I have other tasks running from crontab, so we should be able to get this one running to (eventually).

I tried editing /etc/crontab and running it from my username and as root, neither worked.

I tried making a script with the command: gnome-screensaver-command -l
in it too, and running that from crontab to I can run the command indirectly. That didn't work either.
The script itself works okay whenever I run it the normal way.

I did also try something blindingly simple that works fine!
I went 'System'-->'Administration'-->'Screensaver', and opened the Screensaver Preferences window.
There I marked the box for 'Activate the screensaver when the computer is idle', with an X.
I also marked 'Lock screen when screensaver is active'
That was a simple way to get the screen to lock, but it's only possible to set the timer for it for  between one minute and two hours, not two days.
However, it does seem to at least partially satisfy your requirements.

SO far I have been unable to come up with anything better.
Regards, Herman :)

---

### Post by puffyzacd on 2007-10-06
Thank you Herman for all your hard work! I only wish we had more to show for it. :(

My subsequent efforts have proved fruitless as well, so I think I'm about ready to give up on gnome-screensaver-command and start looking for an alternative way to get something like this up-and-running.

I'll come back and leave a post if I figure something out.

-Zac

---

### Post by Herman on 2007-10-06
Yes, me too ' I'm still trying, I'm reading the man page for the 'at' command right now,  The 'at' command looks a bit promising so far....
Maybe the 'at' command is what we're looking for. :)

---

### Post by Herman on 2007-10-06
YAY! :guitar:
I think I have made a step in the right direction, I used the 'at' command to schedule my shell script to run our '/usr/bin/gnome-screensaver-command -l' command and it seems to be working well for me! :)

Here is an example of my shell script (probably most of us already know, but just for the benefit of those who might not be sure),
1. Open a blank gedit text editor page and name it 'lockscreen.sh'.
```
sudo gedit lockscreen.sh
```Type in or copy and paste the following text,```
#!/bin/bash
/usr/bin/gnome-screensaver-command -l
```Save and close the file.
Make it executable, (by giving it the right file permissions)
```
sudo chmod 0755 lockscreen.sh
```Okay, now for the 'at' command that will run the lockscreen.sh script,
```
at 14:00 < lockscreen.sh
```NOTE: you can substitute and time you like for '14:00'
I have tested that a few times already, now all we need to do is get is practice with it some more and learn how to set it to any times and dates we like.
To see what time formats the 'at' comamnd will accept we need to read the file: /usr/share/doc/at/timespec,
```
cat /usr/share/doc/at/timespec
```I think we're on the home stretch now!  :lolflag:

Regards, Herman :)

---

### Post by HermanAB on 2007-10-06
The cron system has a very limited environment.  When you call a program from a cron script, then you always have to supply the full path.

The at system is different, it runs with the environment of the user that called it.

Cheers,

Herman

---

### Post by Herman on 2007-10-07
Hey, thanks Herman! :)

Do you know how to program this to run every two days? I am still trying to work out how to do that part of it now.
So far I have made another script and I named it: at_command.sh, it contains (as you might guess), an 'at' command that is supposed to in turn run the lockscreen script.

Now, what I am testing is this, the at_command.sh script has two commands in it, one to activate the other script right away, and another command to re-activate its-self (recursively), at a given time interval.
For example, 
```
#!/bin/bash

at now < lockscreen.sh
at now + 5 minutes < at_command.sh
```He-he, if it will work every five minutres I'm optimistic we can just change that to 'now + 2 days' and we'll be all set! :)

Do you think it will work? :)

Regards, Herman  :)

---

### Post by Herman on 2007-10-07
Well it seems to be working really well, in fact it's getting to be a jolly nuisance! :)

But what I did do is make it slighly tidier, in fact we don't need two separate scripts, just the single 'lockscreen.sh script will do, I added the line to that one to make it repeat itself automatically instead, so here's the finished product,
```
#!/bin/bash

at now + 2 days < lockscreen.sh
/usr/bin/gnome-screensaver-command -l
```That's it, but we'll have to wait at least two days to see if it will work every two days or not, but I expect it will.
The five minute version is working fine for me.

Regards, Herman :)

---

