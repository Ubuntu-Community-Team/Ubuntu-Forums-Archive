---
title: "Harddrive test tools?"
date: 2007-05-28
forum: General Help
---

### Post by BigCajun on 2007-05-28
Hi all,

I've recently got an issue with one of my Ubuntu machines. I'm trying to download one of the DVD ISO images to test out 64-bit (currently use 32-bit). The problem I have is that the ISO fails the md5sum check. I've tried multiple sites, it always fails.

For whatever reason, I ignored this and tried to burn the image to a DVD+RW. The burn seemed to go fine, and K3b even verified the contents with no errors. So I tried to boot the disc. It booted to the menu screen, so I did the "check disk" option to make sure the disc was fine, but sure enough, it reported errors.

So, I have a second machine running Ubuntu as well. I decided to try to download the ISO on it. This time, from one of the servers I already tried, the ISO image actually passes the md5sum check. But, I don't have a DVD burner on that machine. So I tried to sftp the image to the original machine.

Funny thing here is that once I sftp'ed the image over, the image now passes the md5sum check. So what's the deal? I would assume that, if the machine I'm having problems with has a bad/defective harddrive, that even the sftp of the image would still be bad. But it seems to be ok.

Are there any test tools out there to test the harddrive? It's a Western Digital SATA drive and I've tested it under Windows with the Western Digital tools and it doesn't report any problems.

Or do I have some kind of network card issue? But then again, I would imagine that would have the problem on an sftp transfer as well.

Any direction would be appreciated....

---

### Post by smoker on 2007-05-28
i use a bootable version of 'drive fitness test' to check hard drives:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

have you checked the file system with fsck? or chkdsk, if a windows partition?

---

### Post by BigCajun on 2007-05-28
So I have checked the disk with Windows chkdsk (when it was formatted NTFS) as well as fsck, neither reports problems. I'm not able to try the DFT program as I don't have a floppy drive in this machine. It's just weird that the ISO download is corrupt when I do it from this machine (the one I'm on) but it works fine when I download it on my other machine.

Any other suggestions?

I've run Memtest86 on my system and that passes fine as well. Not sure what the deal is.

---

