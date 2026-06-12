---
title: "Resize boot partition with LVM"
date: 2013-09-05
forum: General Help
---

### Post by SASDOE2 on 2013-09-05
Hi all, 

I am trying to resize my /boot partition because it is almost full, and is causing errors when running apt-get upgrade.

To put into context: I have two 1TB drives installed. One of them (sda) has 250 MB for an ext2 /boot partition (now almost full), and a LVM taking up the rest of the disk space, and spreading well into the other hard drive (sdb).

When I try and resize the /boot partition using a live CD and gparted, I cannot do anything since there is no space left on the physical drive. 

I was hoping someone could tell me how to move LVM data from sda to sdb (there isn't enough to move all of it).

Or if anyone else has another idea I am keen to hear it!

Thanks!

---

### Post by bluefrog on 2013-09-05
get rid of unwanted kernels. simplest way
reduce the LVM physical volumes. not difficult [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)

---

### Post by SASDOE2 on 2013-09-05
Can't get rid of unwanted kernels because of bugs related to /boot partition full (i think, errors are lock file in use, but fuser returns nothing)

---

### Post by bluefrog on 2013-09-05
post the error u are getting when apt-get upgrading

---

### Post by SASDOE2 on 2013-09-05
[http://pastebin.com/3XKEY0e1](http://pastebin.com/3XKEY0e1)

apt-get -f install (as prompted to by previous error) returns these errors ([http://pastebin.com/kGbSfrzR](http://pastebin.com/kGbSfrzR)), doing sudo apt-get autoremove returns same error as apt-get upgrade.

---

### Post by bluefrog on 2013-09-05
how many vmlinuz in ur boot partition?. get rid of the old ones. old initrd as well.

that will free up some space.

---

### Post by SASDOE2 on 2013-09-05
I have 11 vmlinuz in the boot folder. Sort of new to fidling around with this and I really don't want to break anything here, could you tell me what ones to delete ? As well as the initrd files. 

```

[ maxime @ neo /boot]
$ l
abi-3.2.0-29-generic  abi-3.2.0-45-generic     config-3.2.0-43-generic      initrd.img-3.2.0-39-generic  System.map-3.2.0-35-generic  System.map-3.2.0-48-generic  vmlinuz-3.2.0-44-generic
abi-3.2.0-35-generic  abi-3.2.0-48-generic     config-3.2.0-44-generic      initrd.img-3.2.0-40-generic  System.map-3.2.0-36-generic  vmlinuz-3.2.0-29-generic     vmlinuz-3.2.0-45-generic
abi-3.2.0-36-generic  config-3.2.0-29-generic  config-3.2.0-45-generic      initrd.img-3.2.0-41-generic  System.map-3.2.0-38-generic  vmlinuz-3.2.0-35-generic     vmlinuz-3.2.0-48-generic
abi-3.2.0-38-generic  config-3.2.0-35-generic  config-3.2.0-48-generic      initrd.img-3.2.0-43-generic  System.map-3.2.0-39-generic  vmlinuz-3.2.0-36-generic
abi-3.2.0-39-generic  config-3.2.0-36-generic  grub/                        initrd.img-3.2.0-44-generic  System.map-3.2.0-40-generic  vmlinuz-3.2.0-38-generic
abi-3.2.0-40-generic  config-3.2.0-38-generic  initrd.img-3.2.0-29-generic  lost+found/                  System.map-3.2.0-41-generic  vmlinuz-3.2.0-39-generic
abi-3.2.0-41-generic  config-3.2.0-39-generic  initrd.img-3.2.0-35-generic  memtest86+.bin               System.map-3.2.0-43-generic  vmlinuz-3.2.0-40-generic
abi-3.2.0-43-generic  config-3.2.0-40-generic  initrd.img-3.2.0-36-generic  memtest86+_multiboot.bin     System.map-3.2.0-44-generic  vmlinuz-3.2.0-41-generic
abi-3.2.0-44-generic  config-3.2.0-41-generic  initrd.img-3.2.0-38-generic  System.map-3.2.0-29-generic  System.map-3.2.0-45-generic  vmlinuz-3.2.0-43-generic

```

Looking at this it looks to me (who knows nothing about this) as there aren't corresponding intrd files for vmlinuz 45 and up, is that a potential problem?

---

### Post by bluefrog on 2013-09-05
if u don't understand the command lines below or don't trust them, delete the files you want one by one.
Just leave at minimum the 3.2.0-44 files. that's the one u are using right now

sudo rm config-3.2.0-[2-3][0-9]-generic   will erase all twenties and thirties
sudo rm config-3.2.0-4[0-3]-generic        will leave 44 and above in /boot
sudo rm initrd.img-3.2.0-[2-3][0-9]-generic initrd.img-3.2.0-4[0-3]-generic vmlinuz-3.2.0-[2-3][0-9]-generic

and so on....

---

### Post by SASDOE2 on 2013-09-12
Thank you bluefrog (Tu es français non?). Having done this I am still getting error messages, though unrelated to full boot. Thank you for your help

---

