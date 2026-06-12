---
title: "Can't permanently save things on Ubuntu running off a flash drive"
date: 2012-12-05
forum: General Help
---

### Post by NoahWL1 on 2012-12-05
So I have an old, broken, Windows XP laptop, and I stuck my Ubuntu flash drive into it and it booted up perfectly when choosing "Boot from USB device" in the boot menu.  But the problem is, when I turn off the computer completely, (not just sleep mode or hibernate) EVERYTHING resets!  Like my desktop goes back to normal, all my installed programs go away, everything is just set back to default!  Do you know why this is happening?  As of now, I can't install Ubuntu on the old pre-installed Hard Drive (which still works fine, and I would like to)because I have all my old files still on it.  What can I do to keep all of my data when I turn off my computer without installing Ubuntu on my Hard Drive?  I don't have a problem using the free space on my old Hard Drive to store everything either, I just can't wipe it and install a whole new OS on it.  Thanks.

(If you are wondering what is wrong with my laptop (Windows side) is it blue screens every single time about 5 minutes after booting it up, unless I'm in safe mode, where I can't do any of the features I need to do).

---

### Post by Rebelli0us on 2012-12-05
Follow [this thread]("http://ubuntuforums.org/showthread.php?t=2090076"), you'll find the answer in there.

---

### Post by oldfred on 2012-12-05
How big is flash drive? You may just need to turn persistence on to allow it to store some data. Or convert to a full install where you can save everything but needs 8GB flash drive.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by jdmgwaka89 on 2012-12-05
You will have to install Ubuntu to run along side Windows in order to save things. When you try to save things without installing, the system cannot access the hard drive to save them to.

---

### Post by NoahWL1 on 2012-12-05
> **oldfred said:**
> How big is flash drive? You may just need to turn persistence on to allow it to store some data. Or convert to a full install where you can save everything but needs 8GB flash drive.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
It's just 1 gb.  I didn't want to use my 16gb.  Is there a way to set the paths of the Ubuntu Home folder to the Hard Drive somehow?

---

### Post by trogdor1138 on 2012-12-05
Yes, but you'll need to manually mount the appropriate partition each time you boot. I would recommend checking out the links provided above to set up a persistent install.

If you're just trying to make it by temporarily, and you're not aware of how to mount drives, check out the documentation for explanation and examples: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by C.S.Cameron on 2012-12-06
You can place a ext2, 3 or 4 partition on your hard drive named casper-rw and if you wish a separate home folder, an ext partition named home-rw.

These will take president over casper-rw files or partitions on the USB drive.

But what is the problem installing to the 16GB drive?

If you do a persistent install with 4GB "extra space", you will still have 11GB space to use for file transfers etc.
(When booting the pendrive you need to access filesystem/cdrom as root to see these files).

Or you can do a full install to the drive leaving up to 11GB FAT32 or NTFS in the first partition that can be accessed by Windows or Linux.

---

### Post by C.S.Cameron on 2012-12-07
If you are still interested and following this thread let me know and I will write you a step by step for placing a persistent partition on your hard drive for use when booting a flash drive.

---

