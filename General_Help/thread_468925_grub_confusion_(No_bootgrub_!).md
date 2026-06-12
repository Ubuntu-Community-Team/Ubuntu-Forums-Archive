---
title: "grub confusion (No /boot/grub !)"
date: 2007-06-09
forum: General Help
---

### Post by lbloy on 2007-06-09
So i have been unable to upgrade to the new kerenel because the configuration script would fail at update-grub.  Apparently /boot/grub doesn't exist. "locate menu.1st" just returns some examples files.

I'm using grub as my boot loader and its working fine. I'm just curious what might have happened to my grub configuration files? is there a way to get a working grub configuration based off what is on my MBR? What might have removed these files? The only 3rd party software that I'm running is Vmware workstation 6, might that have removed these files if so why?

-Luke

---

### Post by tpg on 2007-06-09
Can you cd into /boot and/or /boot/grub and do an ls?

By the way, I assume you searched for menu.**l**st not menu.**1**st (i.e. a small L, not a number 1). :)

---

### Post by lbloy on 2007-06-09
Thanks for your reply.
so /boot/grub isn't  there.

any idea what might have removed it?

funcsol@funcsol-laptop:~$ ls /boot/ -lrta
total 9816
-rw-r--r--  1 root root   83217 2007-06-07 14:16 config-2.6.20-16-generic
-rw-r--r--  1 root root 1746636 2007-06-07 16:58 vmlinuz-2.6.20-16-generic
-rw-r--r--  1 root root  414274 2007-06-07 16:58 abi-2.6.20-16-generic
-rw-r--r--  1 root root  806992 2007-06-07 17:00 System.map-2.6.20-16-generic
drwxr-xr-x  2 root root    4096 2007-06-09 10:15 .
-rw-r--r--  1 root root 6947396 2007-06-09 11:35 initrd.img-2.6.20-16-generic
drwxr-xr-x 21 root root    4096 2007-06-09 11:35 ..

funcsol@funcsol-laptop:~$ locate menu.lst
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_displaysplashimagegrub
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_changegrubpasswordforgotten
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_addwindowsentrygrubmenu
/usr/share/doc/grub/examples/menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst

---

