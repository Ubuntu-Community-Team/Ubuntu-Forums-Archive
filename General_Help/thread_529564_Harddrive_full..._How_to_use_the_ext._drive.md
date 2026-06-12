---
title: "Harddrive full... How to use the ext. drive?"
date: 2007-08-19
forum: General Help
---

### Post by ne0trace on 2007-08-19
Hi,
I have some very strange behaviour. I mounted my external drive /dev/sda1 to /media/windows/. I then copied my mp3 collection to /media/windows/mp3. After some time my system refused to continue working because it tells me that my HD is full.

Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/hda1              71G   67G     0 100% /
varrun                506M  232K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   96K  506M   1% /proc/bus/usb
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile

But where is my /dev/sda1?

fdisk -l shows the following...

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

and there it is...

but it seems that my mp3s didn't go to my external drive but instead it went to my internat hd.


I am a little helpless right now so if anyone has some help to offer... ;-)

Felix

---

### Post by ne0trace on 2007-08-19
No idea? Please I am starving without my music...

Felix

---

### Post by ne0trace on 2007-08-19
Did I explain anything wrong or not clear? I'm just feeling a litte "forgotten". :)

Felix

---

### Post by g2g591 on 2007-08-19
dev/sda1 is the 1st partation of your first disk. it is linux... (didn't see the 2nd part) im guessing its your root partation

---

### Post by g2g591 on 2007-08-19
/dev/sdb would be your external hd, but it isnt mounted or in those files it seems. use sudo mount /dev/sdb to mount it

---

### Post by ne0trace on 2007-08-19
But I am pretty sure that this:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes



is my external USB 500gig WD MyBook HD. So /dev/sda1/ would the first partition? Or did I misunderstand you?

Felix

---

