---
title: "Repair USB-Stick (Ubuntu 12.04)"
date: 2013-10-17
forum: General Help
---

### Post by Wa_Si on 2013-10-17
Hi,
 i have an USB 3.0 Stick (Verbatim Store'n Go 16 GB usb 3.0, FAT32 formatted) and it worked fine until a few days ago, when I removed the sitck without unmountig it. From this time on, I could not access the usb-stick. Ubuntu doesn't automount it and windows said, that the sitck is not formatted. Anyway... I googled for a solution and found testdisk. With testdisk I was able to browse trough the directories on the stick and I wrote the partition-informations to the stick, as described [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") . 
After doing this, the stick was completely unaccessible:(. Windows doesn't do anything when I connect the stick and in ubuntu I get the following:

```

~$ sudo dmesg | tail -n 20

[   35.059513] [fglrx] Firegl kernel thread PID: 1190
 [   35.059705] [fglrx] IRQ 51 Enabled
 [   35.235511] [fglrx] Gart USWC size:1280 M.
 [   35.235514] [fglrx] Gart cacheable size:508 M.
 [   35.235518] [fglrx] Reserved FB block: Shared offset:0, size:1000000  
 [   35.235519] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000  
 [   35.235521] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000  
 [   35.393259] postgres (1192): /proc/1192/oom_adj is deprecated, please use /proc/1192/oom_score_adj instead.
 [   40.167792] init: plymouth-stop pre-start process (1867) terminated with status 1
 [   40.439996] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
 [   43.630082] eth0: no IPv6 routers present
 [   54.114326] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
 [   84.085554] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
 [  124.050440] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
 [  138.120864] usb 4-2: USB disconnect, device number 2
 [  146.996044] usb 2-1.4: new high-speed USB device number 5 using ehci_hcd
 [  147.091395] scsi7 : usb-storage 2-1.4:1.0
 [  148.088415] scsi 7:0:0:0: Direct-Access     Phison   USB DISK 50X     PMAP PQ: 0 ANSI: 4
 [  148.090285] sd 7:0:0:0: Attached scsi generic sg2 type 0
 [  148.094463] sd 7:0:0:0: [sdb] Attached SCSI removable disk

```

and this
```

~$ sudo fdisk -l
  
 Disk /dev/sda: 640.1 GB, 640135028736 bytes
 255 Köpfe, 63 Sektoren/Spur, 77825 Zylinder, zusammen 1250263728 Sektoren
 Einheiten = Sektoren von 1 × 512 = 512 Bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Festplattenidentifikation: 0x55cf96d1
 

    Gerät  boot.     Anfang        Ende     Blöcke   Id  System
 /dev/sda1            2048    41945087    20971520   27  Hidden NTFS WinRE
 /dev/sda2   *    41945088    42149887      102400    7  HPFS/NTFS/exFAT
 /dev/sda3        42149888  1054946762   506398437+   7  HPFS/NTFS/exFAT
 /dev/sda4      1054947326  1250263039    97657857    5  Erweiterte
 Partition 4 does not start on physical sector boundary.
 /dev/sda5      1248307200  1250263039      977920   82  Linux Swap / Solaris
 /dev/sda6      1054947328  1248305151    96678912   83  Linux

```

Then I tried to mount the stick using:
```

mount -o ro,offset=$((63*512)) /dev/sdb /mnt

```

The result was "no medium found"
```

/dev/sdb: Kein Medium gefunden

```

Can anyone help? Thanks in advance.

---

### Post by varunendra on 2013-10-18
Hello Wa_Si, and Welcome to the forums!

The partition table that testdisk writes is not always liked by other systems that rely on it.

Please use testdisk again to access the data through it, and in the same stage where you can list and browse through the directories, use "a" to select all files/folders in a directory, then "C" to copy them to an external medium (or small "c" to copy the contents individually). By default it will save the contents in your Home directory, but you can choose to save it elsewhere.

Once all the desired data is copied, exit testdisk, run Gparted (from a live cd/usb, or install it with "sudo apt-get install gparted") and delete the partition table. Create a fresh (MSDOS) partition table from "Device" menu, then recreate a fresh Fat32 partition on it.

If having problem in any of the steps above, post back the error you get.

---

### Post by Wa_Si on 2013-10-18
Hi varunendra,
many thanks for replying.

You wrote
> Please use testdisk again to access the data through it
...thats currently my problem. I can't access the usb-device because I can't mount It. When I run testdisk, the harddisk is shown but not the USB-stick:
[ATTACH=CONFIG]247030[/ATTACH]


And same problem with **gparted**. I can't see the usb-drive. Only my harddisk is available.

So I think I'll have to mount the USB-stick first. In my first Post I've already described how I've tried to mount the USB-Stick.


Any ideas?

---

### Post by varunendra on 2013-10-18
Mounting is not necessary, but detection is. There is no point in using a 'partition recovery tool' if the partition is already 'mountable'.

By the way, your command to mount it was incorrect. You were trying to mount sdb, while it should have been sdb1 or sdb2 etc. That is - you mount a partition, not a device.

Did you try to format it on Windows? If the data on it is not too important for you, try formatting it as at least it is detected there.

It is also detected in Ubuntu as per the last two lines of your dmesg, but maybe there is some severe damage not allowing the system to communicate with it.

From the dmesg messages, it seems as if it is a memory card in a card reader. Maybe they have structured it the same way and now the 'storage area' (like a memory card) has disappeared from the reading module of the drive, probably indicating a possible physical corruption on it.

Check -
```
ls -l /dev/sd*
```
..before plugging it. Then plug it in, wait for about 10 seconds, then run the above command again. Are there any new entries? Which ones?

---

### Post by Wa_Si on 2013-10-19
Hi varunendra,

It would be really great if I could rescue some files from the USB-Stick,  but primary goal is to get it working again, even if it means to loose  all data on it. So...> Did you try to format it on Windows?
Yes I tried to, but windows installed a some drivers after plugging the stick in, but no volume was available. So I couldn't format it.

Here's the check you suggested:
**before** plugging it:
```

ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 Okt 19 06:15 /dev/sda
brw-rw---- 1 root disk 8,  1 Okt 19 06:15 /dev/sda1
brw-rw---- 1 root disk 8,  2 Okt 19 06:15 /dev/sda2
brw-rw---- 1 root disk 8,  3 Okt 19 06:15 /dev/sda3
brw-rw---- 1 root disk 8,  4 Okt 19 06:15 /dev/sda4
brw-rw---- 1 root disk 8,  5 Okt 19 06:15 /dev/sda5
brw-rw---- 1 root disk 8,  6 Okt 19 06:15 /dev/sda6
brw-rw---- 1 root disk 8, 32 Okt 19 06:15 /dev/sdc
brw-rw---- 1 root disk 8, 33 Okt 19 06:15 /dev/sdc1

```

and **after** plugging it:
```

brw-rw---- 1 root disk 8,  0 Okt 19 06:15 /dev/sda
brw-rw---- 1 root disk 8,  1 Okt 19 06:15 /dev/sda1
brw-rw---- 1 root disk 8,  2 Okt 19 06:15 /dev/sda2
brw-rw---- 1 root disk 8,  3 Okt 19 06:15 /dev/sda3
brw-rw---- 1 root disk 8,  4 Okt 19 06:15 /dev/sda4
brw-rw---- 1 root disk 8,  5 Okt 19 06:15 /dev/sda5
brw-rw---- 1 root disk 8,  6 Okt 19 06:15 /dev/sda6
**brw-rw---- 1 root disk 8, 16 Okt 19 06:35 /dev/sdb**
brw-rw---- 1 root disk 8, 32 Okt 19 06:15 /dev/sdc
brw-rw---- 1 root disk 8, 33 Okt 19 06:15 /dev/sdc1

```

**/dev/sdb** was detected.

---

### Post by varunendra on 2013-10-19
..but no /dev/sdb**1** :(

It is same as when I plug in my memory GSM modem with inbuilt memory card reader. Even with no card in it, I would see /dev/sdb, but of course can't do anything with it that can be done with a storage media.

Since both testdisk and gparted can't even *see* the disk (the storage area), I have very little hope that your USB is recoverable. You may try this -
```
sudo dd if=/dev/zero of=/dev/sdb
```
..which will only work if the problem is caused due to some corrupt bits in the storage area. It won't work if the corruption is physical and the storage is not accessible at all.

If the above command works, *everything* on your disk will be lost (data, partition) but the disk itself will be back and available for re-partitioning and usage.

**[COLOR="#FF0000"]Be Careful ![/COLOR]** Make ultra sure the /dev/sdb in indeed the usb disk you want to recover, not any other one. Because once the above command is executed, the data on the target disk will be irrecoverably lost.

**PS:**
If you are feeling super lucky, try this first -
```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```
This will only erase the first 512 bytes (MBR area) on the disk (if a 'disk' is detected first). So if the problem has occurred due to a bad MBR or partition table entry, this may fix it without removing the data. You can then recover the data using testdisk again.

---

### Post by Wa_Si on 2013-10-19
It doesn't work :(
The result of
```
sudo dd if=/dev/zero of=/dev/sdb
``` 

was "no medium found"
```

wasi@EasyNote-LS11HR:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: »/dev/sdb“ wird geöffnet: Kein Medium gefunden

```

Thats so annoying, because i followed the steps from here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step). Before i've done this, I was able to browse the direcories with testdisk. But now it seams to be completely damaged](*,)

---

### Post by varunendra on 2013-10-19
> **Wa_Si said:**
> Thats so annoying, because i followed the steps from here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step). Before i've done this, I was able to browse the direcories with testdisk. But now it seams to be completely damaged](*,)
Hmm.. bad luck :|

I have been using testdisk extensively and can trust my most important data/devices with it. I don't trust commercial products as much as I do testdisk. I believe it was either just a coincidence (it was going to corrupt anyway) or the device is very poorly designed (again, that would make it go wrong with 'any' tool, not just testdisk).

Most USB sticks have a "3 Year" or more warranty tag on them, and USB3 flash drives are rather new. So I think your stick should be under warranty. Have you checked that? Just replace it if it's still under warranty.

If it is out of warranty, try some other tools, search for similar cases/fixes on the forums and elsewhere etc. My limited knowledge and experience may not be the end of world. :)

---

### Post by Wa_Si on 2013-10-19
Yes, very bad luck. But many thanks for your time and your help. This forum is really a great help. 

I just wrote an e-mail to Verbatim. Unfortunately I don't kept the receipt from the store where I bought the USB-stick. Anyway... let's wait what for their reply. In the meantime I'll search for similar problems, as you suggested.

---

### Post by varunendra on 2013-10-19
No problem. And good luck with your further attempts. I'd really like to see if this can be solved using any method.

And if anyone reading this thread has anymore ideas, please jump in !

---

### Post by westie457 on 2013-10-19
Hi, badblocks works on a recognized device whether it is mounted or unmounted.
```
sudo badblocks -s
``` will give a time and number of blocks report in read-only mode.

see ```
man badblocks
``` for more details and options.

---

### Post by Wa_Si on 2013-10-19
Hi westie457,

**badblocks** doesn't help. Same problem: **no medium found**.

I tried **fsck.vfat**
```

fsck.vfat -v /dev/sdb
dosfsck 3.0.12 (29 Oct 2011)
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
**open: Permission denied**

```
:confused:

---

### Post by westie457 on 2013-10-19
Try running that command again using sudo.
The lack of sudo caused the Permission Denied error.

Hopefully you should get a useful response. Post the output anyway.

---

### Post by Wa_Si on 2013-10-20
Hi westie457,
> Try running that command again using sudo.
How could I forget this??? ;)
Here's the output
```

sudo fsck.vfat /dev/sdb
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
open: No medium found

```

Then I tried mkfs... same problem:
```
sudo mkfs.vfat /dev/sdb
mkfs.vfat 3.0.12 (29 Oct 2011)
/dev/sdb: No medium found

```
:cry:

---

### Post by westie457 on 2013-10-21
Hello Wa_Si

That USB stick has died. The MBR area is very badly damaged or part of the circuit-board has broken causing the 'No medium found' messages.

As varunendra has suggested try to get a replacement.

---

### Post by Wa_Si on 2013-10-21
To my surprise, I found the receipt for the USB-Stick. :p So I will surely get a new one.
Even if I didn't got my files rescued, I learned some new things.

Many thanks to you guys.

---

### Post by varunendra on 2013-10-22
> **Wa_Si said:**
> To my surprise, I found the receipt for the USB-Stick. :p So I will surely get a new one.

Congrats !! For the receipt, ..AND.. the 'lesson' - to keep 'em in future, until the warranty is expired. :P

I try to keep even the packing until warranty is expired (learned that from seagate warranty service). ;)

---

