---
title: "Gparted will not let me resize my partition to install windows"
date: 2013-06-21
forum: General Help
---

### Post by patagriff on 2013-06-21
I started Ubuntu 12.10 from a live CD so I could use Gparted to resize my partition and install Windows 8 on the free space. However, Gparted will not let me resize my partition. I have done this in the past with ease, but for some reason, I can't make it work this time.

Here is a screen shot of my hard drive from Gparted. It will let me enter numbers for space before and after and the new partition size, but will not let me proceed.

---

### Post by Bashing-om on 2013-06-21
[COLOR=#000000]patagriff; Hi !

I know little about Logical Volume Management but this I can help with a bit.
The screen shot of GParted shows 2 key icons (sda1 and sda5) this is to indicate that the partitions are presently mounted. One can not operate on any partitions that are mounted. Right click on the key icons and chose to swap off if it is a swap partition, and for /boot (sda1) choose unmount.
With sda5 swapped off or unmounted, the extended partition sda2 may then be manipulated.

As to why /boot would be mounted... can not advise... booting from a liveMedium, sda1 is a mystery to me why it is mounted.
[/COLOR][INDENT=2][COLOR=#000000]
not much, but a little help may go a long way[/COLOR][/INDENT]

---

### Post by ahallubuntu on 2013-06-21
Check this out:

[http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)

---

