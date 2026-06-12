---
title: "[SOLVED] No Sound Notifications from k3b"
date: 2008-05-19
forum: General Help
---

### Post by Gotit on 2008-05-19
It´s a small problem, but annoying... (at least for me)
I did a fresh install of Hardy (after fighting to make the upgrade work for 2 weeks) and installed my favorite apps.  Everything seems to work except the sound notifications from k3b.  These are the:
Success burn (bugle)
Error (wah wah wah)
Insert media (thunk)

I can set the notifications to write to a log file and that works just fine.  Only the sound notifications don´t work.  Other apps with audio wave files work fine, but not k3b. Yes, they are selected in k3b settings > configure > notifications. 

I have checked and the k3b wave files are in the right location usr/share/sounds but they just don´t get played.

I have k3b on another Hardy VM and the sound notifications work fine.  Both Hardy installs have k3b version 1.0.4.

[COLOR="Red"]Update:
Running terminal I get the following error when I try to test the sound by clicking the "Play a Sound" button in configure[/COLOR]
> k3b: 
QGDict::hashKeyString: Invalid null key
k3b: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol ''.


Anyone have any ideas???
Thanks!

---

### Post by Gotit on 2008-06-14
A reinstall of HH with a known good install CD fixed the problem.

---

