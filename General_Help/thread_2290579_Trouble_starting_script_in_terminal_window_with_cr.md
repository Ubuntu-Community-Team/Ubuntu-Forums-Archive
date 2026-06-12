---
title: "Trouble starting script in terminal window with cron"
date: 2015-08-13
forum: General Help
---

### Post by BuskJan on 2015-08-13
Hi! I have tried to start a shellscript once a day in a terminal window but i can not make it work.

The job runs but i cant se no terminal. I tried to start gedit just to eliminate errors in the script.
I have verified that the job starts via journalctl | grep cron. Export or env doesn't work. I have tried DISPLAY=:0.0 and DISPLAY=0.

Any help would be appreciated! 

Here is what i have written i crontab:

```
*/01 * * * * env DISPLAY=:0 gedit
```

---

### Post by Lars Noodén on 2015-08-13
The 'env' is interfering.  Try this:

```

DISPLAY=:0.0 /usr/bin/gedit 

```

---

### Post by BuskJan on 2015-08-13
Sorry! It did not do the trick. Gedit starts but doesn't show.

---

### Post by Lars Noodén on 2015-08-13
Who's cron are you running?  Your own user's or something else?

---

### Post by BuskJan on 2015-08-13
I am running my own user. I have tried running cron as root (sudo) but i did not work either.

---

### Post by tgalati4 on 2015-08-13
Please post the output of:

```
crontab -l
```

I presume you are using *crontab -e* to edit your crontab.

Perhaps:

```
 0 13 * * * DISPLAY=:0 gedit --display=:0
```

It works for me on Linux Mint MATE 17 (based on 14.04), using *pluma* instead of *gedit*.

---

### Post by BuskJan on 2015-08-13
Unfortunately */1 * * * * DISPLAY=:0 gedit --display=:0 did not display gedit.

Output of crontab -l
The line commented out is the script i want to run in a terminal window.
```
*/1 * * * * DISPLAY=:0 gedit --display=:0
#*/1 * * * * DISPLAY=:0 /usr/bin/gnome-terminal -x /home/jan/virusscans/daily_run.sh

```

---

### Post by SeijiSensei on 2015-08-13
Why do you need a terminal window?  Pipe the output of daily_run.sh to a log file.  Also the time codes are wrong if you want to run this once a day.
```

# m h dom mon dow command
0 0 * * * /home/jan/virusscans/daily_run.sh >> /home/jan/virusscans/daily_run.log 2>&1

```
(The "2>&1" redirects output sent to the error device, stderr, to the primary output device, stdout, so it will be included in the log.)

That crontab entry runs the script every night at midnight (m=0; h=0).  If you want to run it at 8 am then replace the second zero with eight.

Writing the results of automated scripts to log files makes things much more convenient for you.  Now you can just go look at daily_run.log each morning.

The crontab entry I wrote assumes daily_run.sh begins with a "hashbang" like this:
```

#!/bin/bash

your code

```

---

### Post by tgalati4 on 2015-08-13
This is my crontab -l:

> # m h  dom mon dow   command
 50 22 * * * DISPLAY=:0 notify-send -u critical "Don't Forget" "Make your phone call."
 50 12 * * * DISPLAY=:0 pluma
*/10 * * * * pluma --display=:0


Every 10 minutes a pluma (MATE's fork of gedit) pops up in the current window.  Don't know why you are having troubles.  Perhaps try greater than 1 minute intervals.

---

### Post by BuskJan on 2015-08-14
I have tried starting gedit every minut, every 10 minuts and at 07:11. Sadly its no go at all occasions. 

The reason for wanting to start a terminal window via cron is not a part of this discussion and trust me, I know how to grep info out of a log file ;)

---

### Post by tgalati4 on 2015-08-14
What version of Ubuntu are your running?

```
cat /etc/issue
uname -a
lsb_release -a
```

If you have a malformed crontab, it will get rejected.  Perhaps you have other entries that are pathological.

---

### Post by BuskJan on 2015-08-15
Here are the outputs! I am running ubuntu 15.04 with gnome desktop.



```
cat /etc/issue

Ubuntu 15.04 \n \l

```
```
cat /etc/issue

Ubuntu 15.04 \n \l

```
```
lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

```


My crontab looks like this:
```
# For more information see the manual pages of crontab(5) and cron(8)# 
# m h  dom mon dow   command


11 7 * * * DISPLAY=:0 gedit --display=:0
#*/1 * * * * DISPLAY=:0 /usr/bin/gnome-terminal -x /home/jan/virusscans/daily_run.sh



```
I verified that cron is doing its thin by running touch foo.txt every minute. So cron works.

---

### Post by tgalati4 on 2015-08-15
Maybe there was a security policy change from 14.04 to 15.04.  Perhaps User crontabs are more restricted in 15.04.  

Try running *gedit* in a terminal with extra settings:

> tgalati4@Mint17 ~ $ pluma --help-gtk
Usage:
  pluma [OPTION...] [FILE...] - Edit text files

GTK+ Options
  --class=CLASS                   Program class as used by the window manager
  --name=NAME                     Program name as used by the window manager
  **--display=DISPLAY               X display to use**
  **--screen=SCREEN                 X screen to use**
  --sync                          Make X calls synchronous
  --gtk-module=MODULES            Load additional GTK+ modules
  **--g-fatal-warnings**              Make all warnings fatal


If you are running multiple monitors, then you would need to define the screen to display your output to.

---

### Post by BuskJan on 2015-08-16
> **tgalati4 said:**
> Maybe there was a security policy change from 14.04 to 15.04.  Perhaps User crontabs are more restricted in 15.04. I

Try running *gedit* in a terminal with extra settings:

Well, running gedit i just for troubleshooting. The real object is to run a shell script i a terminal window so the user can see the output. So running gedit with extra settings don't seem to bring me any closer to a solution.

Maybe it's not possible to start a gui program from crontabs? Since starting a gui program automatically is something I need to do. I have started programming a gui-scheduler in free pascal. (Yes, I'm an old fart and what little coding i done in my life i have mostly done in delphi!) :D 

Btw, Thank you [COLOR=#000000]tgalati4 for taking your time to help me out![/COLOR]

---

