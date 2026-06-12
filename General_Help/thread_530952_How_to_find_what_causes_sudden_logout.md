---
title: "How to find what causes sudden logout?"
date: 2007-08-21
forum: General Help
---

### Post by Dr_Snapid on 2007-08-21
Hi,

I have recently found that my system keeps suddenly logging off and presenting me with the login screen for no apparent reason. Also, when I try to log back in, I get the login sound but no panels or desktop, just a blank screen with the human background and a mouse pointer. I have to kill X (ctrl+alt+bksp) then restart the machine.

Regarding the sudden logouts:

I have looked at the log viewer but cannot see anything which helps me find the cause.
I have recently installed a few things:
Compiz/XGL (about 2 weeks ago, this problem didnt start till a few days ago)
K3B (days ago)
K9Copy (days ago)
DVD::rip (days ago)

Since this issue started when I installed the DVD copying stuff. I believe maybe they are to blame, although they should not be running.... I had a DVD to copy for my karate club a few days ago, now that it's copied I havent used the programs since. I could remove them but since none of them should be running at startup I am not sure how they are to blame.

Is there something in the logs I can use? Nothing in the logs looks like a unexpected logout to me...

Regarding the unable to log back in:
I have seen this from time to time while playing with xorg.conf (I had to restart x a hundred times while setting up my dual monitor setup), if I restart xserver using the key combination, sometimes I cannot log back in. Like maybe the old session isnt really dead or something. I think if i log out before I restart x it is OK though.

Is there some way of killing the running x-session so I can log in without restarting?

---

### Post by Dr_Snapid on 2007-08-23
Bump.... can anybody help here?

---

### Post by bjarneh on 2007-08-23
the reason for the missing panels and so on is that these are still running (the old panels and window-manager and so on) and new ones can't be started before these are killed.


anything can be killed (referring to X as you mentioned), but i'm of little help with the auto-logout thing youv'e got going on there which seems to be the main problem..

hopefully someone clever comes along...

---

### Post by Dr_Snapid on 2007-08-27
> **bjarneh said:**
> the reason for the missing panels and so on is that these are still running (the old panels and window-manager and so on) and new ones can't be started before these are killed.

Thanks for that, I suspected the same. Any idea which processes will need to be killed?

How do I show a process list so I can see which ones to kill? When I run ps -aux the list is too long to see on the screen, is there a way to make it pause each screen so i can read the top ones?:confused:

---

### Post by RedSquirrel on 2007-08-27
> **Dr_Snapid said:**
> Thanks for that, I suspected the same. Any idea which processes will need to be killed?

How do I show a process list so I can see which ones to kill? When I run ps -aux the list is too long to see on the screen, is there a way to make it pause each screen so i can read the top ones?:confused:

```
ps -ef [COLOR=Blue]| more[/COLOR]
```will give you the output one screen at a time (the '| more' is the significant part). Press space to see the next output and 'q' to stop looking at the output. [EDIT: You can use '| less' if you prefer. Some people think less is more. :)  With less, you can use your PageUp and PageDown keys. Again, press 'q' to quit less.]

You should also be able to press **Shift-PageUp** to go back (I mean, without using *more* or *less*).

With regard to the log files, did you look in ~/.xsession-errors?

I haven't used GNOME in quite some time so I can't help much further. Sorry.

---

