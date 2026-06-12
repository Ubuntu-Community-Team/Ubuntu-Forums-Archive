---
title: "help, I cannot burn CD's!"
date: 2005-03-26
forum: General Help
---

### Post by pieter hollenberg on 2005-03-26
I am trying to burn a simple CD with nautilus, but it doensn't work

hoary recognized my plextor cd burner .

but it doesn't want to burn on a new blank cd
it doensn't erase a cd-rw either

it keeps saying " put a blank cd in" 

i cannot find another cd burn front-end

is there a problem with nautilus-burning ?

and why isn't there a decent CD burn front end application like K3b ????

e.g in the windows world there are several cd burn front ends !!!

asus cubx
P3 733
plextor px-W8432

---

### Post by soul_rebel on 2005-03-28
have you tried as root?

---

### Post by ubuntu_demon on 2005-03-28
[QUOTE=pieter hollenberg]I am trying to burn a simple CD with nautilus, but it doensn't work

hoary recognized my plextor cd burner .

but it doesn't want to burn on a new blank cd
it doensn't erase a cd-rw either

it keeps saying " put a blank cd in" 

i cannot find another cd burn front-end

is there a problem with nautilus-burning ?

and why isn't there a decent CD burn front end application like K3b ????

e.g in the windows world there are several cd burn front ends !!!

asus cubx
P3 733
plextor px-W8432[/QUOTE]
 sudo apt-get install k3b

or add this line to your /etc/apt/sources.list:

deb [http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/](http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/) ./

and do :

sudo apt-get install gnomebaker

k3b and gnomebaker are nice burnprograms. you can also try nerolinux..... If you've bought nero you can just go to the site.

---

### Post by wfx on 2005-03-28
burning is a bit broken (the burning tools are not realy like kernel >2.4)

How i do:
add to the file "/boot/grub/menu.lst" :
kernel          /vmlinuz-2.6.10-5-386 root=/dev/hda3 ro **hdd=ide-scsi** quiet splash
Change **hdd** to youre device!

add to the file "/etc/modules"
sg
ide-scsi

reboot (yes)
do a "cat /proc/scsi/scsi" it show you something like this:
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: _NEC     Model: DVD_RW ND-1300A  Rev: 1.05
  Type:   CD-ROM                           ANSI SCSI revision: 02

Ok the new device is sr0 (scsi**0**)
in "/etc/fstab" have you a device named "/dev/hdd ..." change it to:
/dev/sr0 ...

Now i think you can burn.

---

### Post by pieter hollenberg on 2005-03-29
thanx guys

gnomebaker did the job !!

---

