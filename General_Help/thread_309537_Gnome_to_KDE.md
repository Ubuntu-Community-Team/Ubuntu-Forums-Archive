---
title: "Gnome to KDE ?"
date: 2006-11-29
forum: General Help
---

### Post by rfruth on 2006-11-29
if user0 (me) uses Gnome can user1 have KDE without affecting user0 (same physical hard disk) if so how :rolleyes:

---

### Post by taurus on 2006-11-29
Make sure you have both Gnome and KDE on your system.  Then user1 can log in and chooses Gnome as his/her window manager.  But when user2 logs in, he/she can pick KDE.  Both users will have their own $HOME directory so it won't effect either other.  In fact, user2 can choose Gnome next time when he/she logs in.  It's perfectly fine too...

---

### Post by FryerFox on 2006-11-29
You need to install the KDE package:
> sudo apt-get install kde

Since the login manager is still set to gdm (the Gnome one), I think that you won't be able to shutdown or reboot the machine from KDE without logging out.

Other than that, I don't believe there should be any issues.

---

### Post by Mr Fat Bat on 2006-11-29
If you want the entire ubuntu KDE package then use:

> sudo apt-get install kubuntu-desktop

I did it about an hour ago and works a treat!  No need for a restart.

---

### Post by Elimist on 2006-11-29
sudo apt-get install kubuntu-desktop

Then you or another user can use KDE or Gnome.
If you log in and save something, no matter what desktop environment you're in, it'll save into your home folder. If another user logs in at all, it will save into THEIR home folder, not messing with your stuff at all.

---

### Post by FryerFox on 2006-11-29
> **Mr Fat Bat said:**
> If you want the entire ubuntu KDE package then use:
sudo apt-get install kubuntu-desktop
I did it about an hour ago and works a treat!  No need for a restart.

I defer to Fat Bat. 'kubuntu-desktop' sounds like a more comprehensive solution than 'kde'.

---

### Post by strabes on 2006-11-29
yeah kubuntu-desktop installs more stuff that mark shuttleworth thinks you need. Probably a good idea I guess.

---

### Post by aysiu on 2006-11-30
> **FryerFox said:**
> I defer to Fat Bat. 'kubuntu-desktop' sounds like a more comprehensive solution than 'kde'.
Actually, it's quite the opposite--*kubuntu-desktop* installs only Ubuntu's prescribed set of KDE applications, whereas *kde* installs all KDE applications. *kde* is bigger.

To slim down more from *kubuntu-desktop*, you can use *kde-core*, or for barebones you can use *kdebase*.

More info here:

**Installing KDE**
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

**Installing a faster KDE**
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by rfruth on 2006-12-01
I installed kde-base, works like a top :KS

---

