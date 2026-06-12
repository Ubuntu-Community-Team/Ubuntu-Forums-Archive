---
title: "Strange error while botting up ubuntu"
date: 2008-04-28
forum: General Help
---

### Post by abc006 on 2008-04-28
I've got a Wubi dual-boot of Hardy Heron and Vista which I just installed yesterday. However, with varying frequency, while trying to boot up at the progress bar, it stops and goes to a black screen that simply says:
```
BusyBox v1.1.3 (Debian 1:1.13-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built in commands

(initramfs)
```And it just stays like this forever unless you type help which comes up with lots of random words, I assume commands, that only a programmer who wouldn't encounter this problem would know what to do with, and to get out of it all I have to force-power off. Vista works fine, however.

Anybody know what's going on? Thanks so much for your help.

---

### Post by TeoBigusGeekus on 2008-04-28
Type 

```
reboot
```

and enter recovery mode through the grub menu.

While in there type

```
sudo dkpg-reconfigure -phigh xserver-xorg
```

If it is a graphics problem, reconfiguring your xserver could solve it.

---

### Post by danwood76 on 2008-04-28
If it dumps you to a BusyBox it might be an initramfs problem.
rebuild the initramfs also within the recovery console:
```

update-initramfs -u

```

---

### Post by abc006 on 2008-04-30
OK, I enter recovery mode like you said, and it goes back to the screen like before, but when I enter any of the lines and hit enter, it comes up with this for what Teo wrote:
```
/bin/sh: sudo: not found
```
Or for the one danwood reccomended:
```
/bin/dh: update: not found
```
Anybody know that's going on? Thanks again.

---

### Post by danwood76 on 2008-04-30
You have to type 'update-initramfs -u' exactly like that.
You have probably done 'update initramfs -u' notice the - should be in there otherwise it looks for the command update.

Also in the recovery console sudo is not needed so the command TeoBigusGeekus wrote would be

```
dkpg-reconfigure -phigh xserver-xorg
```
dkpg-reconfigure -phigh xserver-xorg
remember to type it exactly like that.

---

### Post by starmanjb on 2008-04-30
I am having EXACTLY the same problem.  I've done all the suggested solutions (above) with no resolution.  The first time I installed ubuntu (current release) on my Win2K box, I designated drive D for ubuntu while Win2K was on C drive.  That version worked but the best screen resolution I could get was 800 x 600.  So I attempted to update the video drivers and it crashed.  I un-installed it, did a registry clean, rebooted and reinstalled ubuntu.  From that point on I kept getting the same text screen and text as described at the start of this thread.  Any help would be appreciated.

Also, I'm a unclear how to get to this "recovery" console mentioned.  If it's the "menu" option at boot up where you press ESC to go to the menu, then I found it correctly.  If not, clue me in.

---

### Post by abc006 on 2008-04-30
Yeah, that's what I did too, in the ESC menu, but it had the same problems as in "normal" mode. danwood, I haven't tried the one you suggested, but I am almost positive that I entered the code danwood suggested with the dash as exactly written and came out like that... I'll try it again as you mentioned, but...

What's also weird is that it just suddenly happened - unlike starmanjb, I didn't have any problems at all, no re-installing or anything like that, I hadn't changed really anything in the system the first day or so I installed it, but one day it just popped up. I reinstalled it today too, but the same things happened. Again, I'll try what you suggested though, and I'll get back to you.

---

### Post by nekr0phage on 2008-04-30
+1

There is a fair amount of additional information when booting safe mode that was not described here.  I'm still a noobie myself, but the errors seem to indicate an access problem with the hard drive.

Some segments:

```


[   38.982989]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   38.983096]  ata8.00: status: { DRDY ERR }
[   38.983140]  ata8.00:error: { ICRC ABRT }
[   38.983199]  ata8: soft resetting link
[   39.258484]  ata8.00: configured for UDMA/33
[   39.258542]  ata8: EH complete
[   39.306515]  sd 8:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   39.306522]  ldm_validate_partition_table(): Disk read failed.
[   39.306527]  Dev sda: unable to read RDB block 0
[   39.306778]   unable to read partition table
[   39.306783]  sd 8:0:0:0: [sda] Write Protect is off
[   39.306812]  sd 8:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.306828]  sd 8:0:0:0: [sda] 976773168 512-byte hardware sectors 
[   39.306835]  sd 8:0:0:0: [sda] Write Protect is off
[   39.306848]  sd 8:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.307126]  sd 8:0:0:0: [sda] Attached SCSI disk
[   39.311672]  sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   39.363736]  sd 2:0:0:1: [sdc] Attached SCSI removable disk

Done.
       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat /proc/modules/ ls /dev
ALERT! /dev/disk/by-uuid/2823cb27-243e-4f74-a08e-b5e895f1bc78 does not exist.  Dropping to a shell!


```

Then it drops to the busybox shell with the (initramfs) prompt.

I was also having an issue trying to install Fedora 8 on my machine.  That spewed a bunch of hardware garbage that appeared to indicate an issue with my hard drive and then kernel panicked, so I couldn't get any good information from it.

Both of these were x64 installs on my AMD-64 system.  I am using an PATA hard drive, and have no other HDD's connected to PATA or SATA controllers.  The only other non-integrated devices in the system are a Plextor optical, Audigy 2-ZS, and a nVidia 8800 GT.

Off I go to dig through more forums... I'll be checking back on this one and will be sure to update with any more info I come across.

Oh, and this is my first post.  hai!

---

### Post by abc006 on 2008-05-01
Yeah, I got that stuff too, but I figured it was just stuff that always appears in recovery mode... not sure though.

Weird thing is that I tried booting it up today, and it worked fine. But next time it probably won't, like it has before - sometimes it boots up normally, but usually it goes to the "(initramfs)" error. Very annoying.

---

### Post by starmanjb on 2008-05-01
Ok, here's what worked for me.  I discovered that the Ubuntu uninstall doesn't really uninstall all the files.  Wubi leaves some files in the Administrator folder.  Run the Wubi uninstaller.  When done, do a search for Wubi and REMOVE all these files.  Once done, reboot and reinstall.

Thanks Mike for the help.

---

### Post by starmanjb on 2008-05-02
Well, maybe I spoke to soon.  No sooner did I have a working version again, than I tried to install new video drivers to get my screen resolution better than 800 x 600.  When I did that, the screen resolution DROPPED to 600 x 400.  Then I tried to uninstall the video drivers and I'm back with the text screen again!  I did a search for all the wubi files and there were none to remove this time.  So now I'm stuck again.

I've just reinstalled it.  I have the Ubuntu screen up on the monitor and it's doing things like "calculating partitions" and such.  Right now there is a pop up window with the heading, "Checking the Installation..." and it's "Installing system"; "formatting swap space in partition #1 of
/host/ubuntu/disks/...".  Now it's  "creating ext3 file system for  ..... ", rats, it went away.  Now it says it's  "scanning files", now it's "Copying Files".  Ok, done with that, we're doing the reboot thing.  It starts up Ubuntu, the little slider bar starts going back and forth, then the screen darkens and we're back to the text screen, "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)<blinking cursor>


Anyone have any clues what's going on here?

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

### Post by LackingIdeas on 2010-10-13
I've been having the same problem, except whenever I enter ANY command, it returns a message stating "unknown command '(insert command)'

Does anyone know what might be the problem here?

---

