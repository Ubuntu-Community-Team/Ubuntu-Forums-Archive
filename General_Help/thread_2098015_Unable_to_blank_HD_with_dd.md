---
title: "Unable to blank HD with dd"
date: 2012-12-25
forum: General Help
---

### Post by satimis on 2012-12-25
Hi all.

Running Ubuntu 12.04 on USB

# dd if=/dev/zero of=/dev/sda```

dd: writing to `/dev/sda': Input/output error
281+0 records in
280+0 records out
143360 bytes (143 kB) copied, 77.3732 s, 1.9 kB/s

```

# dd if=/dev/zero of=/dev/sda bs=512```

dd: writing `/dev/sda': Input/output error
281+0 records in
280+0 records out
143360 bytes (143 kB) copied, 26.7369 s, 5.4 kB/s
281+0 records in
280+0 records out
143360 bytes (143 kB) copied, 26.737 s, 5.4 kB/s

```

Is the HD corrupted?  Please help

TIA

B.R.
satimis

---

### Post by cptrohn on 2012-12-25
Try DBAN,

It's available in sourceforge.

---

### Post by satimis on 2012-12-25
> **cptrohn said:**
> Try DBAN,

It's available in sourceforge.
Hi,

Thanks for your advice.

I'm running Live Ubuntun on USB.  I can't find dban on repository.

B.R.
satimis

---

### Post by irv on 2012-12-25
Run gparted. It is available from the live OS off the USB. You can do what every you want with the HD.
My questing is, do you plan on installing Ubuntu to your HD? If so, just let the install format the HD and it will wipe the drive and install Ubuntu on the entire drive.

---

### Post by satimis on 2012-12-25
> **irv said:**
>  - snip -
My questing is, do you plan on installing Ubuntu to your HD? If so, just let the install format the HD and it will wipe the drive and install Ubuntu on the entire drive.
No.  Sorry

It is an old 160G Maxtor HD.  I'm prepared using it for storage purpose to be installed in an external enclousure.  I suspect it is corrupted.

I'm now also running Live Ubuntu USB formating another old 160G Maxtor HD with dd.

# dd if=/dev/zero of=/dev/sda bs=512
it is now working.

On another terminal;
# watch -n 10 killall -USR1 dd

Output:```

....
13667725824 bytes (14 GB) copied, 604.172 s, 22.6 MB/s
27143777+0 records in
27143777+0 records out
13897613824 bytes (14 GB) copied, 614.177 s, 22.6 MB/s
27598081+0 records in
27598081+0 records out
14130217472 bytes (14 GB) copied, 624.183 s, 22.6 MB/s
27995409+0 records in
27995409+0 records out
14333649408 bytes (14 GB) copied, 634.189 s, 22.6 MB/s
28441145+0 records in
28441145+0 records out
14561866240 bytes (15 GB) copied, 644.195 s, 22.6 MB/s
28889049+0 records in
28889049+0 records out
14791193088 bytes (15 GB) copied, 654.2 s, 22.6 MB/s

```

It is quite slow.

I'll run gparted to check the problematic HD later.

Thanks

B.R.
satimis

---

### Post by irv on 2012-12-25
OK, it's clear what you are trying to do.
When it comes to HD, if there are any bad sectors I just get rid of the HD because in the long run it will save a lot of headaches.

---

### Post by satimis on 2012-12-25
> **irv said:**
> OK, it's clear what you are trying to do.
When it comes to HD, if there are any bad sectors I just get rid of the HD because in the long run it will save a lot of headaches.

First I blanked this problematic HD while it was installed in an external enclosure running on a PC;
# dd if=/dev/zero of=/dev/sdb bs=512

It worked but at very slow speed. Then stopped the program with [Ctrl]+c. Mount the HD in a PC. Then;

Ran again;
# dd if=/dev/zero of=/dev/sdb bs=512
It can't work anymore.

---

### Post by dino99 on 2012-12-25
with gparted, reset the table first, then format it again.

---

### Post by satimis on 2012-12-25
> **dino99 said:**
> with gparted, reset the table first, then format it again.
Before reading your advice I performed following step;

Started Live Ubuntu 12.04 USB installing it on the problematic HD.  It worked without problem.  On reboot, it dropped to;
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built=in shell (sah)
Enter 'help' for a list of built-in commands

(initramfs)


Reboot and started Recovery Mode;
..........
sd 1:0:0:0 [sda] Add. Sense: Unrecovered read error - auto real locate failed
sd 1:0:0:0 [sde] CDN: Read(10) :28 00 00 00 01 18 00 00 08 00
end_request: I/O error, dev sda, sector 285
Buffer I/O error on devcice sda, logical block 35
ata2: EH complete

(hanging here)

It is very strange. Now I even can't boot Live Ubuntu 12.04 USB. It just hangs on Ubuntu screen.

Advice would be appreciated. TIA

