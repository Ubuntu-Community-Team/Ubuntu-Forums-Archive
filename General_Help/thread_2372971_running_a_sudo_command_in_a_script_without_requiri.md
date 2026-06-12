---
title: "running a sudo command in a script without requiring password"
date: 2017-10-01
forum: General Help
---

### Post by nebulous-plasma on 2017-10-01
Hi,

Linux newbie here.  I'd like the following script to run without requiring a password:
[I]
#!/bin/bash
grub-reboot 0
reboot[/I]

Because grub-reboot normally requires sudo privelege, I have added the line below to my sudoers file using visudo (just below the line *root  ALL=(ALL:ALL) ALL)*:

[I]USER_NAME HOST_NAME= NOPASSWD: /usr/sbin/grub-reboot 0
[/I]and I have also tried the line
*USER_NAME HOST_NAME= NOPASSWD: /usr/sbin/grub-reboot*

but no success...

I get the error below:

[I]/usr/bin/grub-editenv: error: cannot open /boot/grub/grubenv: permission denied
[/I]
It's my first ever script, but sadly doesn't work :( I've read quite a few forum posts here and elsewhere, but I can't figure out what I'm doing wrong.  Any suggestions would be appreciated!

Thanks :)

---

### Post by ian-weisser on 2017-10-01
After editing the sudoers file, did you logout/login to load the new settings?

---

### Post by untrustytahr on 2017-10-01
The NOPASSWD directive means you do not have to enter a password when invoking the sudo command... it does not relieve you from invoking sudo.  You never actually invoked sudo with anything.

---

### Post by again? on 2017-10-01
For your particular problem you can setup [SUID]("http://www.linuxnix.com/suid-set-suid-linuxunix/") of /usr/bin/grub-editenv
which will allow you to execute grub-reboot without using sudo.
```
sudo chmod u+s /usr/bin/grub-editenv
```

Also if you like to test different distros where the order of your grub menu may change it may be better to use the actual boot title
rather than a number.
This command will list your grub menu.
```
grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' -e "s/ {//g" | nl --starting-line-number=0
```
eg my output
```
glen@GU17:~$ grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' -e "s/ {//g" | nl --starting-line-number=0
     0	Ubuntu
     1	Ubuntu 16.04.3 LTS (16.04) (on /dev/sda1)
     **2	Fedora** 25 (Workstation Edition) (on /dev/sdb5)
     3	Ubuntu Artful Aardvark (development branch) (17.10) (on /dev/sdc1)
     4	Ubuntu Xenial 16.04.2 ISO
     5	Lubuntu 16.04.1 ISO
     6	Ubuntu Zesty 17.04 ISO
     7	Ubuntu-Gnome 17.04 ISO
     8	Ubuntu Artful 17.10 ISO
```
So to boot into **Fedora** I could use:
```
grub-reboot 2
```
or
```
grub-reboot 'Fedora 25 (Workstation Edition) (on /dev/sdb5)'
```

You can then use this info to create a reboot launcher.

---

