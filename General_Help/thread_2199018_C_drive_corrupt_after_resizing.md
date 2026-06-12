---
title: "C: drive corrupt after resizing?"
date: 2014-01-11
forum: General Help
---

### Post by wzissel on 2014-01-11
EDIT: Thanks for all your help, it was really appreciated! Although I didn't fix Windows, I was able to copy the very few files I'd like to save from Win 7 to Ubuntu, and will probably start using Ubuntu as my main OS (I really like it!). Thanks again!
Yesterday I shrank the largest partition of my hard drive in order to make room for Ubuntu. Everything turned out well... for Ubuntu. Now sda2 has an error beside it in gparted (see screenshot) and when I try to boot windows instead of Ubuntu from sda1 it returns me to the boot menu screen of Ubuntu. If I try to boot windows from sda2 it tells me to insert a Win7 installation disk for repair (which I do not have since it came preinstalled). I don't really have any important information on this partition (it's all either in Google Drive, or backed up in usbs)... but I would like to use windows from time to time.
I am wondering if there is any way to fix sda2 without an installation disk? I cannot interact with the partition at all as all it gives me is errors, unless I try booting windows from it (then it gives me the "Insert Installation Disk" screen).
Screenshot of error via gparted:
[ATTACH=CONFIG]249387[/ATTACH]
Additional error when in file browser (my C: drive displays as 147GB volume now...):
[ATTACH=CONFIG]249388[/ATTACH]

---

### Post by QIII on 2014-01-11
Hello!

Did you resize the Windows partitition using the Windows partition tools, or from gparted?

---

### Post by wzissel on 2014-01-11
I used gparted

---

### Post by QIII on 2014-01-11
Best to use the Windows partition tools to shrink Windows partitions.  It makes sure things are where Windows expects them to be in the end.

gparted should have something to warn people about that, I think.  Oh, well.

I take it you don't have a Windows installation disk?  Using Windows tools would be the best course of action, particularly if you need chkdisk.

If not, you might have a look [here]("https://help.ubuntu.com/community/Boot-Repair") for a tool that might help you.

---

### Post by wzissel on 2014-01-11
> **QIII said:**
> Best to use the Windows partition tools to shrink Windows partitions.  It makes sure things are where Windows expects them to be in the end.

gparted should have something to warn people about that, I think.  Oh, well.

I take it you don't have a Windows installation disk?  Using Windows tools would be the best course of action, particularly if you need chkdisk.

If not, you might have a look [here]("https://help.ubuntu.com/community/Boot-Repair") for a tool that might help you.

Where could I find/use windows tools in order to preform the suggested course of action within the error message?
I just used Boot Repair and attempted to boot windows same problem. I did pick up the window's reason why it will no longer boot off of sda2: the partition is inaccessible. Boot repair pastebin: [http://paste.ubuntu.com/6735339/](http://paste.ubuntu.com/6735339/)

---

### Post by Mark Phelps on 2014-01-11
IF you're willing to spend a little money, and have access to a working PC with a CD burner, you can download an ISO of the Win7 Repair CD from the following link -- and use that to do repairs:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by wzissel on 2014-01-12
I tried to repair Windows after reading this comment. It was working and said the disk had been repaired but I still get the same issue when trying to boot on both sda1 and sda2. The funny thing is I can now see what is inside sda2... why won't my Windows boot now!? TL; DR: The repair worked, and I can see what is inside the partition file wise... but Windows still won't boot while giving me the same error ("The Drive is Inaccessible") but I know it is accessible!!!

Some pictures/references:
New gparted screenshot.
[ATTACH=CONFIG]249454[/ATTACH]
New Boot-Repair url:
[http://paste.ubuntu.com/6742327/](http://paste.ubuntu.com/6742327/)

---

