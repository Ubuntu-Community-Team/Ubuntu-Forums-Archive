---
title: "renice not working (?)"
date: 2008-01-30
forum: General Help
---

### Post by yankcrime on 2008-01-30
Has anyone had an issue using renice?  I am trying to increase the priority of mythfrontend from the command line, and there seems to be problem setting the nice level.

If mythfrontend begins as 0 (typical), I have the following two commands (same command twice):

mythuser@mythbox:~$ sudo renice -5 mythfrontend
0: old priority 0, new priority -5
mythuser@mythbox:~$ sudo renice -5 mythfrontend
0: old priority 0, new priority -5

The first one has no surprise.  It begins at the old priority of 0, and it claims it sets at the new priority of -5.  If I run the same command again, it again says the old priority is 0, and new is -5.  I have confirmed that this command does not actually change the nice level through top and through the gnome system monitor.

If I use nice, things work nicely (pun intended) in that I can set the nice level.  However, this won't work for me because I don't want mythtv to start with root priveledges (and the X session won't open properly sudo-ing mythfrontend).

Any thoughts?  Much thanks.

---

### Post by danwood76 on 2008-01-30
I found a very good script for setting nice levels a while ago called 'verynice'.
It has a config file and you just set the names of process you want the nice level increased or decreased on.

You do need to compile it from source but it has no dependencies.

heres the link [http://thermal.cnde.iastate.edu/~sdh4/verynice/](http://thermal.cnde.iastate.edu/~sdh4/verynice/)

I used it in a jukebox I made to keep the mp3s from breaking up during play.

reagrds,
Danny

---

### Post by heindsight on 2008-01-30
renice expects a PID as argument, not a process name. If you look at the output you got from renice: ```
0: old priority 0, new priority -5
``` the 0: on the left, indicates that the niceness of the process with PID 0 has been changed. Process ID's usually start at 1, I'm not sure how a PID of 0 is interpreted (it might be causing renice to renice itself though).

You can obtain the PID of a process using pgrep, so perhaps you could do something like:
```
sudo renice -5 $(pgrep mythfrontend)
``` to renice mythfrontend.

---

### Post by yankcrime on 2008-01-30
While I haven't yet looked into verynice (just downloaded so far), it seems like an interesting program.  Perhaps it is best intended for a system which is using multimedia as well as other applications (email, browser, etc.).  Because this system is a dedicated mythtv frontend, I am chosing to use the simpler solution (renice through the process id).  It works like a charm.  I don't really know why renice based on name doesn't work, but this one definately does.  That tid-bit about the process ID as the first number makes significant sence as well!  Thanks for both suggestions!

---

