---
title: "How to disable hardware detection for a CD drive"
date: 2006-10-30
forum: General Help
---

### Post by lhtown on 2006-10-30
Since I upgraded to Edgy, I have been getting an error at bootup. Basically, I get a screenful of the following error message:
expected NULL handler on exit hdc: ide_intr: huh?

It scrolls for a minute or two as though it is searching memory positions or something and then it appears to fsck my hdc and then goes on with no obvious problems.

I have an Acer Travelmate290 with a defective CD/DVD writer that is at hdc.

It seems that my problem is basically because of the hardware fault. However, I don't want to take out my cdrom for aesthetic reasons, but I can't figure out how to disable it either.

I tried configuring the laptop's bios settings, but it doesn't let me do anything with it. I also deleted the lines relating to my floppy and cdrom from my fstab with no obvious results.

It seems that it is finding it with automatic hardware detection of some kind, but I don't know how to blacklist my cdrom or disable it. 

Is there a sofware option within ubuntu to do this, or am I stuck with my machines bios settings which won't let me do anything? Or is this relating to another problem altogether?

---

### Post by tzulberti on 2006-10-30
To disable automatic mount of cd/dvds in Gnome, you should go to:
System->Preferences->Removable Drives and Media...
There you should disable all the options related to your cdrom

---

### Post by lhtown on 2006-10-31
> **tzulberti said:**
> To disable automatic mount of cd/dvds in Gnome, you should go to:
System->Preferences->Removable Drives and Media...
There you should disable all the options related to your cdrom

Thanks for the tip, but it doesn't help my situation although there are some interesting options there.

I need to be able to mount removeable media (like my usb memory stick and digital camera). I just want to convince the computer that the CD drive doesn't exist regardless of whether or not I insert a CD.

---

### Post by altaaa on 2006-11-14
Try adding this to your /etc/rc.local:

[FONT="Courier New"]rmmod ide_cd
rmmod cdrom[/FONT]


put these lines before [FONT="Courier New"]exit 0[/FONT].

Worked for me.

---

### Post by lhtown on 2006-11-14
altaaa,

Thanks for the tip. I tried it, but I can't see that it changed anything for me.

Maybe you are on the right track, but I am not quite sure how I might adjust it or what other options I could try. I have never played with that script and kernel modules aren't really my thing.

---

### Post by altaaa on 2006-11-15
You're right. What I suggested has nothing to do with the actual detection, it just unloads the drive *after* it has been detected.

I'm not sure how and if you can disable linux to detect the hardware. Would it be safe to remove items from the /dev directory?

edit:
The items in the /dev dir are generated at startup.
I would try to (re)move the modules themselves. Mine are located at (I think):

/lib/modules/2.6.17-10-generic/kernel/drivers/ide/ide-cd.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/cdrom/cdrom.ko

But I must warn you: I am no linux guru, so try it at your own risk!

---

### Post by lhtown on 2006-11-29
Does anyone have any other ideas?

---

### Post by fnf on 2006-12-08
Since the device detection happens before any other data is read, the only place to look for is kernel parameters. You may want to pass this as a kernel option:

```
hdc=noprobe
```

To make the drive active again, the only way I'm aware of is to reload the kernel on the fly, which is not quite peaceful. I can imagine a much easier way to do this (udev ?) but haven't found a spare time yet.

---

### Post by lhtown on 2006-12-08
I added hdc=noprobe into /boot/grub/menu.lst but it didn't seem to change anything. Am I putting it in the wrong place?

---

### Post by fnf on 2006-12-08
That option effectively disables detection of your optical drive, you can 'dmesg | grep hdc' to ensure the drive is no longer active. If you're still experiencing problems, that's probably not related to hdc device but the IDE controller on the mainboard, which is rarely mutate-able on laptops, unfortunately.

Did you try to build a custom kernel ?. It may have already been fixed if that was a kernel bug. Look at [this thread]("http://ubuntuforums.org/showthread.php?t=157560") for a general guide line.

