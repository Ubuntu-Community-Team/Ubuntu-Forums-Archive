---
title: "libparted warning for ssd hard drive"
date: 2012-11-14
forum: General Help
---

### Post by airworks on 2012-11-14
Hi,

I have a SSD hard drive that I think was totally dead. It would not show up in bios, and the hard drive would not be detected by any OS as well as any disk utility programs. Whenever the PC starts up it also takes extra long to start up, I assume it tries to read the drive, but can't and gives up in a couple minutes. It previously had Windows 7 on it.

Today I was trying the ubuntu live CD, and ran gparted partition editor and I got a libparted warning:
> Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?What happens if I answer wrongly? Should I be answering yes or no?
Does this mean there is a chance that this hard drive is still working? I would like to try to recover the data from it if at all possible.

Thanks.

Edit:
Oops, /dev/sda is the USB drive. Got worked up over nothing. :(

I wonder if there is a chance to recover data from this hard drive anyways? I should mention that also running sudo fdisk -l doesn't show the drive. Any programs I should try to see if I can recover data from? Although it probably is completely dead.

---

### Post by oldfred on 2012-11-14
Welcome to the forums.

gpt is often suggested for SSD and is required for drives over 2TB. Windows only boots from gpt drives with UEFI and if you install Windows in BIOS mode to previously gpt partitioned drive it converts to MBR(msdos). But it does not convert completely, gpt has a backup partition table and Windows ignores that. Linux tools see both MBR and gpt partition info and get confused.

If drive is really MBR.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by airworks on 2012-11-14
You probably posted before I made my edit. :P

Sadly the /dev/sda I mentioned was actually the USB I was running the live CD from. I can't even see my SSD hard drive as a device, running fdisk -l also does not show the drive. I think I am only left with expensive professional recovery options now?

---

### Post by oldfred on 2012-11-14
If BIOS does not see it, then no operating system or repair tool will see it.

You may want to double check connections, sometimes they get loose. (I always had to reopen case to push connections back in on something I did not change but bumped. :) )
And sometimes different SATA cable or power connection makes a difference. Worth trying.

---

### Post by airworks on 2012-11-14
> **oldfred said:**
> If BIOS does not see it, then no operating system or repair tool will see it.

You may want to double check connections, sometimes they get loose. (I always had to reopen case to push connections back in on something I did not change but bumped. :) )
And sometimes different SATA cable or power connection makes a difference. Worth trying.
Yea, I have tried that. Also tried attaching it to another computer, but no luck. I think I will leave it for now, but thanks for your assistance.

---