B.R.
satimis

---

### Post by Kirk Schnable on 2012-12-25
I think the best advice anyone can give you is not to use this hard drive for anything important anymore. It sounds like it has some issues.

---

### Post by satimis on 2012-12-25
> **Kirk Schnable said:**
> I think the best advice anyone can give you is not to use this hard drive for anything important anymore. It sounds like it has some issues.
No, you're right.

I only use old HD for;
1) storing old data with it mounted on external enclosure
2) for testing purpose.  Recently I used old HD testing cloud because some of them need bare metal to run.

For this problematic HD I would only use it for testing purpose even if it can be recovered.

Thanks

satimis

---

### Post by Kirk Schnable on 2012-12-25
> **satimis said:**
> No, you're right.

I only use old HD for;
1) storing old data with it mounted on external enclosure
2) for testing purpose.  Recently I used old HD testing cloud because some of them need bare metal to run.

For this problematic HD I would only use it for testing purpose even if it can be recovered.

Thanks

satimis

At work, we are not authorized to spend the money to replace hard drives right now, so when a workstation becomes so corrupted it doesn't boot anymore, we DBAN the drive, reimage it with Linux, and put it back in circulation. Since we don't allow permanent storage of files on the workstations anyway, data loss isn't a huge concern. 

However, usually once a drive gets to the point where it's throwing I/O errors, it usually fails DBAN. But, you're welcome to try. 

[http://www.dban.org/download](http://www.dban.org/download)

Kirk

---

### Post by satimis on 2012-12-25
> **Kirk Schnable said:**
> At work, we are not authorized to spend the money to replace hard drives right now, so when a workstation becomes so corrupted it doesn't boot anymore, we DBAN the drive, reimage it with Linux, and put it back in circulation. Since we don't allow permanent storage of files on the workstations anyway, data loss isn't a huge concern. 

However, usually once a drive gets to the point where it's throwing I/O errors, it usually fails DBAN. But, you're welcome to try. 

[http://www.dban.org/download](http://www.dban.org/download)


Hi Kirk,

Thanks for your advice.  Can DBAN run on USB?  B'cos no CDROM on this PC.

I found following threads/article:
how do i make a DBAN in a bootable usb fladh drive?
[http://ubuntuforums.org/showthread.php?t=1701757](http://ubuntuforums.org/showthread.php?t=1701757)

How To Boot DBAN Off USB Drive To Wipe Out the Hard Drive
[http://www.windows7hacker.com/index.php/2011/09/how-to-boot-dban-off-usb-drive-to-wipe-out-the-hard-drive/](http://www.windows7hacker.com/index.php/2011/09/how-to-boot-dban-off-usb-drive-to-wipe-out-the-hard-drive/)

Using DBAN from USB 
[http://www.youtube.com/watch?v=76X8W-ykkac](http://www.youtube.com/watch?v=76X8W-ykkac)


I have 2 PCs running WD (black series) HD storing useful data plus an external enclouse.  So it is quite safe.

I have encountered HD problem on Seagate, Maxtor, Hitachi etc.  I'm happy with WD, black series, HD.  Up to now without problem after running 5 years.

If the price of SSD drops I'll replace all HD with SSD.  There is no moving part on SSD.

satimis

---

### Post by Kirk Schnable on 2012-12-25
> **satimis said:**
> Hi Kirk,

Thanks for your advice.  Can DBAN run on USB?  B'cos no CDROM on this PC.

I found following threads/article:
how do i make a DBAN in a bootable usb fladh drive?
[http://ubuntuforums.org/showthread.php?t=1701757](http://ubuntuforums.org/showthread.php?t=1701757)

How To Boot DBAN Off USB Drive To Wipe Out the Hard Drive
[http://www.windows7hacker.com/index.php/2011/09/how-to-boot-dban-off-usb-drive-to-wipe-out-the-hard-drive/](http://www.windows7hacker.com/index.php/2011/09/how-to-boot-dban-off-usb-drive-to-wipe-out-the-hard-drive/)

Using DBAN from USB 
[http://www.youtube.com/watch?v=76X8W-ykkac](http://www.youtube.com/watch?v=76X8W-ykkac)


I have 2 PCs running WD (black series) HD storing useful data plus an external enclouse.  So it is quite safe.

I have encountered HD problem on Seagate, Maxtor, Hitachi etc.  I'm happy with WD, black series, HD.  Up to now without problem after running 5 years.

If the price of SSD drops I'll replace all HD with SSD.  There is no moving part on SSD.

satimis

Sometimes I find myself astonished at how many people's problems could be solved by a simple external USB CD drive...

Here's a tutorial for creating a DBAN USB stick:
[http://www.trishtech.com/security/create_bootable_dban_usb_pen_drive.php](http://www.trishtech.com/security/create_bootable_dban_usb_pen_drive.php)

---

