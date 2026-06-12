---
title: "Crontab -e not running my recording script."
date: 2008-04-11
forum: General Help
---

### Post by glore2002 on 2008-04-11
Hello! :)

My system: Ubuntu 7.10. 

I have a script to record TV. Its name is tape. It records tv. It is located in the folder:
/home/myuser/bin/.

The script input format is: tape channel# NameOfFile 00:00:00. It works OK if I execute it from the console (as user).

But (here is where the problem appears) when I want to schedule the recording through crontab -e, it doesn't work. I am sure I am doing something wrong but I don't know what.

If I edit my crontab -e, it look like:

#########################################

# Recording TV.

00 21 * * 1-5 /home/myuser/bin/tape 10 tvprogram 01:00:00

##########################################

I've also tried with /bin/tape. I am trying to record a program starting at 9 pm from Monday to Friday.

Well, I don't know why it doesn't work. Maybe I have to start this daemon somewhere else or so. I will really appreciate any kind of help. 

Thanks in advance,

Glore2002.-

---

### Post by ibuclaw on 2008-04-11
if you copy the script to it's own directory
ie:
```
 /home/myuser/bin/**directory**/tape 
```

You can use the command **run-parts** in your script. 
The simplest way to describe the app, is that it runs all executable scripts in a directory.

So change your crontab line to:
```
 00 21 * * 1-5 run-parts /home/myuser/bin/**directory** 10 tvprogram 01:00:00 
```

[EDIT]
Sorry, that won't work. As run-parts doesn't take input arguments (***10 tvprogram 01:00:00***).
Unless you can embed the arguments into the script as variables. I'll look for another way.

Give that a try
Regards
Iain

---

### Post by dcstar on 2008-04-12
> **glore2002 said:**
> Hello! :)

My system: Ubuntu 7.10. 

I have a script to record TV. Its name is** tape**. It records tv. It is located in the folder:
/home/myuser/bin/.

The script input format is: tape channel# NameOfFile 00:00:00. It works OK if I execute it from the console (as user).
..........

If this is a graphical app then it **will not run** in cron without having the graphical environment set.

---

### Post by drs305 on 2008-04-12
> **dcstar said:**
> If this is a graphical app then it **will not run** in cron without having the graphical environment set.

Here is an example. I have a crontab entry which opens VLC at specific times (06:50, 11:50, 17:50) and sounds an alarm. Since the script opens up a GUI-based app (VLC), it creates problems in crontab if not given some special instructions. Here is my crontab entry:

```
50 6,11,17 * * * export DISPLAY=:0 && sh ~/.scripts/pcs.alarm.sh > /dev/null 
```

---

### Post by glore2002 on 2008-04-12
First of all, thanks for the help.

No, it is not a graphical application. The script uses mencoder to record tv. It works from console.

The problem (I guess) is related to cron. Maybe I am forgetting something when editing crontab -e or I have to start the daemon somewhere else or ...

If I run the script from console (ie; tape 10 tvnews 00:30:00) it works OK.  When I add it to cron (crontab -e) nothing happens. The script isn't executed.

glore2002

---

