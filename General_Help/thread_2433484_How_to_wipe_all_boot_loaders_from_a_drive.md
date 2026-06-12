---
title: "How to wipe all boot loaders from a drive?"
date: 2019-12-19
forum: General Help
---

### Post by meta-fox on 2019-12-19
Hi everyone! 

So to try and keep things as simple as possible, I want to totally wipe a drive (SSD, just in case it's relevant) entirely, including all boot loaders. My reason for this is I've been having problems with conflicting boot loaders for some time now ever since I tried out Ubuntu as my daily driver a while back. I won't pretend to fully understand exactly what boot loaders are, or why one will still be present even after formatting a drive, however what I do understand (I think) is that Ubuntu uses GRUB and Windows uses BOOTMGR? If I'm wrong however please let me know, I am interested to learn more. 

Anyway, I digress. After a recent issue wherein I couldn't boot into my Windows 10 installation (After POST all I had on screen was the 'Unkown Filesystem, entering GRUB rescue' message) I've decided to simply reinstall Windows to another drive that I have on hand and I'd like to totally wipe my usual boot drive completely, including the purging of all boot loaders, in the hopes that I can once again re-install Windows to that drive and finally be free of all problems. Before anyone asks, I didn't lose any data as I backup all my files regularly anyway, so this really isn't a huge issue for me, it's just a minor inconvenience. Ha ha. 

How would I go about totally wiping the drive? Would simply zeroing the drive achieve this, or will I need to delve a little deeper? 

Any help that you can offer me would be greatly appreciated! Thanks in advance!

---

### Post by yancek on 2019-12-19
Windows 10 when pre-installed will be an EFI system.  When you installed Ubuntu, did you install it in EFI mode?  Were you able to boot Ubuntu and did you boot windows from the Ubuntu Grub menu or did you need to boot to each by accessing the BIOS firmware and selecting either?  If you can't boot windows, can you boot Ubuntu?  On an EFI install, there is information in the BIOS firmware which is not on the hard drive/SSD.  Most computers will allow you to access an OS by entering the BIOS by using a specific key on boot which will give you boot options, in this case either windows or Ubuntu.  The key to use should show on screen for several seconds immediately after booting.  The key to use varies with manufacturer and you haven't indicated which you are using.

Did you read the Ubuntu documentation page on dual booting with windows 10, link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by meta-fox on 2019-12-19
I honestly couldn't tell you unfortunately, it's been so long since I was actually running Ubuntu now I can barely even remember the password I set to access it. Ha ha. 

All I'm looking for really now is a sure fire way to purge my drive and ensure that no boot loaders of any kind remain, essentially setting the drive back to a factory state, so that I can once again re-install Windows and have no conflicting boot loader errors in the future.

---

### Post by TheFu on 2019-12-19
```
$ sudo dd bs=4k count=2  /dev/null    /dev/sdZ
```

That will wipe the first 8KB on the sdZ disk from the beginning.  

You'll need to figure out which whole disk device is to be used. Pick the wrong one and nothing will work on any disk inside the computer.
Best to run this from any Linux installer in the "Try Ubuntu" mode.  The distro shouldn't matter, dd is on every Unix system.

If you get the wrong device, it can be terrible, bad, really bad.  So don't do that.

---

### Post by meta-fox on 2019-12-19
Brill, thanks Thefu. I'll have to try this out tomorrow now, but I'll be sure to post back once I've done so. I have a copy of Ubuntu knocking around somewhere, I'll chuck it on a pen drive.

Thanks for the warning about choosing the right disk, I'll be able to work that out I'm sure. 

So just to clarify, this process should eliminate all boot loaders from the drive in question?

---

### Post by TheFu on 2019-12-19
> **meta-fox said:**
> 
So just to clarify, this process should eliminate all boot loaders from the drive in question?

It will wipe the first 8K of any disk, which is where non-UEFI boot happens. It will wipe the 1st copy of the partition table for GPT disks and both copies for MSDOS disks.  Really 1K is overkill.

---

### Post by oldfred on 2019-12-19
Also if UEFI as yancek has mentioned are UEFI boot entries in the firmware.
From Ubuntu in UEFI boot mode this will show UEFI boot entries.
sudo efibootmgr -v

You can delete in UEFI or with efibootmgr.
sudo efibootmgr -b XXXX -B where XXXX is the hex number shown in the -v listing of an entry you want to delete.
See also:
man efibootmgr

---

