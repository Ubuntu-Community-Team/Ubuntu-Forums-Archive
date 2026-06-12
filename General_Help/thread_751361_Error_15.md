---
title: "Error 15"
date: 2008-04-10
forum: General Help
---

### Post by arystrom on 2008-04-10
I get the following error. Installing from Windows, Rebooted, Waited for the installation to finish, it rebooted, then I selected ubuntu and got the following error. 

Any help would be appreciated. 

```

booting 'ubuntu hardy (development branch), kernel 2.6.24-12-generic'

file system type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24012-generic root=UUID=7C50B67F50B63FA6 loop=ubuntu

Error 15: file not found
any key to continue...

```

---

### Post by ago on 2008-04-10
Do you have more than 1 hard disk? If so see: [https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1](https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1)

---

### Post by arystrom on 2008-04-10
Hrm. This machine is a Gateway business machine, and has some funky stuff going on with a D backup drive. I'll check the post you sent and see if this is the source of the problem. It sounds like it's pointing to that second partition for ubuntu and should be going somewhere else.

---

### Post by you.buntu on 2008-04-11
I had the same error... best way to get rid of it... either burn ISO image onto a CD or use a virtual drive n mount the ISO... 

run wubi from the CD rather than the file from the wubi site

---

### Post by ago on 2008-04-11
Hmmm there should be no difference between wubi on the site and the one on the CD (other than for occasional version mismatch due to different update frequency).

I am really surprised that one of the 2 addresses the issue and the other does not. Are you sure? Can you compare the relevant menu.lst files in the 2 cases?

---

### Post by ago on 2008-04-11
In fact can you pls compare all the content of C:\ubuntu\install\boot (if the error happens after first reboot from windows) or C:\ubuntu\disks\boot (if the error happens after second reboot)

---

### Post by garferi on 2008-04-14
Hi!

I get this after the first reboot:
```
find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
Error 15: File not found
Press any key to continue...
```
In this computer there are 2 hard drives:
The first have 2 partition: C: Windows, E: Data
The second  is an unused 80 GB hard disk, has letter D:.
I tried many ways (mounted iso, CD, downloaded Wubi-8.04-beta-rev487sh.exe) to install it on disk D:, but I always get this error.
I tested install it on the  disk E:, and it was successful, but I would like to install ubuntu on the  drive D:, because it has 80 GB free space.
I attached the log file.
Thanks!

---

### Post by ago on 2008-04-14
see 

[https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1](https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1)

---

### Post by garferi on 2008-04-14
> **ago said:**
> see 

[https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1](https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1)
Thanks, but I read it already yesterday and didn't help.
1. I installed it on D: drive, not on C:
2. I havent got D:\ubuntu\disks\boot\grub\menu.lst, just D:\ubuntu\install\boot\grub\menu.lst

Thaks for any help!

---

### Post by ago on 2008-04-14
That might be grub4dos not able to "see" your drive
Press insert immediately after choosing ubuntu at boot

also in the grub console use tab expansion to navigate and see if you can browse your disk. E.G. "configfile (hd1,0)/ubuntu/boot/[TAB]" 
where 1,0 denote disk 2 partition 1 (change as appropriate)

also see [http://ubuntuforums.org/showpost.php?p=4676703&postcount=32](http://ubuntuforums.org/showpost.php?p=4676703&postcount=32)

---

### Post by bean123 on 2008-04-15
you can type:

cat (hd

then [TAB] (don't press <enter>), this will show all recognized hard disks. Then,

cat (hd0,

then [TAB], this will show all the partitions in (hd0)

---

### Post by ago on 2008-04-15
Did any of you use the ALTERNATE ISO with Wubi 8.04 by any chance? That would result in an unbootable installation (no vmlinuz/initrd), 8.04 requires the DESKTOP ISO. The problem will be addressed once md5 checks are activated.

PS thanks a lot Bean123 for coming to help (again)!

---

### Post by garferi on 2008-04-16
I will try the tips, thanks!

---

### Post by ago on 2008-04-16
See also [https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

