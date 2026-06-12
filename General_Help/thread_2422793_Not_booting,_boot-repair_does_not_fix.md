---
title: "Not booting, boot-repair does not fix"
date: 2019-07-12
forum: General Help
---

### Post by str3r on 2019-07-12
Hi,

I have an Ideapad 120s-141ap with 18.04.2 on it which isn't booting. I've been trying to fix it based on various posts and suggestions since last night and at this point I'm worried I'm only breaking it more, so I wanted to ask for some help.


I think whatever is going on is related to an fstab issue I had before - after an update it wanted to boot from my HDD that just has data files on it. I deleted the HDD from fstab and it's been working fine for the past few months but I recently updated again and now it's broken again. There's no entry for the problem HDD in fstab so I'm not sure what's up. 


I can get into BIOS, then a Lenovo splash, then always GRUB and I have to select, then scrolling white on black cmd style text with each line tagged with [ok] or [failed] in green and red. Then I get grey boot screen with logo, and then it goes into a cmd style login page. when I log into that I get some error messages saying a bunch of stuff didn't work because the file system is read only.


I tried boot-repair, and it didn't work. Here's two logs, from before and after I ran it:

[http://paste.ubuntu.com/p/rQNjJdvQF2/](http://paste.ubuntu.com/p/rQNjJdvQF2/)
[http://paste.ubuntu.com/p/k6tjKxBZww/](http://paste.ubuntu.com/p/k6tjKxBZww/)

I can also see all my files from the live usb, although they are read only and I can't copy them. At this point I would also be fine with just copying them over and reinstalling budgie cleanly.

Thank You :KS

---

### Post by oldfred on 2019-07-12
Report does not show all the details on MMC type devices.
But I do not see printout of fstab at all? Did you not save it correctly?

If read only, you still can read your data & copy to another device.

But your sdb drive is NTFS, which does not support Linux style ownership & permissions. It may be ok to copy your own data, but not anything system related. With your data you can easily reset ownership & permissions to you. But system setting vary a lot and cannot be restored.

Looks like an UEFI system, but BIOS type install.
Is this one with 32 bit UEFI, but 64 bit system?
       LENOVO Ideapad 100S Laptop  32 bit UEFI bootia32.efi
[https://ubuntuforums.org/showthread.php?t=2350606](https://ubuntuforums.org/showthread.php?t=2350606)

---

