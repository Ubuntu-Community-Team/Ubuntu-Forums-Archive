---
title: "How to change # times reboot triggers fsck"
date: 2007-08-31
forum: General Help
---

### Post by Rizlaw on 2007-08-31
After installing Ubuntu 7.04, there is a setting somewhere, I don't know where, which causes Linux to perform an automatic "fschk" after about 25 restarts. This is very annoying since I have three 750GB ext3 formatted drives which take quite some time to check.

I know that I can disable "fschk" by editing my "fstab" file for each drive to be "0 0" instead of "0 1" or "0 2", but that, in my judgment, would be dangerous. So my, question is: 

How can I increase the interval (number) before a recheck is triggered - say to 100?

Thanks.

---

### Post by lloyd_b on 2007-08-31
> **Rizlaw said:**
> After installing Ubuntu 7.04, there is a setting somewhere, I don't know where, which causes Linux to perform an automatic "fschk" after about 25 restarts. This is very annoying since I have three 750GB ext3 formatted drives which take quite some time to check.

I know that I can disable "fschk" by editing my "fstab" file for each drive to be "0 0" instead of "0 1" or "0 2", but that, in my judgment, would be dangerous. So my, question is: 

How can I increase the interval (number) before a recheck is triggered - say to 100?

Thanks.

It's actually pretty simple.  First off, you'll need to know the device for the particular partition ("/dev/hda2", "/dev/sda3", etc).  You should be able to see this in the "/etc/fstab" file.

Then, in a terminal window:
```
sudo tune2fs -c 100 /dev/hda2
```
assuming that the partition is "/dev/hda2", of course.

Type "man tune2fs" in a terminal window for more info about that (or pretty much any other) command.

One suggestion: set the different partitions with different values (like one at 97, one at 98, and one at 99).  That way it'll be a very rare occurrence for more than one of them to hit the check at the same time.

Lloyd B.

---

### Post by Rizlaw on 2007-08-31
Thanks for the info lloyd_b

---

### Post by Muhahahahaz on 2007-12-12
Also, setting it to 0 or -1 will disable checking.  This is useful for me because I have an Eee PC, where I am using my 8GB SDHC card for my home directory.  For whatever reason, fsck doesn't like SDHC cards, so I'm happy to disable it now!  Otherwise I would randomly be failing to boot every 20th time, which sucks.

Thanks for letting us know about this command! :)

---

