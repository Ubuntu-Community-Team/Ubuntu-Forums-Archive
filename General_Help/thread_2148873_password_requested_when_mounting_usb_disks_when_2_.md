---
title: "password requested when mounting usb disks when 2 users logged in"
date: 2013-05-27
forum: General Help
---

### Post by anoe on 2013-05-27
hi all. This is a problem i'm running into, i guess it's related to the new policy in ubuntu about mounting external usb's in /media/user instead of directly in /media. I am using lubuntu 12.10 64 bits.

The thing is, bassically, i've got one user, called normal-user. She belongs to plugdev group. When she is logged in by herself, she can plug and unplug her usb devices with no problem.

Now, we have another user, admin-user, with all admin privileges. The problem is, when both of them are logged in, if normal-user tries to plug in a usb device, a password window shows up in admin-user user desktop requesting for admin-user password. Even, when logging out from admin-user account, still the window shows up if normal-user tries to plug in any usb device, but this time in normal-user desktop.

As I said before, nothing of this happens if normal-user is the only user logged in.

any help appreciated.

tx.

---

### Post by sudodus on 2013-05-27
Will it make things easier if you (install and) run ***users-admin*** and give her user account custom settings and allow her to perform certain actions, for example to mount external media?

---

### Post by anoe on 2013-05-27
hi,

thanks for the answer. The thing is that she can already mount external media, she does does with no troubles. The problem is when she is logged in and an administrator is logged in too - then it is when we have this problem about administrative rights to mount and unmount her media.

I am talking about a single laptop shared at the same time between these two users.

tx.

---

### Post by sudodus on 2013-05-27
It works well have several users in an Ubuntu desktop system, but the system is not really made to work well with several users logged in and working at the same time. Is the problem that the administrator (you) are logged in remotely, and she is not prompted to mount the USB drive?

Have you given her permission to run sudo? In that case she should be able to run

```
 sudo mount -t auto /dev/sdxy /mnt
```

where x is the drive letter and y is the partition number, for example /dev/sdb1. You can prepare a few directories for her to mount on, if she would need more than one, for example subdirectories of /mnt or subdirectories of /media.

Are terminal commands an option? If not, we need to find some GUI application doing the same or something similar.

---

### Post by anoe on 2013-05-27
hi,

i don't want her to have permisions to run sudo. The problem, as you point out, is when both of us are logged at the same time in the same machine. If she is logged by herself, she has no problems to mount or umount (because of her belonging to the plugdev group, i guess).

it's not a big deal, though it's a bit a pain in the ass.

love

---

### Post by sudodus on 2013-05-27
I think it is also possible to allow sudo permission for a certain command.

Maybe this link will help you.

[https://www.linuxquestions.org/questions/linux-general-1/no-password-sudo-for-one-command-910711/](https://www.linuxquestions.org/questions/linux-general-1/no-password-sudo-for-one-command-910711/)

> Nevermind...I did some testing and found this works...
```
billybob ALL=(ALL) NOPASSWD: /bin/mount, PASSWD:ALL
```


---

