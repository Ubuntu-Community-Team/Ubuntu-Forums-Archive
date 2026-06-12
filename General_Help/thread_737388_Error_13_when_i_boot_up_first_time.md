---
title: "Error 13 when i boot up first time"
date: 2008-03-27
forum: General Help
---

### Post by daberger on 2008-03-27
i recently used wubi to install ubuntu on an old decrepit laptop to try and speed things up a bit. when i selected ubuntu as my os of choice for the day from the startup menu it gave me this message

Booting 'start installler in normal mode'

(hd0,0)
Filesystem type is ntfs, partition type 0x7
kernel /ubunutu/install/boot/vmlinuz boot=casper debian-installation=/ubuntu/install/custum-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso quiet splash ro automatic ubiquity locale=en_US.UTf-8 noprompt --

Error 13: Invalid or unsupported executable format

Press any Key to continue...




as an ubuntu noob i have no idea what this message means and i appreciate it if u more knowledgeable folks could help bcuz i am anxious to get it booted up for the first time

---

### Post by ago on 2008-03-27
can you pls compare the md5 of the files 

c:\ubuntu\install\boot\vmlinuz

and

\casper\vmlinuz within the ISO/CD?

---

### Post by daberger on 2008-03-28
how???

(im a newb :D)

---

### Post by bean123 on 2008-03-28
you can use cat command in grub console to dump the header information:

cat --hex --skip=0x1F0 --length=80  path_to_kernel_file

---

### Post by ago on 2008-03-28
Thanks bean123 for coming to the rescue ;)

For the others the relevant launchpad bug is [https://bugs.launchpad.net/wubi/+bug/202768](https://bugs.launchpad.net/wubi/+bug/202768)

---

### Post by daberger on 2008-03-28
thank you all i am now running ubuntu

---

### Post by ago on 2008-03-28
> **daberger said:**
> thank you all i am now running ubuntu

What did you do to address the issue?

---

### Post by daberger on 2008-03-28
reinstalled ubuntu

---

