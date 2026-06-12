---
title: "Big mistake with file manager caja cut instead of copy"
date: 2018-12-15
forum: General Help
---

### Post by jonnykickinbut on 2018-12-15
So I made a serious mistake doing something I  almost never do that is to use cut instead of copy while in Caja file  manager to transfer files to a flash storage device from the hard drive.

 Big oops, since somewhere during the transfer of the files over to flash drive  it stopped being able to write to the filesystem and showed in /etc/syslog with all sorts of nasty messages involving bad sectors and whatever on the USB flash storage device.  So now things seem pretty messed up since the filesystem is pretty much in the crappyiest of conditions (for the flash stick, which won’t mount).  I tried fsck there, but even if it were to mount I know that at least some of the files didn't make it over (because of the aborted operation during moving/renaming or whatever it is that cut/paste actually does in the Caja file manager I was working in).

So probably not expecting any quick  fix here and I guess it is a lesson about backup or redundant copies if I can't solve...not the biggest deal.

I was actually wondering though if maybe the Ubunut/Linux desktop  environment or the Mate provided Caja file manager may have temporarily stored these files or kept them in case the cut and paste operation failed the way it did just now.

I don't believe I stand a prayer at using recovery software to locate the files on the usb but I will try with whatever solution I already have installed for that...no need for any suggestions about file reovery tools thanks.

---

### Post by TheFu on 2018-12-15
As you know, flash storage dies all the time. So do SSDs. I've had both die, unexpectedly.  Never at a convenient time. The only fix is to have backups made at the frequency which prevents data loss you can't live without.  For me, that is 24 hrs. Many people decide that once a week or once a month is sufficient.

fsck on a flash drive probably isn't useful. Most flash drives are formatted to FAT32, so fsck won't help.  Use a Windows chkdsk to attempt any fix.  If you are using F2FS, the tools for that file system should include an fsck tool.

As for how Caja works, I don't know, but I do use it from time to time to move/copy files.  Using a move would entail multiple copy/delete tasks for each file.  It wouldn't be smart to pre-copy/cache the files anywhere else, so I'm 99.9999% certain caja doesn't do that.  I would be very surprised if any files not marked as successfully copied to the flash drive were deleted from the source drive. If caja didn't get told buy the flash drive that the data was written successfully, then it wouldn't delete the source.

Whether you can get data off the flash drive or not is unknown.  I would use ddrescue to clone the entire storage device, then make all attempts to recover files using a copy of that image.  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Any changes to the file system that held the source files - ANY WRITE - could be over writing the disk locations where the data is stored.  Installing tools included.  Really the best answer would have been to never touch the source disk again and to only use it in a read-only mount from an alternate OS boot, probably a different flash storage.  When/if you attempt any data recovery on the source disk, you'll see that you'll be returned thousands of files, most completely uninteresting, with names like file0001.dat, file0002.dat .... file9999.dat ... 

Restoring from backups is much easier.  Time to setup automatic, daily, versioned, backups.

And just so you know, you aren't the first person to lose data.  I lost 80% of my data in the early 2000s before I got backup religion. One disk failed in a 3 disk LVM stripe.

---

### Post by HermanAB on 2018-12-15
On the theme of backups, I use a Raspberry Pi as a backup file server and stuck it into the wall box together with the home fibre modem and wifi router.  It doesn't come any cheaper than that, so there is really no excuse not to make backups.

---

### Post by TheFu on 2018-12-15
> **HermanAB said:**
> On the theme of backups, I use a Raspberry Pi as a backup file server and stuck it into the wall box together with the home fibre modem and wifi router.  It doesn't come any cheaper than that, so there is really no excuse not to make backups.

Herman - Saw a $50 SBC this week with true USB3 and GigE networking. You might want to upgrade.
[https://www.phoronix.com/scan.php?page=article&item=odroid-xu4-arm&num=1](https://www.phoronix.com/scan.php?page=article&item=odroid-xu4-arm&num=1)  R-pis are great for certain purposes, but anything where I/O is the main goal, the Pi hardware is lacking.

---

### Post by jonnykickinbut on 2018-12-15
Hey I really appreciate the detail @TheFu and what a nightmare for you back in 2000 that really sounds bad.

For one most of these lost files are already backed up somewhere so I think the data loss is  relative not too bad.

But this is definitely a good learning point regarding hard drives so I will be sure to only invest in good ones from now on and keep to the old adage about backing up files daily like you said and maybe swapping the drives from time to time too.

Also in terms of the recovering from the system that had the file manager (caja) that was doing copy/move command from there to USB it is still an area of confusion for me, as I really can't make a good guess not seeing any files that remain from the aborted or failed move/copy to the usb as a result of the flash storage drive errirs. One other thing the USB drive is now inaccessible (linux or udev can't even make sense of the darn thing) so I guess that it is pretty much done!  I can't even get the device partitions to show up or access it via /dev without a error about no medium found.

So I will probably just move on with the daily backup schedule just as soon as possible. 

 And maybe avoid flash drives for anything other than transporting the file conveniently from now on.

Thank you everyone for your suggestions!

---

