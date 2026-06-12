---
title: "Edgy boot problem"
date: 2007-03-11
forum: General Help
---

### Post by westli on 2007-03-11
My Edgy installation has gotten flakey in the boot department, and is steadily getting worse.

System:  AMD64 3000+,  there's a 40GB drive, mainly for XP-specific files, and two 160GB drives.  Edgy dual boot with XP.   I think Grub is in the first HD MBR (how do you tell?).

It seems to boot normally until I have logged in.  Then, instead of getting the rectangular window showing the initialization of various parts of the system, I get a blank default-orange screen.  If I wait long enough, a white rectangle appears in the upper left of the screen, about 1/8 screen in size, and that's as far as it goes.  Yesterday, a reboot was all I needed.  Today, many reboots are needed.  I tried the Ubuntu CD (I used the alternate version) to rescue.  I was unable to reinstall Grub to the MBR of HD0 (/dev/hda1).  Ubu is installed on /dev/hdd1.

---

### Post by zvacet on 2007-03-12
It seems that you tryed to reinstalled grub in the wrong partition.Boot up your Ubuntu CD and from initial screen choose &#733;Recover a broken system&#733;.After a while you will be asked to choose root device.Because you are dual-booting your device is probably second(first is windows).If you continue to next dialog you choosed right,and if not you are wrong.All you have to do is to choose right one this time.In the next dialog you will see number of options,and you pick &#733;Reinstall GRUB boot loader&#733;.You will be asked where you like to install GRUB and you will type hd0.When is finished choose reboot,and if it´s all O.K. you will have your GRUB in right place again.

---

### Post by westli on 2007-03-17
Thanks for the response, Zvacet.  Sorry it took so long to get back.  I've been in the hospital.

I no longer think this is a GRUB issue, though.  Like I said, I get logged in and then things go blank.  And it's intermittant.  It doesn't happen all the time, although it's getting more frequent.

I boot without beryl, by the way, and turn that on later if I feel like it.

dj

---

### Post by zvacet on 2007-03-18
```
sudo dpkg-reconfigure xserver-xorg
```

---

