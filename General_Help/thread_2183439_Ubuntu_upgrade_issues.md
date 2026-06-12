---
title: "Ubuntu upgrade issues"
date: 2013-10-24
forum: General Help
---

### Post by kerleym on 2013-10-24
Hi all, if this has already been asked, my apologies.  I did a search but couldn't quite find an answer to my problem.  I have an Acer Aspire 5517 with a 320GB SATA hard drive that had Windows 7 on it.  I puchased a 256 GB SSD drive and decided to load Ubuntu as my operating system.  I used the instructions for installing Ubuntu via USB drive.  I had version 13.04 and everything was fine.  I love ubuntu by the way.  I recently upgraded to 13.10 and that's when the problems started.  It began with just not being able to connect to my wifi.  My wife's computer and our phones all connect to wifi just fine.  I tried everything I could think of to no avail (it doesn't even give me the option of trying to connect wifi, it just has Enable Networking).  Well now, Ubuntu 13.10 has just quit working.  It first started a couple of nights ago when I was trying to wake the computer up.  My login screen would appear and then the computer would just go back to sleep, and it just kept doing this over and over.  Then when I hard powered it down and powered it back up, I could log in, but then I kept getting a notification that Ubuntu has encountered a problem.  I tried downloading 13.10 on my USB drive and reinstalling it, but I'm still having the same issues.  Any suggestions?

---

### Post by fantab on 2013-10-25
You are dual-booting, right? 
Can you boot into Windows?
What graphics card does your machine have?
When you've set up the SSD, did you change the SATA mode in BIOS to 'AHCI'?

Boot with Ubuntu DVD/USB, run the following commands from the terminal [ctrl + alt + T] and post its output here:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by kerleym on 2013-10-25
Thanks for the reply!  Before I try your suggestion, I wanted to mention that I do not dual boot.  I purchased the SSD for the sole purpose of loading Ubuntu onto it, so Ubuntu is my only OS right now.  My graphics card is an ATI Radeon HD 3200 GPU.  I did not change the SATA mode in BIOS.  I will have to do that.  I'll try running the code in terminal and let you know what I find.  I also forgot to mention, prior to having trouble with Ubuntu my Unity icons all disappeared.  I had none along the top bar (date/time, power, wireless) and none along the left side either.  The only thing that would show up were any icons I had on my desktop.

---

### Post by kerleym on 2013-10-26
SATA mode in BIOS was changed to AHCI.

This is what was displayed when I ran parted:

Model: Linux device-mapper (crypt) (dm)
Disk: /dev/mapper/cryptswap1: 4022MB
 Sector Size (logical/physical): 512B/512B
Partition Table: loop

Number     Start     End          Size         File system         Flags
1               0.00      4022MB    4022MB   linux-swap(v1)     
 
error: /dev/mapper/ubuntu--vg-swap_1: unrecognized disk label

Model: Linux device-mapper (linear) (dm)
Disk: /dev/mapper/ubuntu--vg-root: 252GB
 Sector Size (logical/physical): 512B/512B
Partition Table: loop

Number     Start     End          Size         File system         Flags
1               0.00      252GB     252GB      ext4     
 
error: /dev/mapper/sda5_crypt: unrecognized disk label

And when I ran fdisk:

Sector size (logical/physical): 512 bytes/512 bytes
I/O Size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg--root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4022MB, 402233736 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856128 sectors
units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O Size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg--swap_1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 4022MB, 402233736 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856128 sectors
units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O Size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

On a side note, I just booted up the laptop and my unity desktop is back.  Still can't connect to my wifi and I'm still getting the same error message.

---

### Post by fantab on 2013-10-26
AFAIK, SSD only works with AHCI mode. 
There seems to be some problem with your SWAP partition. I think you have encrypted your HDD, not sure how to deal with encrypted disks... Wait for someone who knows their way around encrypted disks to respond.

Meanwhile run the following command:
```
sudo blkid
```

Note the UUID of your SWAP partition.

```
sudo gedit /etc/fstab
```
Gedit will open fstab file.
Compare the UUID of the SWAP partition with that of the UUID you got from the above command. If they are same then its ok. If there is mismatch then replace the UUID in /etc/fstab with UUID you got from the *_blkid_* command and SAVE the file.
The quatation marks [""] are important in /etc/fstab don't miss them.

---

### Post by kerleym on 2013-10-27
For blkid I get:

/dev/sda1: UUID="d2981b10-52ec-4160-99a1-c99ce82226bb" TYPE="ext2" 
/dev/sda5: UUID="f4af44fd-9276-48e8-ab14-11a5b2a17900" TYPE="crypto_LUKS" 
/dev/mapper/sda5_crypt: UUID="e0hW5K-pVmg-OhGu-rH2t-0FvY-G8GF-23UvzD" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="cff0842d-9a07-4f40-ad23-7e03643209c2" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="6812b535-dc18-4876-8f40-0e4bc44c3dc5" TYPE="swap" 

For gedit I get:

** (gedit:2638): WARNING **: Could not load Gedit repository: Typelib file for namespace 'GtkSource', version '3.0' not found

(gedit:2638): IBUS-WARNING **: The owner of /home/fog/.config/ibus/bus is not root!


Now I'm still learning my way around terminal and the commands.  I may have done something in error.

---

### Post by kerleym on 2013-10-27
I forgot to mention, my computer happened to connect to wifi when I posted the above code.  I'm still connected but the connection seems sluggish.

---

### Post by kerleym on 2013-10-28
Well, I've sort of solved my problem.  My computer just crashed.  So I downloaded 12.04 LTS and burned it to a DVD.  I'm now running that and everything seems fine so far.  I appreciate all the help though!

---

