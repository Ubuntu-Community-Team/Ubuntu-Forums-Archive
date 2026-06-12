---
title: "Keep getting dumped into Busy Box/ Initramfs"
date: 2008-06-15
forum: General Help
---

### Post by KnavishClout on 2008-06-15
I can't boot into Ubuntu.  Every time I try I get dumped into Busy Box / initramfs.  I don't even know what that is.

Ubuntu was running fine, then I booted into my Windows Server 2008 partition once, and when I tried to boot back I was facing this problem.  The Windows partition still works, that's what I'm using now.

I'm really new to Ubuntu so if you need more info, please ask.  Also be very specific with any instructions because I don't know what a lot of things mean.

---

### Post by KnavishClout on 2008-06-15
This is mostly a bump, but I thought that it might be helpful to point out that the only thing that has changed at ALL in my system is that I pulled out my DVD-RW drive.

---

### Post by pointone on 2008-06-15
Right above the BusyBox prompt should be an error message describing exactly why the boot process failed. Please post the last few lines before the prompt to help us help you.

If you removed your DVD drive, chances are there's an entry in your fstab causing problems; but please post the error message to make sure.

---

### Post by KnavishClout on 2008-06-15
Apparently you were right.  During the time between my last post & now I decided to put the drive back in (I had only removed it to install XP on another PC that didn't have a DVD drive).  

In the future, how can I safely remove a drive?

---

