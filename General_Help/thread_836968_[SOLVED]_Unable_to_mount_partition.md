---
title: "[SOLVED] Unable to mount partition"
date: 2008-06-22
forum: General Help
---

### Post by uberlube on 2008-06-22
I have been experiencing difficulty getting my sda4 mounted on a clean install of DreamLinux. When I double click on the Computer icon on the desktop it shows me the partition right away, but when i try to access it it tells me

> Cannot mount volume.

You are not privileged to mount this volume.

So naturally I opened up a root file manager and tried to access it through the mount point i specified during the install (/media/vault). Once i got into the media dir i was surprised to find that there was nothing in it, i even activated the hidden folder view with no results. Next I open up a terminal and tried to manually mount it and i got this

> dan@laptop:~$ sudo mount /dev/sda4
mount: mount point /media/vault does not exist


So now i am left scratching my head as to how to get this to work. If ive missed anything here please let me know. Also here is my fstab

```
/dev/sda2	/	ext3	defaults	0	1
/dev/sda3	/home	ext3	defaults	0	2
/dev/sda4	/media/vault	ext3	defaults	0	2
/dev/sda1	none	swap	sw	0	0
proc	/proc	proc	defaults	0	0
```


:):(:confused::mad:

---

### Post by plucky on 2008-06-22
This link might help

[Psychocats:Mounting Linux Partitions](http://www.psychocats.net/ubuntu/mountlinux)

Good Luck

---

### Post by uberlube on 2008-06-22
Thanks! Found the problem while going through the steps.

---

