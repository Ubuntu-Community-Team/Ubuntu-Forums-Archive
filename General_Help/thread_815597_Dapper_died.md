---
title: "Dapper died"
date: 2008-06-01
forum: General Help
---

### Post by stevejeep on 2008-06-01
Problem with Dapper. Used the computer one month ago, was fine. Booted yesterday and it froze with "waiting for root file system... ..." About 10 minutes later this message popped up "Alert! /dev/hdc3 does not exist. Dropping to a shell! Busy box comes up next and this message "/bin/sh: can't access tty; job control turned off." One hard drive Maxtor 200gb, 3 partions 1=Windows 2000 pro, 2=ntfs data, 3=Ubuntu. Any ideas???? Web search shows allot of this failures, does Ubuntu have a "restore" or some repair method. I want to use this drive and am locked out. Remind anyone of "Windows?" Grub menu boots and Windows boots ok, connections checked about 4 dozen times, always the same W2k boots no Ubuntu. Booted with live cd and all partions show hda1, hda2 and hda3. Admin> disks> shows 2 more hds with no names and no information?

---

### Post by Joeb454 on 2008-06-01
Check the connections on all your drives.

And does Windows see the 3rd hard drive? (I assume that it's the 3rd, as it's called hd**c**)

---

### Post by stevejeep on 2008-06-02
[QUOTE=stevejeep;5095600]Problem with Dapper. Used the computer one month ago, was fine. Booted yesterday and it froze with "waiting for root file system... ..." About 10 minutes later this message popped up "Alert! /dev/hdc3 does not exist. Dropping to a shell! Busy box comes up next and this message "/bin/sh: can't access tty; job control turned off." One hard drive Maxtor 200gb, 3 partions 1=Windows 2000 pro, 2=ntfs data, 3=Ubuntu. Any ideas???? Web search shows allot of this failures, does Ubuntu have a "restore" or some repair method. I want to use this drive and am locked out. Remind anyone of "Windows?" Grub menu boots and Windows boots ok, connections checked about 4 dozen times, always the same W2k boots no Ubuntu. Booted with live cd and all partions show hda1, hda2 and hda3. Admin> disks> shows 2 more hds with no names and no information? Any help out there, I really want to access this disk, all email and business stuff.

---

### Post by ibuclaw on 2008-06-02
While in your LiveCD, mount the Ubuntu Partition and chroot to it.
```

sudo mount /dev/hda3 /mnt
sudo chroot /mnt

```

Backup, then edit the menu.lst file
```

cd /boot/grub
sudo cp menu.lst menu.lst.bak
sudo nano menu.lst

```

Press **Ctrl+W** followed by **Ctrl+R** and type in **hdc3** into the searchbox, and **hda3** (Or whatever the device name of the partition is) and Press "**A**" to replace all instances.

Then reboot.

Regards
Iain

---

### Post by stevejeep on 2008-06-02
> **stevejeep said:**
> [QUOTE=stevejeep;5095600]Problem with Dapper. Used the computer one month ago, was fine. Booted yesterday and it froze with "waiting for root file system... ..." About 10 minutes later this message popped up "Alert! /dev/hdc3 does not exist. Dropping to a shell! Busy box comes up next and this message "/bin/sh: can't access tty; job control turned off." One hard drive Maxtor 200gb, 3 partions 1=Windows 2000 pro, 2=ntfs data, 3=Ubuntu. Any ideas???? Web search shows allot of this failures, does Ubuntu have a "restore" or some repair method. I want to use this drive and am locked out. Remind anyone of "Windows?" Grub menu boots and Windows boots ok, connections checked about 4 dozen times, always the same W2k boots no Ubuntu. Booted with live cd and all partions show hda1, hda2 and hda3. Admin> disks> shows 2 more hds with no names and no information? Any help out there, I really want to access this disk, all email and business stuff. What I got so far and thanks!

ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# cd /boot/grub
root@ubuntu:/boot/grub# sudo cp menu.lst menu.lst.bak
sudo: unable to lookup ubuntu via gethostbyname()
root@ubuntu:/boot/grub# sudo nano menu.lst
sudo: unable to lookup ubuntu via gethostbyname()
root@ubuntu:/boot/grub#

---

### Post by stevejeep on 2008-06-02
> **stevejeep said:**
> [QUOTE=stevejeep;5100920] What I got so far and thanks!

ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# cd /boot/grub
root@ubuntu:/boot/grub# sudo cp menu.lst menu.lst.bak
sudo: unable to lookup ubuntu via gethostbyname()
root@ubuntu:/boot/grub# sudo nano menu.lst
sudo: unable to lookup ubuntu via gethostbyname()
root@ubuntu:/boot/grub#

says no menu.lst running on live CD

---

### Post by stevejeep on 2008-06-03
Problem solved. Thank you Tinivole

---

