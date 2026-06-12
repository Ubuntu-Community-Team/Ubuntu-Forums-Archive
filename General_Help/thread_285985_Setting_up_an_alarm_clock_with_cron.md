---
title: "Setting up an alarm clock with cron"
date: 2006-10-27
forum: General Help
---

### Post by cvp on 2006-10-27
Every simple online guide I've found online talks me pretty directly through setting up an event with **cron**.
Long story short, here's what I did:
**crontab -e**
added "30 11 * * * /home/cvp/alarm"
made /home/cvp/alarm, whose contents were "vlc /home/cvp/mp3/alarm.mp3" (this step is included because I plan on fancifying the alarm program once I get it to work)
**chmod +x /home/cvp/alarm**
tested out /home/cvp/alarm - it does exactly what I want it to do: starts up vlc and starts playing alarm.mp3
come 11:30, nothing happens.

**crontab -l** gives:
# m h  dom mon dow   command
30 11 * * * /home/cvp/alarm

The only things I'm fuzzy on are:
Some of the tutorials mention some process called **crond** which needs to be running. I don't have **crond** on my system.
**ps aux | grep cron**, on the other hand, says that a process called **cron** is running.
I have neither an **/etc/cron.allow** file nor **/etc/cron.deny** file. Do I need either?

Please help soon.
Thanks in advance!
-cvp

---

### Post by lloyd_b on 2006-10-27
> The only things I'm fuzzy on are:
Some of the tutorials mention some process called crond which needs to be running. I don't have crond on my system.
ps aux | grep cron, on the other hand, says that a process called cron is running.
I have neither an /etc/cron.allow file nor /etc/cron.deny file. Do I need either?

The "cron" process is the cron "daemon" - on other Unix variants it's sometimes named "crond".  That's not the problem.

The most common problem with cron scripts (and the one I think is the problem here) is that cron jobs need to specify the full path to the command to be run:

```
/usr/bin/vlc /home/cvp/mp3/alarm.mp3
```

rather than

```
vlc /home/cvp/mp3/alarm.mp3
```

(That's assuming that "vlc" is in /usr/bin, of course.  Type "which vlc" to find out for certain).

Lloyd B.

---

### Post by flyingbrass on 2006-10-27
That doesn't work either, at least not in Dapper.  Apps that use X don't work.  I set my crontab to have totem play a video clip.  Cron's mail said:

(totem:30659): Gtk-WARNING **: cannot open display: 

I ran into this before when I wanted a sound file to play at a certain time.  I ended up using aplay to make it work.

I think this has to do with cron not having access to a user's X session.  If so, there might be a simple way to allow it without opening X up to everyone (which would be a security risk).

---

### Post by lloyd_b on 2006-10-27
Ouch.  I didn't realize that "vlc" is an X application.

I agree - to make this idea work it'll require a non-Xwindows application like aplay.

Lloyd B.

---

### Post by flyingbrass on 2006-10-27
I tried the suggestions [here](http://www.linuxquestions.org/questions/showthread.php?threadid=135208).  "xhost + localhost" didn't help.  The su solution sounded good but didn't work.  The error mail said su must be run from a terminal.  Ugh.

"xhost +" is a bad idea, so I didn't even try it.  

There must be some way to allow cron to run X apps, preferably as the user.

---

### Post by flyingbrass on 2006-10-27
Ok, got it.  There may be other ways, but here's what I did.  Pull up a terminal and type:
> xhost +local:localhost
Keep in mind that you'll have to type this each time you log in unless you figure out where to set it permanently.  There may be a better way to accomplish the same thing.  I'm not sure how much of a security concern this is, but it's surely better than simply "xhost +".

Script for cron to run:
> #!/bin/bash
export DISPLAY=:0.0
/usr/bin/totem /home/username/videofile.avi

---

