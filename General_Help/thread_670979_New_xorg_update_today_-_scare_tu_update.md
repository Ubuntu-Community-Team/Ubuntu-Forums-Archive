---
title: "New xorg update today - scare tu update"
date: 2008-01-18
forum: General Help
---

### Post by Prisma on 2008-01-18
I have a new update for the xorg server waiting for me in the update manager, but I had a really bad experience last time I did it in 2006, like a lot of people did i wasn't able to load X at all, it is safe to update now?  :confused:

---

### Post by tgilber1 on 2008-01-18
1.  What kind of video card do you have?
2.  Which driver are you using, proprietary or Ubuntu's?
3.  Provide a copy of your /etc/X11/xorg.conf file

---

### Post by dcstar on 2008-01-18
> **Prisma said:**
> I have a new update for the xorg server waiting for me in the update manager, but I had a really bad experience last time I did it in 2006, like a lot of people did i wasn't able to load X at all, it is safe to update now?  :confused:

Works fine on my system.

---

### Post by Prisma on 2008-01-18
I have an Nvidia 7600GT and the restricted drivers that came with Ubuntu.

---

### Post by PmDematagoda on 2008-01-18
You should not face much problems with updating the X-Server. In any case, even if you do face a problem with the Nvidia driver it would not be that difficult to reinstall them and get the GUI working perfectly again. We can help you with any problems you face:).

---

### Post by Prisma on 2008-01-18
> **PmDematagoda said:**
> You should not face much problems with updating the X-Server. In any case, even if you do face a problem with the Nvidia driver it would not be that difficult to reinstall them and get the GUI working perfectly again. We can help you with any problems you face:).

thanks :guitar:

---

### Post by Buddha443556 on 2008-01-18
There's another thread and a bug report that says the current update is killing Java Apps.

[http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

I'd hold off.

---

### Post by simonjcruse on 2008-01-18
do not update, i have 2 machines not working because of todays update, its a real mess... no info on how to fix this? i've tried to downgrade my xorg and reinstall nvidia driver.. nothing still doesn't work... Awaiting UPDATE to fix this... SO for the moment i have no graphics on any of my machines, not good really as im showing the linux installation to clients on monday so i can migrate there entire network to ubuntu... This is not looking good at the moment.......

Unless there are alot of dual booters out there thee only hope at the moment is lynx to try and find solution coz after 6 hours so far im not managed to come across the solution.

updated to version 8.1 (xorg)

Both machines run Nvidia 169.07
8400gs
8600gt 512

Any help please?

---

### Post by rich86 on 2008-01-18
DO NOT UPDATE, it has broken vlc and many java programs amongst others, fortunately i managed to downgrade to a previous version and all is ok.

I read somewhere it was meant to have been pulled by now and that the developers are aware.

---

### Post by jwcgator on 2008-01-18
Ok so, nothing on my system has broken due to the new Xorg update.  However, i did install Azureus and indeed got the error that everyone else has been recieving.

Frostwire still works (isn't that a java app too?)

---

### Post by Mindstab on 2008-01-18
Ah, this explains it.  I came to the forum looking for why when trying to install the new XOrg update in the update manager failed with a 403 Forbidden Error.  I guess they figured that was the fastest way to stop the update in an emergency situation like this.  Good to know they're at least trying to minimize this.  A little sad that this Xorg fiasco is happening again tho :/

---

### Post by Tosa on 2008-01-18
I've updated it half an hour ago... No errors during update. Off course, I've read this thread **after** I updated.
I guess I wont reboot till next update... :confused:

---

### Post by zipperback on 2008-01-18
Nothing broke on my system.

- zipperback
:popcorn:

---

### Post by drs305 on 2008-01-18
I just tried updating 2 files via the update manager. The xserver-xorg-core won't download although the other xorg file did and installed ok.

Gutsy 64-bit.

---

### Post by dcstar on 2008-01-18
The "broken" update has now been updated itself, so there is a new "new" xorg update available to install (neither have caused any issues on my system).

---

### Post by ubuntu-freak on 2008-01-18
We really ARE running Debian Sid! Ahh brings back memories.
 
I had less issues in Sid actually, but I enjoy the fact that Ubuntu is a deskop distro. Not a huge fan of Gutsy though. Should be called Bugsy.
 
Bring on Hardy I say. It's gonna be good.
 
Nathan

---

