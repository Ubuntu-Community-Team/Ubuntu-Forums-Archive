---
title: "[SOLVED] Changing grub splash image with update-grub"
date: 2008-03-27
forum: General Help
---

### Post by Jadd on 2008-03-27
These are the instructions I've followed in the past to change my grub splash image:
> The command update-grub will ausutomatically pick up /boot/grub/splash.xpm.gz and configure the menu.lst file for you. It will take care of the correct hdX and partition number [no need to type in (hd0,4)]. s
sudo apt-get install grub-splashimages 
sudo ln -s /boot/grub/splashimages/my_image.xpm.gz /boot/grub/splash.xpm.gz
sudo update-grub
This worked great in the past (can't remember if I tried it on Gutsy, but I definately did on Feisty). But now, sude update-grub refuses to find /boot/grub/splash.xpm.gz. Any ideas why? I'm currently running Gutsy.
This is what I get:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

---

### Post by dcstar on 2008-03-27
> **Jadd said:**
> These are the instructions I've followed in the past to change my grub splash image:

This worked great in the past (can't remember if I tried it on Gutsy, but I definately did on Feisty). But now, sude update-grub refuses to find /boot/grub/splash.xpm.gz. Any ideas why? I'm currently running Gutsy.
This is what I get:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

Do you also need to do:

```
sudo update-initramfs -u
```

---

### Post by Jadd on 2008-03-28
> **dcstar said:**
> Do you also need to do:

```
sudo update-initramfs -u
```
No, that didn't work.
You know, I'm beginning to think it's encfs' fault. When I run
sudo cat menu.lst
for instance, I get:
```
[sudo] password for user:
12:09:00 (main.cpp:642) Root directory: /home/user/.arwen/
12:09:00 (main.cpp:643) Fuse arguments: (daemon) (threaded) (timeout 1) (keyCheck) (useStdin) encfs /home/user/.evolution -s -o use_ino -o default_permissions -o allow_root,allow_root,nonempty 
12:09:00 (Interface.cpp:165) checking if ssl/aes(2:1:1) implements ssl/blowfish(2:1:1)
12:09:00 (Interface.cpp:165) checking if ssl/blowfish(2:1:1) implements ssl/blowfish(2:1:1)
12:09:00 (SSL_Cipher.cpp:322) allocated cipher ssl/blowfish, keySize 20, ivlength 8
12:09:00 (FileUtils.cpp:1307) useStdin: 1
12:09:00 (FileUtils.cpp:1318) configuration key size = 32
12:09:00 (FileUtils.cpp:1319) cipher key size = 32
12:09:00 (Interface.cpp:165) checking if nameio/block(3:0:1) implements nameio/block(3:0:1)
cat: menu.lst: No such file or directory
```
But when I try the same command again, I get the content of menu.lst, which is what cat is supposed to do.
Could someone try those instructions on Gutsy to verify that they're supposed to work.

---

### Post by Jadd on 2008-03-28
I just tried those instructions on a fresh install of Ubuntu Gutsy in a VirtualBox, and it worked, so I'm pretty sure it's encfs and pam-encfs' fault. So I've solved this problem, but not the other one. Thanks dcstar.

---

