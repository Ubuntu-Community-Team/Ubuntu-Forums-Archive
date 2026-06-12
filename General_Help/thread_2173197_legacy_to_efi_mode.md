---
title: "legacy to efi mode"
date: 2013-09-08
forum: General Help
---

### Post by linuxonbute on 2013-09-08
I  am running ubuntu 12.04 64 bit with all updates on my HP G6-1154 laptop.
It appears to have been installed in legacy mode which I didn't concern myself with at the time.
This last week i bought a verbatim 3TB usb3 external drive which I had intended to set up with my raspberry pi as a backup and for photo/video sharing on my home network.
When I unpacked it there was a note with it saying it was partitioned as 2 drives and it appears as /dev/sdb and /dev/sdc.
I have been looking at various threads to try to figure out how I can make it 1 device. One suggested I set it to gpt on both which I did but that hasn't helped as it is still 2 devices. Since then another suggests changing the internal system to efi mode using boot-repair. This does report a small efi partition on the internal disc.
I could change to this but then the article said to change the boot option to uefi mode.
There comes the snag as there is no option in the bios referring to legacy/uefi  in fact uefi is not mentioned anywhere. I only bought the laptop about 6 weeks ago so I fully expected be able to sort it out.
I suspect I could change the drive to efi mode and if it fails I suspect I could boot a live Cd, download boot-repair and change the drive back to legacy mode.
I also wonder if the problem relates to the firmware on the external disc drive.
What I could do with is your thoughts as to whether this is possible and if it would mean I could change the external drive to one device. 
thanks

---

### Post by bewareofthephog on 2013-09-08
Try installing gparted.  This will let you delete the two partitions, then create a new single one.  I'm sure some of the more hardcore linux people will say use fdisk, and I'm normally all for the terminal except partitioning, I love gparted.  WARNING:  I have no idea if this will work and you might want to proceed with caution, the only reason I'm unsure of this method is because I've never run into a problem like yours.  But if it's just a matter of deleting the old and creating a new then this should work.  (I think ;))

---

### Post by linuxonbute on 2013-09-08
Hi,
thanks for the suggestion. Unfortunately that's the first thing I tried. it was useful for changing all the partitions to gpt from msdos but that was all.
I should have added more information initially.
It appeared as /dev/sdb1 and /dev/sdc1 which my system had no problem mounting. using fdisk at that time ( they were both msdos types )
I was able to delete the partitions but then it still appeared as 2 devices. I changed them to gpt and rebooted my laptop but they were still 2 devices
It is actually, physically, 1 disc and yet the o/s sees it as 2. I can create and delete partitions as often as I like but it doesn't turn it into 1 disc to the o/s.
I have emailed verbatim to see if they can help but I don't suppose they will reply before monday;) as I do suspect it is the firmware on the device which is causing the problem.

---

### Post by oldfred on 2013-09-08
Do not use fdisk. If wanting a command line tool use gdisk which is for gpt partitioned drives.
Do not change a 3TB drive to MBR(msdos) or will be only be 2TB.
You want gpt as that supports drives over 2TB. That may be why the vendor did something special to make it be two drives. Only if used with XP which does not work with gpt would you maybe want that special configuration.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Do not mix UEFI with gpt. UEFI needs gpt partitioning but is how you boot from UEFI/BIOS. Windows only boots from gpt partitioned drives with UEFI, but Ubuntu can boot from gpt partitioned drives with either UEFI or BIOS. With UEFI you do need an efi partition as first on drive and any gpt drive that might in the future have an operating system should have the efi partition as the first partition. It does not have to be large 200 to 300MB formatted as FAT32 with boot flag.

Found this. See post almost half way down with email from Verbatim.
[http://www.tomshardware.com/forum/274015-32-external-usb3-drive-shows-devices](http://www.tomshardware.com/forum/274015-32-external-usb3-drive-shows-devices)

---

### Post by linuxonbute on 2013-09-08
Hi oldfred thanks for the links. I only have Ubuntu on my laptop but ( although she doesn't know it) my wife still has Win7 on hers. I will download the update there and try it when I get time and let you know how I get on.

i converted the original to gpt from msdos as a first stab at sorting it. fdisk reports that it can see gpt partitions but that it cant edit them. gdisk does seem to work as does gparted.

---

### Post by linuxonbute on 2013-09-09
I tried the suggestions but the drive was not recognised by the software. I guess it's because mine isn't a "Store and Go" drive but a "store and Save" drive. However I had emailed verbatim and they replied and attached a suitable piece of software to the email. I ran it from a Win 7 machine and it did the job fine.
Here is a link to the file i used, which I have uploaded to my box account:    [https://app.box.com/s/h7xdyt5s0kyi70y87e81](https://app.box.com/s/h7xdyt5s0kyi70y87e81)
I hope it helps others.

---

