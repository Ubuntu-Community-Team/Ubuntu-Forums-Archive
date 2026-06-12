---
title: "&quot;Warning: no final new line at the end of /etc/fstab/?"
date: 2007-04-21
forum: General Help
---

### Post by randell6564 on 2007-04-21
Hey folks!
I googled this subject but nothing seems to relate to my issue.
Every time that I boot, I get this error:
> *Mounting file system
                 [mntnt]: Warning, no new line at the end of /etc/fstab
I dual boot Windows XP and Feisty Fawn, but have no problem accessing my NTFS drive from Ubuntu, so I'm just wondering what this could mean, and how I might fix it.

Here is my /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=6a316831-0b44-4f7b-bf21-af209f470762 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=dda8cf20-1a75-4f1f-ac0b-6a13f65a0e02 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=B410740B1073D2BA /media/windows ntfs user,fmask=0111,dmask=0000 0 0
Thanks!

---

### Post by raja on 2007-04-21
Open /etc/fstab with a text editor (with admin priveleges) and press enter after the last line. Now you should see a blank line at the end. You should not see any more messages about the missing newline.

---

### Post by randell6564 on 2007-04-21
> **raja said:**
> Open /etc/fstab with a text editor (with admin priveleges) and press enter after the last line. Now you should see a blank line at the end. You should not see any more messages about the missing newline.
Thank You raja!  That worked!  Never expected it to be that simple. DUH:) 

Thanks again!

---

