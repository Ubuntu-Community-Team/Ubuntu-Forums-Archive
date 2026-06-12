---
title: "System freezing--HELP PLEASE!!!!!"
date: 2007-08-30
forum: General Help
---

### Post by laserluke on 2007-08-30
Hi--

My computer freezes at completely random times. I have to power down and restart the computer to get back on. I suspect it is related to firefox, because when it freezes i have firefox open, but sometimes it also happens when i leave the computer idle for about 10-15mins, even at the logon screen. I am running Ubuntu Fiesty v.7.04 with an 3.46ghz intel pentium 4 processor (single core) and an Ati mobility radeon 9000 IGP. 

I am a complete noob at ubuntu (just installed for the first time yesterday) and would appreciate detailed responses. So far I like ubuntu, however this problem is very frustrating ](*,)and beginning to change my  mind.

Thanks!!!

---

### Post by Bart_D on 2007-08-30
Well, do you have some desktop effects installed?

What else were you running besides Firefox?

Does Firefox have plugins or is it the stripped down basic version that came with your Ubuntu installation?

_Back up all your important files now._

---

### Post by laserluke on 2007-08-30
No, just firefox and sometimes the terminal. I do not have desktop effects enabled/installed, and I am working off a clean installation of fiesty.

---

### Post by merlinus on 2007-08-30
Did you install the specific drivers for your video card?

-merlin

---

### Post by laserluke on 2007-08-30
I try downloading and installing the driver from ATI's website and this is what I get in the terminal:

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.2.0

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install
root@lucas-laptop:~/Desktop# sh ati-driver-installer-8.28.8.run




:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by dagrump on 2007-08-30
Good luck kid, there's a 50+ page post about this. Dig down ,you'll find it.
My biggest issues with freezing were fixed w/  sudo apt-get remove powernowd
I had very few freezes after scaling of the cpu was disabled, I wouldn't do this on a laptop though. might eat your battery up quicker.

---

### Post by laserluke on 2007-08-30
> **dagrump said:**
> Good luck kid, there's a 50+ page post about this. Dig down ,you'll find it.
My biggest issues with freezing were fixed w/  sudo apt-get remove powernowd
I had very few freezes after scaling of the cpu was disabled, I wouldn't do this on a laptop though. might eat your battery up quicker.

Uhoh :sad:. Anybody know where I could find this post?

Thanks everyone for all your help...

---

### Post by dagrump on 2007-08-30
About page 9 or 10 in this topic (general help)

---

### Post by laserluke on 2007-08-30
thnx

---

