---
title: "First time booting - error, new user"
date: 2008-04-29
forum: General Help
---

### Post by jvittetoe on 2008-04-29
Hello,

I have just plugged up a second hard drive, formatted it and installed ubuntu 8.04 on it. After the installation I rebooted, I selected to boot up ububunu and it began to finish installing. After it finished, I rebooted again and then came the following error.

--------
Booting 'Ubuntu 8.04, kernal 2.6.24-16-generic'

Filesystem type is ntsf, partition type 0x7
kernal /boot/svmlinuz-2.6.24-16-generic root=UUID=9498289c98287ebc loop=/ubuntu/disks/root.disk ro quiet splash

Error 15: File not found

Press any key to continue
--------

pressing any key gives me three options to boot from, all of which bare the same message. is this an issue that i can resolve by reinstalling? or is my file system wrong? thanks.

---

### Post by jvittetoe on 2008-04-29
any idea? I have tried reinstalling but I get the same error.

---

### Post by jvittetoe on 2008-04-30
anybody?

---

### Post by lswest on 2008-04-30
what did you format the drive as?  it should be formatted as ext3.

---

### Post by strabes on 2008-04-30
Reinstalling GRUB should fix this problem. Follow the GRUB link in my signature.

---

### Post by jvittetoe on 2008-04-30
well, i cleared my 2nd hard drive and formatted it ntsf from windows' disk management tool. a buddy i work with told me today i should just leave it unformatted and ubuntu will format it itself during the install. i will try the GRUB fix later and let you know. thanks.

---

### Post by jvittetoe on 2008-04-30
> **strabes said:**
> Reinstalling GRUB should fix this problem. Follow the GRUB link in my signature.

okay, so i booted up ubuntu from the cd, i noticed a few I/O errors but it kept on going. i followed the direction on reinstalling grub, i got to this step,

find /boot/grub/stage1

and returned 'Error 15: File not found

which is the same error i got from when trying to install ubuntu normally. 

im lost now.

---

### Post by lswest on 2008-05-01
you must delete the ntfs partition you created from windows and format it as ext3 during the install of Ubuntu, Ubuntu can't run on an ntfs drive, which is why the files can't be found.

---

### Post by jvittetoe on 2008-05-01
that makes sense, but when will i tell the ubuntu installation that i want it to format and install on my other hard drive? i want to keep my 1st drive for windows and my seconds drive for ubuntu.

---

### Post by lswest on 2008-05-01
at the partitioning stage (i think it's something like step 5 of 7) you can choose "manual partitioning" and then choose the partition you made for Ubuntu (or the free space that used to be that partition) and create 1 partition as ext3 and set the mountpoint as "/" (without the quotes) and then another, smaller partition (probably about 1GB if you can spare it, not less than 512MB though) and format it as "swap" (choose it from the drop-down menu).  After that it should be fine.

If you're wondering:
- the swap partition is similar to Windows' virtual memory option, where it uses part of your hard drive as random access memory.

- the "/" is the designation for "root filesystem" (pretty much what "C:\" is in Windows)

---

