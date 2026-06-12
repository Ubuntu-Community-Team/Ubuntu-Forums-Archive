---
title: "Multiple users in 8.04 seems horribly broken!"
date: 2008-05-22
forum: General Help
---

### Post by wkulecz on 2008-05-22
Can't say I've really tested this on 6.06 or 7.04 (skiped 7.10 altogether) but with the "fast user switcher" bringing this to the top level in 8.04 it seemed logical to add another private login for my development environment and use the default automatic login for our normal operators that run my applications.  Under 6.06 I did all work as the default login and simply trusted the operators to follow instructions and not generally muck things up which has worked out pretty well, but its that one exception that had me looking to change.

Basically I'm finding multiple users unusable for the following reasons.

My default log in created with the User and Groups tool is full of weird problems that don't exist when only the default login is used.

1) No sound for the added uses. If I leave the default user logged in and then switch to my private login I ten get sound.  This would be a work around but...

2) System randomly locks up (no mouse movement, keyboard dead, no numlock capslock LED status changes) when the two logins are active.  Hard reset is all I can to to recover.  With only the default user loged in system is rock solid even running the random screen savers over the weekend.

3) Screen resolutions are fubar, I can recover by recreating xorg.conf with the nvidia-settings tool but this seems to keep happening at random intervals.


I am currently testing to see if logging out the default user and using only my private login without sound will be stable.

--wally.

---

### Post by wkulecz on 2008-05-23
So far it looks like being logged in as my private user after logging out of the default user the system seem stable, now I'll switch to the default user leaving my private login active as well and see if things wedge again, in case one of the 100+ updates these past few days accidentally fixed it.

With this many updatates, this quickly since release, me thinks it probabably shouldn't have been released when it was.

--wally.

---

### Post by wkulecz on 2008-05-28
Looks like one of the many updates has silently fixed the issue.  System remained active after my four day holiday with both users active.

The update did not fix the issue of no sound if only my added user is logged in.  Switching to make the default user active and then back to my added userID leaving the default user active results in sounds working.  If it doesn't lockup, its a viable workaround.


I updated my wife's home computer over the weekend.  Fresh install to second hard drive actually, then copied over what she needed from her old home folder.  Only glitch was the USB Wireless-G network interface didn't show up in System_>Administration->Network.  After a bit of cussing about regression, I stumbled upon  the taskbar network icon in the upper right cornor and the drop down showed it was automagically working and asking which of mine and my neighbors networks to use and set the passphrase.

Random screen saver locks on this system same as it did on 7.04 (and my 6.06 systems) but other than that it has been solid -- the builtin support for the Samsung CLP-300 color laser has much better print quality that the Samsung drivers did under 7.04.  The wireless network performance seem better too, but some or all of this could be improvements in Gnome.

--wally.

---

### Post by zvacet on 2008-05-28
During installation you make default account with administrator privileges.As far I can remember itwas recommended to make other one after install.Difference between them is that second account doesn´t have admin privileges.Second account is for everyday work and you update,install new packages,remove them... with first (administrator)account.It is made that way for security reason (not just secure you from outside world it secure system from yourself,because we are one who make mistakes).In short my advice will be to use non admin user account for your everyday work.

---

### Post by wkulecz on 2008-05-28
I believe what you are saying is not correct.  The default user (set-up by the installer) is allowed to use sudo for administrative tasks, but there is no root login setup by the installer -- try it!

I gave my added user the same settings privilidges with the user and groups tool as the one setup by the installer.  I plan to remove the sudo ablity from the default user when things are working correctly and don't plan to enable a root or administrative login.

If there are setting is some "policy editor" that are not exposed in the users and groups tool, it could account for the sound bug, but if there are, the question is to findout what they might be.

The show stopper of hard lockups under system idle activity with two uses active via the "switch user tool" seems to have been silently resolved by one of the 100+ updates from the initial post to my tests to isolate the circumstances further.

--wally.

---

### Post by zvacet on 2008-05-28
>  The default user (set-up by the installer) is allowed to use sudo for administrative tasks, but there is no root login setup by the installer -- try it!

Can you point to the line in my post where I talking about root?I don´t want to command you what to do with your comp.I was just giving you advice.You will decide will you accept it or not.

---

### Post by louieb on 2008-05-28
> **wkulecz said:**
> ...With this many updatates, this quickly since release, me thinks it probabably shouldn't have been released when it was...

Been using Ubuntu since 5.10. 6.10 was the only one I skipped. Haven't really noticed  an increase in updates over previous releases.   But if I remember right Dapper had the most.  It was two months late being released   and had so many updates that it wasn't long before 6.06.1 came out.  Seems like Ubuntu is getting better at putting out a polished release. 

Also don't think Ubuntu has much control over the timing of upstream security updates such as the recent one  fixing ssh key generation.  


I normally log on with two users and I agree that this is an area that needs work.  Feisty seemed to have the most problems.  Screen resolution or the screen just going blank altogether have been my main problem but its one that seems to come and go .    

Linux development is moving fast. I guess I could freeze my system at some point where every thing works. (or just switch to Slackware or CentOS).  :)Oh well

---

### Post by wkulecz on 2008-05-29
At least the updates appear to have solved my lockup issue with two users logged in, so I can leave the default user logged in and active to workaround my sound not working when only my added user is logged in.

Basically I've had smooth transition from 6.06 and 7.04 to 8.04, its just I don't think pulse audio is ready to be in a LTS release, I had no sound issues with the older versions.

8.04 wireless networking and printing support seems much improved so on balance its a worthwhile improvement since sound is not critical for what I do.  But without the pulse audio sound issues the release would be fantastic.

--wally.

---