---

### Post by lhtown on 2006-12-08
fnf,
Thanks for your help. Here is the output from dmesg. It is actually much longer, but I truncated the results for easier reading. This is the end of it.

I haven't tried a different kernel with Edgy except to use the "generic" kernel instead of the 386 kernel. The drive has had a problem for several years rendering it  unusable, but for some reason, Edgy has to give me a long error message on boot up which no other version has.

Does this error message confirm the likelihood of a controller problem?

```
[17179646.740000] hdc: ATAPI reset complete
[17179646.740000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.740000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.740000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.740000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.740000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.740000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.740000] hdc: ide_intr: huh? expected NULL handler on exit
[17179646.788000] hdc: ATAPI reset complete
[17179646.788000] end_request: I/O error, dev hdc, sector 24
[17179646.792000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.792000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.792000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.792000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.792000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.792000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.792000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.792000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.792000] hdc: ide_intr: huh? expected NULL handler on exit
[17179646.840000] hdc: ATAPI reset complete
[17179646.840000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.840000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.840000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.840000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.840000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.840000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.840000] hdc: ide_intr: huh? expected NULL handler on exit
[17179646.888000] hdc: ATAPI reset complete
[17179646.888000] end_request: I/O error, dev hdc, sector 28
[17179646.892000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.892000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.892000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.892000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.892000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.892000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.892000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.892000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.892000] hdc: ide_intr: huh? expected NULL handler on exit
[17179646.940000] hdc: ATAPI reset complete
[17179646.940000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.940000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.940000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.940000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.940000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.940000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.940000] hdc: ide_intr: huh? expected NULL handler on exit
[17179646.988000] hdc: ATAPI reset complete
[17179646.988000] end_request: I/O error, dev hdc, sector 0
[17179646.992000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.992000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.992000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.992000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.992000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.992000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.992000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179646.992000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179646.992000] hdc: ide_intr: huh? expected NULL handler on exit
[17179647.040000] hdc: ATAPI reset complete
[17179647.040000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179647.040000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179647.040000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179647.040000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179647.040000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17179647.040000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17179647.040000] hdc: ide_intr: huh? expected NULL handler on exit
[17179647.088000] hdc: ATAPI reset complete
[17179647.088000] end_request: I/O error, dev hdc, sector 4

```

---

### Post by fnf on 2006-12-08
It looks like Edgy was still trying to read from the drive. Can you verify that '/dev/hdc' exists after it boots up ?.

I'm stuck here, sorry, the last thing I'd want to do do before reverting back to Dapper is to try the newest kernel (and possibly with CD-ROM support disabled). The process is pretty fast if you don't mind a bloated kernel (just use the default), it will take about 15 to 60 minutes to compile depending on the specs and kernel configuration.

---

### Post by lhtown on 2006-12-09
hdc exists. It even automounts with an icon on the desktop (there is no cd in the drive). I can even eject the tray by right clicking and selecting eject.

Note that the CD drive has worked only very VERY sporadically for the last several years to the point that I haven't even tried it in a long time.

---

### Post by fnf on 2006-12-09
Please verify that your menu.conf or the GRUB detail menu looks like this:

```
title    ...
root     ...
kernel   /vmlinuz-2.6.19 root=... ro hda=noprobe hdb=noprobe hdc=noprobe hdd=noprobe
initrd   /initrd.img-2.6.19
quiet
savedefault
boot
```

Not that all the lines are important but 'kernel', I just want to make sure they're not messed up. Note that I've also added 'hda=noprobe' to see if the system can even be booted. Parameter parsing is the most basic feature, it's hard to believe that was a kernel bug, or GRUB's.

---

### Post by lhtown on 2006-12-09
fnf,

Thanks for your help!

I had the kernel parameter hdc=noprobe on the wrong line. I had just stuck it into the file /etc/grub/menu.lst in a random place.

I put in on the same line as kernel like you explained and it works like a charm.

Thanks again for sticking with me on this in my ignorance.

---

