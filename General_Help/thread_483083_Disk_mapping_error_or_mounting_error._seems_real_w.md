---
title: "Disk mapping error or mounting error. seems real weird"
date: 2007-06-24
forum: General Help
---

### Post by sinaen on 2007-06-24
my disks all seem to be mounted but at the wrong places. but the system works and indicates the / root system to be a 80 gb disk but i know that it olny is to be a 10. gig disk it seems like the partitions are reversely mounted. in some kind of way 

df -h gives this
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.0G  6.6G  2.0G  78% /
varrun                506M  188K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  112K  506M   1% /proc/bus/usb
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sdb1             229G  182G   38G  83% /yoshi/naruto
/dev/sdd1             114G   98G   11G  91% /yoshi/bebop
/dev/sdc1              74G   31G   40G  44% /yoshi/trrnt

ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdb1  /dev/sdc  /dev/sdc1  /dev/sdd  /dev/sdd1  /dev/sde  /dev/sde1  /dev/sde2  /dev/sde5

cfdisk for the different disks give me :

                                                             cfdisk 2.12r

                                                          Disk Drive: /dev/sda
                                                    Size: 81964302336 bytes, 81.9 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 9964

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sdb
                                                   Size: 320072933376 bytes, 320.0 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 38913

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sdc
                                                    Size: 80026361856 bytes, 80.0 GB
                                          Heads: 16   Sectors per Track: 63   Cylinders: 155061

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sdd
                                                   Size: 123522416640 bytes, 123.5 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 15017

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sde
                                                    Size: 10242892800 bytes, 10.2 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 1245

---

### Post by sinaen on 2007-06-26
heres a fdisk -l output. i dont know if i said it but the disk that stands for /dev/sda and the disk that stands for dev/sde is reversed. i dont know how the f**k that happend because they dont sit on the same IDE controller unit at all.

sde sits on the first ide on the mobo (the intended to be sda)
but yet the system boots up ????
sda sdb sdc sdd sits on a IDE controller card.


Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30249   242975061   83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      155061    78150712+  83  Linux

Disk /dev/sdd: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       15017   120624021   83  Linux

Disk /dev/sde: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        1186     9526513+  83  Linux
/dev/sde2            1187        1245      473917+   5  Extended
/dev/sde5            1187        1245      473886   82  Linux swap / Solaris

---

### Post by sinaen on 2007-06-26
thought it was the file /boot/grub/device.map that was the missing link in this. but seems that the "correction"  i made for it wasn't the solving factor.. :(

---

### Post by sinaen on 2007-06-26
now ive remapped my /etc/fstab file with UUID instead of the usual stuff

But i reasoned out that it either must be the udev thats freaked out. and i would gladly recieve help from someone who knows much better than i

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=50a8d4c1-4ea4-4f87-9cd4-5fb689c17351       /               ext3    defaults,errors=remount-ro 0       1
UUID=8c9321fc-a9ac-4a4a-ad6d-cc5d5b107728       none            swap    sw              0       0


#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

UUID=053713c6-0693-4f31-8599-555a735305ba       /yoshi/naruto   ext3    defaults        0       0
UUID=6c939034-f7f0-4b6e-9857-1dafe1b57a50       /yoshi/bebop    ext3    defaults        0       0
UUID=cca7b30d-a278-487d-8052-b28378e30377       /yoshi/trrnt    ext3    defaults        0       0
UUID=ad8a6038-b0f8-407b-9686-312705432e08       /yoshi/dorifto  ext3    defaults        0       0

---

### Post by sinaen on 2007-06-27
A little aftermath. it seems that its udev thats the problem. ive harmapped the disks/partitions with UUID and that works. but i dont see it as an permanent resolve.

---

