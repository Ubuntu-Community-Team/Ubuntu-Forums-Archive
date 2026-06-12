---
title: "[SOLVED] Dual-boot: cannot access Windows disk or data partition - permission denied"
date: 2007-12-21
forum: General Help
---

### Post by twin_57103 on 2007-12-21
I have an established dual-boot system that has suddenly started giving me trouble accessing my NTFS partitions from Ubuntu.

I have two hard drives, both SATA.  Windows XP is on an 80 Gb drive, and the second has two partitions: an NTFS data partition and Ubuntu, which was a default install of 7.04, then upgraded to 7.10 without incident.  I have NTFS read-write support installed.

I've been using Windows a lot recently, but booted into Ubuntu tonight, only to find that I can't even see the data partition or Windows drives from nautilus, and when I try to access them from the terminal (from \media) I get permission denied messages.  
karin@karin-desktop:/media$ cd Windows
bash: cd: Windows: Permission denied

Nothing has changed that I'm aware of - my drives are just missing from Ubuntu.  I could see the data partition from Windows, so I know the files are still there.  I've tried rebooting, which hasn't made a difference.  This has worked in the past and I'm not sure what's changed.

I'd appreciate any suggestions you could give.  Thanks & Merry Christmas!

---

### Post by jpkotta on 2007-12-21
Is it a permissions issue?  Does it work when you're root?
```
sudo -i
cd /media/Windows
ls
...
exit
```

Or maybe it's not even mounted?  Try running mount and see if you can recognize the partition (it should say ntfs for the filesystem).
```
mount
```

---

### Post by twin_57103 on 2007-12-21
Well, I guess there's a good argument for sleeping on your computer problems.  I booted to Ubuntu this morning to see if your suggestions would help, and somehow it had self-corrected overnight.  Go figure.  Thanks for the help!

---

