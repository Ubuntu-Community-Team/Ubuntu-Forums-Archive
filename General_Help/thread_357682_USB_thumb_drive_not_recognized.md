---
title: "USB thumb drive not recognized"
date: 2007-02-09
forum: General Help
---

### Post by Ewat on 2007-02-09
I am still very new to Linux and require much help.

My computer is unable to recognize the usb thumb drive that I want to use. It is formated FAT32.The only thing listed in "Computer" is the CD drive and File System. I have tried following some of the post listed, but I am not sure that they fit my situation.

I am working on an IBM T40 Laptop with two USB drives. 

Thank you.

---

### Post by taurus on 2007-02-10
What's the output of this command from a terminal after you've inserted the drive into the USB slot?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Ewat on 2007-02-10
Taurus,

Thank you for your response. After taking a break, I logged in, read your message, and the thumb drive appeared, both on the desktop and in "Computer"!!!  Kinda weird. 

Well, I tried that command and the only thing that came back was ">". This is what I typed in 
"sudo fdisk -|". I am not sure what I did wrong.

Will this procedure also help recognize my hard drive.

I appreciate your help.

---

### Post by Ewat on 2007-02-10
Okay....

I just went to take a look at the thumb drive. It is not there!!!! It disappeared...

I didn't do anything different. Let me try the sudo fdisk -| again.

---

### Post by gradedcheese on 2007-02-10
That's the lowercase letter L in what he posted ;)

You can take a look at 'dmesg' to see what happened, and perhaps find out why it took so long (see any USB errors?).   An nice experiment to try:

1) clear dmesg log (run "sudo dmesg -c")

2) eject the USB disk in question (right-click, choose 'Eject') and unplug it when it dissapears

3) wait 30 seconds or so, plug the disk back in

4) wait until the disk is recognized (or if you want, wait just a few seconds) and run "dmesg" again to see what messages the insertion generated.  The messages should indicate that a USB device was found, it was identified as such-and-such, a particular driver was chosen, etc.

---

### Post by dcstar on 2007-02-10
> **Ewat said:**
> Taurus,

Thank you for your response. After taking a break, I logged in, read your message, and the thumb drive appeared, both on the desktop and in "Computer"!!!  Kinda weird. 
...........

If your USB drive was already plugged in and did not appear after a boot - and you are using "Auto-login" - then disable the auto-login and set up a 5 second Timed Login.

There is an issue with the X system starting too quickly at boot before some other processes have finished initialising.

---

### Post by Ewat on 2007-02-10
Taurus,

Sorry to take so long; I had to get some sleep. Here is the output after correctly typing the commands:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4662    37447483+  83  Linux
/dev/hda2            4663        4864     1622565    5  Extended
/dev/hda5            4663        4864     1622533+  82  Linux swap / Solaris

The thumb drive is working this morning, by the way.

Thanks again for your help and that of the others responding to my Post.

---

### Post by Ewat on 2007-02-10
Well, the drive is not working again after the dmesg message. Here are the last few lines of what happened after entering the second dmesg command:

[17182862.188000] usb 4-4: new high speed USB device using ehci_hcd and address 67
[17182862.692000] usb 4-4: new high speed USB device using ehci_hcd and address 68
[17182864.708000] usb 4-4: new high speed USB device using ehci_hcd and address 75
[17182864.968000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[17182864.968000] hub 4-0:1.0: hub_port_status failed (err = -32)
[17182868.992000] usb 4-4: new high speed USB device using ehci_hcd and address 89
[17182869.496000] usb 4-4: new high speed USB device using ehci_hcd and address 90
[17182872.016000] usb 4-4: new high speed USB device using ehci_hcd and address 99
[17182875.040000] usb 4-4: new high speed USB device using ehci_hcd and address 110


From the little that I am able to understand and experience, the usb drive is unstable, going in and out. Let me know if you need to see more.

Thank you for your support.

---

### Post by gradedcheese on 2007-02-10
> 
[17182864.968000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[17182864.968000] hub 4-0:1.0: hub_port_status failed (err = -32)


I've had this sort of thing happen with a USB drive that was actually failing (on any PC you plug it in to).  'wound up throwing it away.  Can you test another USB thumb drive?

---

### Post by Ewat on 2007-02-10
Hi,

I have exchanged the thumb drive with another that I have and the result is the same. It's not working.

This is a fairly serious situation for me. I use thumb drives to keep my business files and transfer them to and from work. What do I do now? What if I reinstalled Ubuntu, would that help? Are there commands I can use to force the usb thumb drive to work?

I really need your help.

---

### Post by gradedcheese on 2007-02-10
Ok, after inserting the thumb drive and waiting about 5 seconds, run:

```

dmesg | tail

```

I don't have a thumb drive here at the moment, but here's my iPod being plugged in:

```

[17192519.660000] sdb: Mode Sense: 68 00 00 08
[17192519.660000] sdb: assuming drive cache: write through
[17192519.668000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[17192519.672000] sdb: Write Protect is off
[17192519.672000] sdb: Mode Sense: 68 00 00 08
[17192519.672000] sdb: assuming drive cache: write through
[17192519.672000]  sdb: sdb1 sdb2
[17192519.680000] sd 1:0:0:0: Attached scsi removable disk sdb
[17192519.680000] sd 1:0:0:0: Attached scsi generic sg1 type 0

```

What this says is: "hey, I found a disk, with /dev/sdb1 and /dev/sdb2 partitions" ...what does yours say?

---

### Post by mgmiller on 2007-02-20
I also use thumb drives to transfer and backup/restore files between my work windows XP box and my home Ubuntu 6.10 box.  I have 2 OCZ rally thumb drives.  A 1 gig and a 2 gig.  They are very fast to read/write and work perfectly in Ubuntu and Windows.  As with all these devices, when you unmount them in Ubuntu, the little power light will stay illuminated.  It's safe to remove as long as the dismount graphic has stopped.  

The only other thought I have is for you to check in your BIOS and see if "legacy USB" is enabled.  If it is, try disabling it.  If it's disabled, try enabling it.

Good Luck

---

