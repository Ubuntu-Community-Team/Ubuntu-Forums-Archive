---
title: "Help Mounting Kindle Keyboard"
date: 2013-07-14
forum: General Help
---

### Post by nate_d099 on 2013-07-14
Ok, so I'll fill brief you wizards on what has happened so far.
In my searches for the Kindle Keyboard mounting, I have been stunted in different instructions.


**[SIZE=3]#1[/SIZE]** Sudo fdisk -l does not show my kindle as far as I know...

```
 Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c676e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       29865   239780864    7  HPFS/NTFS
/dev/sda3           29865       31131    10173441    5  Extended
/dev/sda5           29865       31131    10173440   82  Linux swap / Solaris

Disk /dev/sdb: 31.2 GB, 31221153792 bytes
128 heads, 63 sectors/track, 7561 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2088        7561    22071168    c  W95 FAT32 (LBA)
/dev/sdb2               1        2087     8413185    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sdb5               1        2087     8413184   83  Linux
```

Those are the results of such.

[SIZE=3]**#2**[/SIZE]
the "quickfix" ive heard of by using 
sudo apt-get install mtpfs

does not auto-mount or entice my computer into reading the kindle.

watch -n 1 "dmesg | tail"

produces this....

```
 [ 1213.900358] usb 2-1.1: device descriptor read/64, error -32
[ 1214.075294] usb 2-1.1: device descriptor read/64, error -32
[ 1214.251742] usb 2-1.1: new full speed USB device using ehci_hcd and address 6
0
[ 1214.322863] usb 2-1.1: device descriptor read/64, error -32
[ 1214.498400] usb 2-1.1: device descriptor read/64, error -32
[ 1214.674266] usb 2-1.1: new full speed USB device using ehci_hcd and address 6
1
[ 1215.081317] usb 2-1.1: device not accepting address 61, error -32
[ 1215.153437] usb 2-1.1: new full speed USB device using ehci_hcd and address 6
2
[ 1215.560515] usb 2-1.1: device not accepting address 62, error -32
[ 1215.560809] hub 2-1:1.0: unable to enumerate USB device on port 1


```

Any and all help would be greatly appreciated. I just want to put my Harry Potter books on my kindle! 
Thanks!

---

### Post by oldos2er on 2013-07-14
Moved to General Help.

What version of Ubuntu are you running?

---

### Post by nate_d099 on 2013-07-14
My bad, Im on Lucid, 10.04 LTS

---

### Post by oldos2er on 2013-07-14
Maybe it's time to upgrade, since 10.04 is EOL. I've used a Kindle 3G with Ubuntu versions 11.10 and later, they all have automounted it with no problem.

Edit: Of course I can't guarantee upgrading will solve your Kindle problem.

---

### Post by leopoldbirkholm on 2013-07-14
At OP, what is your computer like? Maker, model? RAM, CPU? Why I ask is to see if your computer can handle the upgrade.

---

### Post by nate_d099 on 2013-07-14
Dell Latitude E6410 i5 cpu w/ 2 GB RAM. I know it can handle the upgrade, but what repositories must I add and what command line executes the update?

---

### Post by oldos2er on 2013-07-14
[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by nate_d099 on 2013-07-14
I apologize, i know how to update to 12.04 as your link instructs. I prefer gnome and would like to know how to update to 11.10 or a suitable series of commands/downloads to mount my kindle if someone could help me. Thanks

---

### Post by oldos2er on 2013-07-15
11.10 is also no longer supported. You could always upgrade to 12.04 and install gnome-shell or any other DE you might prefer.

---

### Post by leopoldbirkholm on 2013-07-16
I would agree with oldos2er. Backup your data, download the 12.04 LTS, install the 12.04 LTS and then install the Gnome interface. You get a ton of benefit for maybe two hours work. I highly recommend it.

---

### Post by leopoldbirkholm on 2013-07-16
I was reading on a problem I am having with my TrekStor e-reader and I was wondering what the command ```
lsusb
```give you when you have your Kindle attached via cable to your Dell? :)

---

