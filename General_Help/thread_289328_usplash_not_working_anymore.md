---
title: "usplash not working anymore"
date: 2006-10-30
forum: General Help
---

### Post by JackDog on 2006-10-30
Doesnt really matter to me except the family believes the machine is frozen on boot because nothing gets displayed except a cursor in the upper left. I have seen some other posts regarding this however none have solved my problems. After reinstalling the usplash things look ok. But when I reconfigure the kernel, dpkg reports the splash missing. I have not attempted any custom usplash's, just the default. I have also tried specifying multiple fb modes, none have worked. Any ideas?

```
 root@Laptop:/etc/alternatives# sudo aptitude reinstall usplash-theme-ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following packages have been kept back:
  hpijs libggi2 mplayer python-adns python-clientcookie python-crypto 
  python-egenix-mxdatetime python-egenix-mxproxy python-egenix-mxstack 
  python-egenix-mxtexttools python-gadfly python-htmlgen python-htmltmpl 
  python-imaging python-imaging-sane python-jabber python-kjbuckets 
  python-ldap python-mysqldb python-pam python-pexpect python-pgsql 
  python-pylibacl python-pyopenssl python-pyxattr python-reportlab 
  python-simpletal python-soappy python-sqlite python-syck python-xmpp 
The following packages will be REINSTALLED:
  usplash-theme-ubuntu 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 31 not upgraded.
Need to get 0B/89.7kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 136161 files and directories currently installed.)
Preparing to replace usplash-theme-ubuntu 0.6 (using .../usplash-theme-ubuntu_0.6_i386.deb) ...
Unpacking replacement usplash-theme-ubuntu ...
Setting up usplash-theme-ubuntu (0.6) ...
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic

root@Laptop:/etc/alternatives# sudo dpkg-reconfigure linux-image-$(uname -r)
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


```

---

### Post by madonion87 on 2006-11-01
well for the default kernel my usplash works fine
except for the kernel i compiled which is 2.6.18.1 when i install it, it displays the same message as yours, so now i dont see a splash screen on boot too

---

### Post by centyx on 2006-11-20
I too, am experiencing the blinking cursor, since the upgrade to edgy.
I am also using linux-image-2.6.17-10-generic.

I've tried dpkg-reconfigure'ing linux-image-2.6.17-10-generic, usplash, and usplash-theme-ubuntu, w/ no success. I do not see the splash on bootup or shutdown. I do see the splash screen when I run 'usplash' from the command prompt. 

I have another edgy machine that I upgraded from Dapper that has the splash showing fine. I've tried to find differences in grub's menu.lst, usplash's usplash.conf, and package versions, and file permissions, but there aren't any. I'm really not sure why it's not working on the one machine.

Any suggestions greatly appreciated.

---

### Post by strabes on 2006-11-20
My edgy usplash image works fine on startup, but on shutdown I get these crazy combinations of colors that change every time. It's very wierd and disconcerting and it's only been happening on edgy.

---

