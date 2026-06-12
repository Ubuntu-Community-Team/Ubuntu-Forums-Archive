---
title: "[SOLVED] kill firefox"
date: 2008-04-24
forum: General Help
---

### Post by dpwilson on 2008-04-24
I am having the same problem with firefox that many have and I guess its related to flash.  The problem is that it freezes up and in turn, screws up other things as well, for example, I cannot run system monitor after it freezes.  I have to force close to get rid of firefox.  When I try to start it again, I get a message that *"firefox is already running but not responding.  To open a new window, you must first close the existing firefox process or restart your system"*

Typically I have to restart my system because I cannot figure out how to close the process.  I have tried killall, sudo kill, pkill, and have tried to find the process, but for the life of me, cant figure out what it is and exactly how to stop it.

Anybody got an idea of something for me to try?

---

### Post by hessiess on 2008-04-24
normaly i can just shutdown the prosess with system monitor

---

### Post by dpwilson on 2008-04-24
> **hessiess said:**
> normaly i can just shutdown the prosess with system monitor

problem is, after firefox freezes, system monitor doesnt work.  It looks like it is starting, but never does come up.  I would like to think there is something other than shutting down everytime.

This has been the hardest thing to try and sell my wife over from Windows.  If I could just get the freeze ups taken care of.

---

### Post by hessiess on 2008-04-24
have you tryed restarting X? (ctrl->alt->backspace)

---

### Post by retrow on 2008-04-24
Find process number for firefox in terminal:
```
ps x | grep firefox
```
You'll find the process ID for firefox, its the number at the beginning.
Then,
```
kill xxxxxx
```That way you can restart firefox without having to restart the system or restarting X.

---

### Post by dpwilson on 2008-04-24
restarting X never worked.  I still had the same message when I logged back on.  I pasted that into terminal.```
wilson@75-106-163-58:~$ ps x | grep firefox
 5944 ?        S      0:00 /bin/sh /usr/bin/firefox
 5956 ?        S      0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
 5960 ?        Rl     0:05 /usr/lib/firefox/firefox-bin
 5976 pts/1    R+     0:00 grep firefox

```  Is it the very first line (5944) that I would kill?

Right now its working after a reboot, but will try that next time it freezes.

---

### Post by retrow on 2008-04-24
No, you have to kill the one that holds the actual program. In your case, firefox is in the /usr/lib/firefox/ directory. You want to kill process number 5960, or whichever one thats running **/usr/lib/firefox/firefox-bin** it happens to be when it freezes.

Just to get some practice, you can kill firefox just for fun. Don't worry about the data and cookies, because the next time you fire it up, it will ask you whether you want to restore your earlier session.

---

### Post by dpwilson on 2008-04-24
cool that worked.  Thanks for the info.  I will have to try it when it freezes and let ya know how it worked.  Thanks again.

---

