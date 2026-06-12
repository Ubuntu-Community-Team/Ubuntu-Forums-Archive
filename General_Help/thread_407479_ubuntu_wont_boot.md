---
title: "ubuntu wont boot"
date: 2007-04-12
forum: General Help
---

### Post by richardjennings on 2007-04-12
I have been using Ubuntu for a while now. Yesterday I was playing about with F4L from sourceforge. 

The last change to the system before reboot was to install Qt3 dev tools with synaptic. 

I have tried to boot the system up again today with no luck whatsoever.

I have tried running fsck from the live cd, it reports no problems for either of my partitions. hda6 and hda7

In grub I have tried booting 

2.6.17-11-generic
2.6.17-11-generic (recovery mode)
2.6.17-10-generic
2.6.17-10-generic (recovery mode)

in recovery mode for both kernels, the boot hangs at:

[17179584.144000] Type: CD-ROM ANSI SCSI revision: 00

Otherwise, the boot shows Ubuntu splash, the indicator bar does not show any progression, then reverts to a black screen with a white blinking cursor.

The processor fan is working a lot harder than it usually would be during boot.

I am currently running memtest86 - (mainly because I couldnt think of anything better to do)

If it shows an issue il post as a follow up.

the commands I used to check the hard drives where:

sudo fsck /dev/hda7
sudo fsck /dev/hda6

---

### Post by NICU on 2007-04-12
How long have you waited for the system to boot?  I had a very similar problem after replacing a DVD-RW drive.  The system would start to boot Ubuntu, the splash screen would show up, the progress bar wouldn't show any progress.  After 10-20 seconds the screen would go blank with a blinking cursor on the top left corner of the screen.  After close to 5 minutes the system would start booting like normal.  I don't know exactly what fixed it, but after 5-6 reboots the problem went away.  

If you wait 5-10 minutes will your system boot?

---

### Post by richardjennings on 2007-04-14
i have tried rebooting many many times now, & left the cursor blinking for upwards of a half an hour a few timer.

seems something has broken. Any ideas what? or at least - how I can salvage my install?

---

### Post by GexX2 on 2007-04-14
I had a similar problem just now. All my kernels hung at the same spot on recovery mode and normal boots. I had to delete my old (dying) drive's partition, and now it starts fine. Sounds similar. Maybe unplug you CD rom drive to see if Linux boots without it? That looks more like a driver though...

---

### Post by richardjennings on 2007-04-14
unfortunately the comp in question is a laptop. Makes unplugging the cd drive rather laborious. You deleted you old partition? What do you mean? Did you simply reinstall ubuntu?

---

### Post by GexX2 on 2007-04-14
No, mine would always stall in the recovery mode at fsck, and wouldn't load anymore after that, so I figured it had something to do with the older drive I had that I was using as a Windows to Linux transfer drive. This was right after I upgraded to the newest kernel in fiesty. So I just deleted the partition on my transfer drive and ubuntu started booting again. I've rebooted ~3 times since then.

---

### Post by mac.ryan on 2007-04-14
If the problem is with the *fsck*, then there is an *hide* option you could use at the boot time, that would prevent fsck to run on selected devices/partitions. See [this article]("http://forums.pcper.com/showthread.php?p=4035102") for more info.

---

### Post by richardjennings on 2007-04-14
i seem to have fixed it by adding resume = /dev/hda6

no idea why that works but it does :)

---

