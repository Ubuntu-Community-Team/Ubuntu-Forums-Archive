---
title: "Changes to grub.cfg not taking effect (Kubuntu 14.04)"
date: 2014-09-21
forum: General Help
---

### Post by weyland42 on 2014-09-21
After installing Kubuntu 14.04 (on AMD64) the grub boot menu contains that (on 5th line) and the previous version (on 1st line), which is fine except that I want 14.04 to boot by default, not the older version.

So I edited /etc/default/grub with GRUB_DEFAULT=4 and ran update-grub. No apparent problems, and grub.cfg looks OK.

But the boot menu still defaults to the 1st line, which is the previous installation.

Any ideas how to fix this?

---

### Post by ajgreeny on 2014-09-21
I assume from your post that you have two separate OSs installed with Kubuntu 14.04 as the most recent.

When you edited the grub file and ran sudo update-grub which OS were you using, and which OS is actually managing grub?

If you go to boot-repair in my signature and run the boot-info script that it gives you, not the repair option, you will get a web-link for the output of the script which you can copy here and may help us diagnose the problem, which I suspect is because the wrong OS is managing grub, ie the old version, not the new.

To avoid all this you may prefer to try booting to the new Kubuntu 14.04 and running command ```
sudo grub-install /dev/sda
``` assuming sda is your only disk or is the first priority device in the boot order if you have more than one.

---

### Post by weyland42 on 2014-09-21
Doh! Senior moment. Thanks, ajgreeny. (I updated grub.cfg in the other Kubuntu, and it all works fine now.)

You're clearly no novice, so I'd be interested to know why you prefer Xubuntu, if you don't mind telling us.

---

### Post by ajgreeny on 2014-09-21
I used to use Ubuntu with gnome 2 desktop, but also had the kubuntu-desktop package installed on that to try, which I quite liked.  However when kde 4 appeared it lost me totally and I did not like it at all, so used gnome 2.

Then when gnome 2 disappeared and unity came along I was again lost and tried the fallback classic-desktop which could be added to unity.  That was bearable, until I tried adding xubuntu-desktop to the system.

I was hooked, totally, by the attractive, very configurable and also very fast, classic-style desktop that it gave me, even on what was then an old desktop machine with single-core sempron 2400+ cpu and a graphic card that would and could only use the open-source radeon driver.  Sice then I have stuck with Xubuntu and still love it.  I have yet to upgrade this fast new desktop machine to 14.04 but I have it in a VirtualBox installation and will very soon upgrade the main OS as it looks as if the bugs of Xubuntu 14.04 have now been sorted out completely.

---

