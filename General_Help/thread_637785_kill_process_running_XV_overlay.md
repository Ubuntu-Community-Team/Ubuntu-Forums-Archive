---
title: "kill process running XV overlay?"
date: 2007-12-11
forum: General Help
---

### Post by segalion on 2007-12-11
I´m searching a command to discover the process PID that is using the XV overlay.

Sometimes firefox or rythmbox are using the XV videorender (that it is known to be used only by one program at a time), and when I run my favorite videoplayer it isnt able to get the XV overlay. I would like a script (myplayer) to kill all process using XV before running the player. 

I have this script in order to:

>disable compiz - for better videoplaying support (OSD, changing overlay monitor and resize while playing, etc.).
>kill process running XV ?( thats what I need to ensure XV for my player)
>run player "$*"
>and then enable compiz again at exiting...


Please help me, I cant find anything (xvattr?, xvinfo? or something similar).

---

### Post by DagMan on 2007-12-11
I don't know what an XV overlay is.  Is it a process running that you can find when you type ps -e, or specifically 
ps -e | grep whatevertheXVnameiswhenitruns

and if so, are you wanting to kill the XV process or just what is using the process, and if it is just what is using the process, is it always that only one thing uses it?

What user runs the XV thing, you or root?

---

### Post by segalion on 2007-12-12
XV is the name of an option to render video directly and fastest on video-cards by Xorg (usually named overlay).
Only one program can use it at a time, and I want to kill process using it.
In most players (totem, xine, mplayer, etc) you have options to use XV or other "motor renders", but usually this is the default.
At this post you can see how to disable XV on most favourit players to avoid conflict with compiz...

[http://ubuntuforums.org/showthread.php?t=507332&highlight=compiz+xine+totem+mplayer](http://ubuntuforums.org/showthread.php?t=507332&highlight=compiz+xine+totem+mplayer)

---

### Post by DagMan on 2007-12-12
ouch.  good luck.  It might be worth putting this down in the programming forum as well.  I think I've wasted your time with the thread no longer showing up in unanswered posts.

---

