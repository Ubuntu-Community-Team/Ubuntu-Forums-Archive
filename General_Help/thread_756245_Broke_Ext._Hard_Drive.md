---
title: "Broke Ext. Hard Drive"
date: 2008-04-15
forum: General Help
---

### Post by Bios___ on 2008-04-15
Hi there,

my friend has dropped her 400gb Western Digital External Hard Drive, and so far I have managed to connect it to my desktop via USB and fortunatley Ubuntu has detected the drive, however upon an attempt to open it I get the message:

"Unable to mount media

There is probably no media in the drive"

I and her, would appreciate any help anyone can provide as this hard drive contains all of her University work.

I am begging anyone that can lend a hand.

Also I will add that it has been a while since I have used Ubuntu, but have a basic understanding of it. So please any help would be appreciated!

---

### Post by Bios___ on 2008-04-15
Bump.

I've found that the hard drive is apparently "not a block device"

and is referred to as sg2 in the device manager...This is my assumption as I said it's been a while since I used Ubuntu

---

### Post by retrow on 2008-04-15
Try loading nautilus as root, i.e. 'sudo nautilus'

Then if you can see the volume, you can right click on it and say mount.

And while I have been using Ubuntu for 2+ years, I know very very little, so I could be dead wrong.

---

### Post by Bios___ on 2008-04-15
The hard drive didn't appear, it just gave me a folder called Desktop.....

When connected to a Windows OS it mentioned about the disk needs to be initialized....but now it doesn't.

Im connecting it to Linux and Windows trying different ideas and such, any ideas.....?

---

### Post by ryanhaigh on 2008-04-15
Could you post the output of the commands below after the device is plugged in and 'recognised':
```

lsusb
dmesg (just the last bit that appears after plugging the device in)
mount
sudo fdisk -l

```

---

### Post by Bios___ on 2008-04-15
lsusb
> Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 07d0:1202 Dazzle 
Bus 001 Device 001: ID 0000:0000 

dmesg
> [ 6232.476000] end_request: I/O error, dev sdc, sector 0


mount
> proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


sudo fdisk -l

> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc24cc24

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8942    71826583+   7  HPFS/NTFS
/dev/hda2            8943       10208    10169113+   7  HPFS/NTFS
/dev/hda3           10209       14593    35222512+   f  W95 Ext'd (LBA)
/dev/hda5           10209       14593    35222481    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99abff25

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401    c  W95 FAT32 (LBA)


The 120gb and 200gb hard drives are the ones connected to my desktop. The damaged hard drive is 400gb.

Thanks

---

### Post by ryanhaigh on 2008-04-16
The only thing that I can suggest is that you try taking the hd out of the caddy and connecting it directly, although I hate to say it but it doesn't look good. That error in dmesg obviously means your comp cant talk to the drive at the moment, hopefully its a problem with the caddy as IO errors probably mean you couldn't even clone the drive with dd.

---

### Post by Bios___ on 2008-04-16
Ok I will try that as soon as I get back from my lecture. Thanks for that. 

I'll keep you posted.

---

### Post by Bios___ on 2008-04-16
Unfortunately that didn't work.

I tried booting into Linux with the hard drive connected via Sata, and it caused the boot to crash.

So I proceeded to try and boot Ubuntu without the hard drive connected via sata, and connect it once it had started up.

The drive hasn't appear in the File Browser.

---

### Post by stefangr1 on 2008-04-16
Hard disks are normally not hot pluggable, you should therefore NEVER plug in a hdd while the system is already on. Your system can crash if you do so.

I think the only way to get your data back is to go to a data recovery specialist.

---

### Post by anaconda on 2008-04-16
> **stefangr1 said:**
> Hard disks are normally not hot pluggable, you should therefore NEVER plug in a hdd while the system is already on. Your system can crash if you do so.

I think the only way to get your data back is to go to a data recovery specialist.

SATA hd:s are hotpluggable.. or atleast they should be.. My motherboard came with a sticker which said something like:" This motherboard doesnt support the hotplugging of SATA hd's"

---

### Post by aquavitae on 2008-04-16
Have you tryed googling for something like "recovering damaged disks"? I had a similar problem with a flash drive a while back and found a couple of docs that helped.  I didn't manage to actually get the data back cos the drive was totally fried, but it should work if there is anything there. I'll post back if I find the docs I used.

---

### Post by aquavitae on 2008-04-16
Try:
[http://www.linux.com/articles/56588]("http://www.linux.com/articles/56588")
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html")

I think there are a couple of tools that will be useful (mentioned in the links): testdisk, photorec and ddrescue.  Just remember that if the drive you're working with is 400Gb, you may have problems trying to copy it to a 200Gb drive... Also your dmsg output says there's an error at sector 0.  IIRC, this might make the drive completely unreadable, but I'd still try ddrescue.

Good luck!

---

### Post by Bios___ on 2008-04-16
Thankyou for your input everyone! I will give that a try aquavitae and let you know my results.

Also I have done some research into data recovery specialists and my friend has made some calls and may have an appointment for tomorrow, but I will try this also.

Thanks for the help so far.

---