### Post by drs305 on 2008-04-12
> **glore2002 said:**
> If I run the script from console (ie; tape 10 tvnews 00:30:00) it works OK.  When I add it to cron (crontab -e) nothing happens. The script isn't executed.
[glore2002 

When you say you run the script from console, are you running a script  or are you just entering the line in?

If the former, I would make a bash script, make it executable, make sure the folder with the script is in your PATH, and test it to make sure it works (try typing the script name from the root directory to check the PATH and the script). Then have cron reference the bash script (see my example in previous post) instead of the actual command /switches.

Best of luck.

---

### Post by glore2002 on 2008-04-13
> **drs305 said:**
> When you say you run the script from console, are you running a script  or are you just entering the line in?

If the former, I would make a bash script, make it executable, make sure the folder with the script is in your PATH, and test it to make sure it works (try typing the script name from the root directory to check the PATH and the script). Then have cron reference the bash script (see my example in previous post) instead of the actual command /switches.

Best of luck.

Hello again,

#1. Thanks for your help. I appreciate that.
#2 I will include in this message my script and what I added to cron (crontab -e):

So, my script (tape) looks like this. 
###########################################################################
!/bin/bash
#
# script to encode tv using mencoder
#
# usage tape <channel#> <name> <duration>
#
CHAN="$1"
FNAME="$2"
DURATION="$3"

if [ $# -ne 3 ] 
then
echo "Usage tape <Channel> <Name> <duration>"
echo "duration = hh:mm:ss"
exit
fi

echo
echo "Taping " "$FNAME""_`date +%m%d`"
echo

mencoder tv:// -tv driver=v4l:device=/dev/video0:width=320:height=288:fps=25:norm=palnc:chanlist=us-cable:channel=$CHAN:saturation=-20:contrast=-20:audiorate=48000:immediatemode=0 -vf denoise3d -oac mp3lame -lameopts fastreset=medium -ovc lavc -lavcopts vcodec=mpeg4:vqscale=4:aspect=4/3 -endpos $DURATION -ffourcc DX50 -o "$FNAME"_`date +%m%d`.avi -quiet
###########################################################################

It is saved in /bin which is inside my folder (/home/user/bin). It can be run as executable (right click, permissions, etc). So, if I type (in terminal) tape 10 tvprogram 00:30:00 it works and record half an hour from channel 10.
I wrote this in crontab -e:

###########################################################################
# m h dom mon dow command
# Recording TV. 
00 08 * * 1-5 /bin/tape 10 tvrecord 01:00:00
###########################################################################

So, that's everything I have. What would you recommend to add/modify?

Thans again my friends!
Glore2002.-

---

### Post by glore2002 on 2008-05-23
Any other ideas?

In my previous post, you can see the script I use to record TV. I've saved it in /home/glorenzo/bin. I made it executable. If I type "tape 10 name 01:00:00" anywhere it will record 1 tv hour. So, it was added to $PATH. But when I add the job to cron via crontab -e, it just doesn't work! Nothing happens.

By console I really meant command line. Sorry for the mistake.

Should I add any command while editing cron to make the script run? 

Thanks again. I appreciate your efforts :-)

Glore2002.-

---

### Post by g00f on 2008-06-24
Hi,

I came across this thread because I have exactly the same problem ... and I have stumbled across the answer (for me at least).

To help with debugging the command you can capture the stdio output that mencoder would normally write to the console by appending '> filename.txt' to the line in crontab. For more info have a look at [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html").

In this case there were no clues by doing the above, so I decided to redirect stderr as well. I appended '1>file1.txt 2>file2.txt' to my crontab line. All of a sudden it all started working! I don't know the theory of why redirecting stdio/stderr makes a difference, but for me, it does.

What I have ended up doing is appending '1> /dev/null 2> /dev/null' to my line in crontab and all is now working as I wanted.

I hope this helps.

-g00f

---

### Post by glore2002 on 2008-07-13
Hi back!

First of all, thanks for your cooperation. I really appreciate that.

g00f, please let me know what exactly you added to cron line.Mi line is:

```

# Recording TV.

00 21 * * 1-5 tape 10 tvprogram 01:00:00

```

If I execute the script anywhere, it works OK (so it is in $PATH). I made the script executable.

If I do -exactly- the same thing and steps in Slackware, it works perfectly from within cron. The same happened when using Ubuntu 7.04. But in Ubuntu 7.10, 8.04 and Linux Mint nothing happens. I still don't know why. I can't find out the problem with cron! :confused:

Please, any new help will be appreciated.

Thank you!
Glore2002.-

---

### Post by g00f on 2008-07-15
> **glore2002 said:**
> g00f, please let me know what exactly you added to cron line.Mi line is:

```

# Recording TV.

00 21 * * 1-5 tape 10 tvprogram 01:00:00

```


Change your entry to

```

# Recording TV.

00 21 * * 1-5 tape 10 tvprogram 01:00:00 1> /dev/null 2> /dev/null

```

(Sorry for the delay, I really should read this forum more often.)

---

