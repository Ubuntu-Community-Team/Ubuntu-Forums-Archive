---
title: "Unable to mount root filesystem"
date: 2006-07-21
forum: General Help
---

### Post by FredLick on 2006-07-21
Of some unknown reason, my computer started to get unstable just recently. Now everything stalls when the computer tries to mount the root filesystem, and I get this busybox shell thingie.. So I am wondering, is there any possibilities of retreiving data from my HD, while running my computer with the live CD? If I try to access the HD now, I get a message that says the hd cant be mounted :(

---

### Post by longinus on 2006-07-21
I never could mount my HD with the live CD by just clicking on them... always had to do something like...

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

### Post by FredLick on 2006-07-23
Thanks for the advice. But it didnt work for me. I get the following error>

[I]mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/I]

Any ideas what I am doing wrong?

---

