---
title: "Dual Boot Problems"
date: 2013-07-03
forum: General Help
---

### Post by olnik on 2013-07-03
I have two Hard Disks, a 1TB and a 500GB in my custom build. I split the 500GB in to two 250GB partitions, then installed Ubuntu on to one of them first. I then installed Windows 7 on the other partition. Now when I boot up it doesn't boot in to GRUB it boots straight in to Windows without any options. How can I make it boot back in to GRUB?

Thanks, James.

---

### Post by SirDelder on 2013-07-03
Windows can cause some problems when installed after another OS. Try Reinstalling Ubuntu on the partition you want it on. That may solve your problem. I don't know how to fix it if that doesn't work.

---

### Post by olnik on 2013-07-03
It would be ideal if there was another way to maybe purely reinstall GRUB instead of Ubuntu as I have a very slow connection and installed a lot of updates. Also, I have files on there which I wish to keep, I could run the live disc and transfer the files but I'd rather not.

But thanks for the help!

---

### Post by leclerc65 on 2013-07-03
Yes, you can reinstall Grub from your Ubuntu CD.
If nobody helps you now, wait for me a few hours until I get home.

---

### Post by varunendra on 2013-07-03
> **SirDelder said:**
> Windows can cause some problems when installed after another OS..

In fact, Windows will definitely cause this problem when installed AFTER Linux. It just overwrites the MBR (Master Boot Record) with its own, and obviously doesn't/can't detect Linux to include it in its boot menu.

Fortunately, the fix is easy enough. If you don't want to go into hassle of commands, just use Boot-Repair to reinstall Grub on the MBR : [http://help.ubuntu.com/community/Boot-Repair](http://help.ubuntu.com/community/Boot-Repair)

It will return you the Grub menu which will give you the option to boot either Ubuntu or Windows.

---

### Post by SirDelder on 2013-07-03
OK, I didn't think about that. Here's a link to the steps:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[edit] Sorry, I didn't see someone had already posted the answer while I googled it.

---

### Post by coffeecat on 2013-07-03
Support question.

*Thread moved to **General Help**.*

---

### Post by stalkingwolf on 2013-07-04
yep , i keep a copy of the boot repair disk handy anytime i do an install.  usually to fix the resolution out of range issue.

---

