---
title: "KDE taskbar hosed"
date: 2008-02-15
forum: General Help
---

### Post by anjilslaire on 2008-02-15
Hey everybody,

My Kicker has mysteriously fouled itself up. It no longer displays the time, or KNetworkManager, or any tray applets like pidgin, kgpg, Klipboard, etc. And on th left, the KMenu icon is messed up, I have no shotrcut to places ( like home, storage devices, etc), 

Finally, There is no shutdown menu (log off/lock/etc) option when I open the Kmenu. 

Any thoughts?
Kubuntu Gutsy, all updates.

Thanks!

---

### Post by aysiu on 2008-02-15
Maybe rename your /home/*username*/.kde and /home/*username*/.config directories to ~/.kde.old and ~/.config.old and logging out and logging back in again?

---

### Post by anjilslaire on 2008-02-16
ah, that probably would have worked.
In the meantime, I backup up my home directory, deleted it, and reinstalled  the OS on "/" while leaving home untouched.
I keep a 20 gig root  + separate /home/ partition, so reinstalling the OS is trivial. ( I have a 100mbit fiber connection to the house for $40/month. In the US even!) A fairly quick apt-get and I'm up & running again.
 Then I just dropped my personal files back in place and resetup my gui preferences a bit. It was time for a fresh start, anyways :)

I'll keep that in mind for next time.

---

