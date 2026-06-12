---
title: "Anyone successfully running the Nvidia 331.20 graphics driver on 12.04.4?"
date: 2014-02-11
forum: General Help
---

### Post by Butthead on 2014-02-11
Hi,

Like the title says, I'm just wondering if anyone on the forum here with a Nvidia based graphics card has the 331.20 Nvidia grapics driver (the current "recommended" on found in Additional Drivers) running well on thir rig, or if it's buggy (like some Google searches I've done) have indicated?  

I'd like to install it, but don't look forward to possibly having to reinstall 12.04 again when renders the system inoperable. :mad:

---

### Post by SonWon on 2014-02-11
I've been using without problems.  Also playing games using PlayonLinux.

---

### Post by Butthead on 2014-02-12
Okay, thanks for the reply! :guitar:

Did you use "Additional Drivers" (or the command line) to install it (if you don't mind me asking)? :-k

---

### Post by SonWon on 2014-02-12
"Additional Drivers" however you may need to uninstall the old driver first and reboot.  Or you may see the Black Screen of Death when booting.  Like Windows Blue Screen of Death only worst since there is no message telling you why it failed.  I had this and did a reinstall to clear.  I took a leap of faith and let the auto updater load the newest Nvidia drivers without uninstalling the older driver first and it just worked.  I don't know why it failed when I originally loaded Ubuntu.

---

### Post by Butthead on 2014-02-13
Thanks for all your help!  Got the Nvidia 331.20 driver to install (I guess "Additional Drivers" actually DOES work sometimes without buggering up the system :P ).

Had to turn around and uninstall it though (back to 304.116 :mad: ).  Seems my current graphics card (a cheap GeForce 8200 in a Zareason rig) doesn't get along with the 331 (had all kinds of tearing and lock-up's when it was installed).  So glad the "Additional Drivers" worked both times without having to do a reinstall again. :shock::-x:biggrin:

I wonder why a driver shows up as "recommended" when it won't work though? :confused:

---

### Post by SonWon on 2014-02-14
Computer stuff is difficult since every board is a little different between manufacturers unless they are reference design and even then they likely differ.  So what works with most cards may not work for all.  There may have been a setting in the Nvidia Xserver Settings that would fix the tearing.  Nvidia Xserver Settings is a program install with the driver.

---

### Post by Butthead on 2014-02-14
> **SonWon said:**
> Computer stuff is difficult since every board is a little different between manufacturers unless they are reference design and even then they likely differ.  So what works with most cards may not work for all.  There may have been a setting in the Nvidia Xserver Settings that would fix the tearing.  Nvidia Xserver Settings is a program install with the driver.

Only problem is is that you got to find that setting that (might?) work in Nvidia Xserver Settings before it locks up (or the screen starts tearing) on you. :x

Kind of akin to defusing a bomb before it goes off on you. :eek: :tongue:

---

