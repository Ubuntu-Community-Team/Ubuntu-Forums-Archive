---
title: "Boot repair disk failed (raid0 array failed Dell xps 8300)"
date: 2015-09-28
forum: General Help
---

### Post by julian29 on 2015-09-28
Hi, 

when I start my PC it shows that the Raid0 array failed and is not bootable. (Raid0 was preset on my Dell xps 8300, I did not know it until it failed) I was not able to repair it with boot-repair-disk. 
The following link leads to the report   [http://paste.ubuntu.com/12601369/](http://paste.ubuntu.com/12601369/)
I do not know how to interprete it. (plus my PC came with windows 7 preinstalled, not windows vista)
Do you know how I can get my data back?

Thanks in advance!

---

### Post by tgalati4 on 2015-09-28
Welcome to the forums.

Many Windows Vista and 7 machines came with RAID0 which gives you roughly double the disk speed, since the data is striped across two identical drives.  This allows the manufacturer to use cheaper, spinning drives (since large SSD's are expensive) and give a speed boost since Vista and Win7 are hogs on older hardware.

Of course, if a disk fails, 100% of your data is lost because it is striped across both drives, so each file has about 1/2 of its contents on the bad drive in lots of tiny stripes.  I'm sure there are Windows tools to try to recover and reassemble these bits and pieces.  I don't know of any Linux tools to do that.

Otherwise, the Dell Utility partition seems OK.  Can you boot into it?  What utilities are available?

I don't see any recovery partitions on your 2 disks, sometimes there are backup/recovery partitions that will store User data.  Otherwise, you will have to rely on your personal data backups.  Recovery on RAID0 is not easy.

Boot a LiveUSB, plug in an ethernet cable, load smartmontools and get the SMART status of both drives.

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
sudo smartctl -a /dev/sdb
```

Capture the output and save it, since you will lose the output when you shut down.

```

sudo smartctl -a /dev/sda > sda_SMART.txt
sudo smartctl -a /dev/sdb > sdb_SMART.txt
```

If you can determine the disk's problem, you may be able to revive it long enough to perform a data recovery.

Perhaps copy it to a blank USB stick.

Using preinstalled RAID0 is a disservice to customers.

---

### Post by oldfred on 2015-09-28
Boot-Repair is not really for Windows repairs, it can only do very minor things for Windows.
You need your Windows repair CD or flash drive. When I got my Dell it told me to both make a full Dell recovery & Windows recovery disks.

For NTFS you should use chkdsk to see it that works.
If you have access to another Windows 7 any version but needs to be either 32bit or 64 bit to match yours.
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by julian29 on 2015-09-29
Thank you for the replies! 

I followed your instructions, but then I found and followed these instructions: [http://www.overclock.net/t/478557/howto-recover-intel-raid-non-member-disk-error](http://www.overclock.net/t/478557/howto-recover-intel-raid-non-member-disk-error) 
 But I did it with a bootable ubuntu cd and installed testdisk like [this: http://askubuntu.com/questions/398335/how-to-install-testdisk-in-ubuntu-13-10]("http://askubuntu.com/questions/398335/how-to-install-testdisk-in-ubuntu-13-10")
Before that I created drive-images(using ubuntu) on an external drive, just in case.

Windows 10 works again (I used the  windows7 installation/repair cd)! I got back all of my data and I am currently saving it to an external drive.

I hope this can help someone in the future!

---

### Post by tgalati4 on 2015-09-29
And understand that your RAID0 is a ticking time bomb that will blow up at any time in the future.  It's designed that way, by the manufacturer.  I would get a label maker and put this on the bezel:  "This computer is running RAID0 and can fail at any time.  Back up your important files."

---

