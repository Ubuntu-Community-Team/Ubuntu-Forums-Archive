---
title: "Problem with new DVD drive and/or fstab"
date: 2007-09-15
forum: General Help
---

### Post by J-Rod on 2007-09-15
I just installed a new hard drive, and a DVD/RW drive. The HDD was not really a problem, other than it being a 320gb drive, and it reports to gparted as 298, and then looks like it uses 5 gb for filesystem. That's beside the point... :)

*edit* I forgot to post the error when I click on the DVD drive: "mount: special device /dev/cdrom does not exist
"

I am guessing this is a problem with my fstab. Original drive worked ok, other than it didn't read all my discs properly. In my computer devices, it appears to show up as "CD-ROM 1", but there's no entry of that name in fstab. Does it get mounted from some other procedure than fstab? Here is my current and backed up fstab, if anyone can help me out it would be appreciated. I have been using Ubuntu for close to a year now, but this is the first time I have changed devices.

CURRENT:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=d489473c-db7f-477a-890e-59d4043349f1 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc3 -- converted during upgrade to edgy
UUID=69d40a8d-e9a6-440c-b88d-5e10b704a920 /home ext3 defaults 0 2
# /dev/hdc2 -- converted during upgrade to edgy
UUID=f1e42a9a-88b9-4638-bf48-7a17de12a255 none swap sw 0 0
/dev/cdrom     /media/cdrom  	auto  	ro,noauto,user,exec  	0 0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=006400ca-60f3-421d-8357-8b7bacef734f /mnt/oldstuff ext3 auto,user,exec,rw 0 0

BACKUP:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=d489473c-db7f-477a-890e-59d4043349f1 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc3 -- converted during upgrade to edgy
UUID=69d40a8d-e9a6-440c-b88d-5e10b704a920 /home ext3 defaults 0 2
# /dev/hdc2 -- converted during upgrade to edgy
UUID=f1e42a9a-88b9-4638-bf48-7a17de12a255 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=006400ca-60f3-421d-8357-8b7bacef734f /mnt/oldstuff ext3 auto,user,exec,rw 0 0

---

### Post by logos34 on 2007-09-15
what does 
[B]
sudo lshw -C dis[/B]k

show?

could be you need to change '/dev/cdrom' to '/dev/scd0' or '/dev/hdx' format
> 
320gb drive, and it reports to gparted as 298

remember, the OS sees 1 GB as =1,073,741,824 bytes, *not *1,000,000,000 as hdd manufacturers claim (looks better from marketing perspective)

---

### Post by J-Rod on 2007-09-15
Yeah, I forgot about that part, as far as how manufacturers report storage. I managed to fart around enough to get things working, thanks for the reply though. I was looking at my fstab, and realized how ugly it looked. I found an older backup from before I went from dapper to Feisty, and made that my current. Voila, the DVD drive reads discs and automounts now. I also managed to get my HDD1 mounted as /mnt/storage, shared it and made a link to it from my desktop, and changed the permissions from root to my normal user.

```
  *-cdrom                 
       description: DVD-RAM writer
       product: HL-DT-STDVD-RAM GSA-H55N
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.00
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma4
     *-disc
          physical id: 0
          logical name: /dev/hda
  *-disk:0
       description: ATA Disk
       product: ST340810A
       vendor: Seagate
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 3.39
       serial: 5FB5NL1R
       size: 37GB
       capacity: 37GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@1.0,1
          logical name: /dev/hdc1
          capacity: 10236MB
          capabilities: primary
     *-volume:1
          description: Linux swap / Solaris partition
          physical id: 2
          bus info: ide@1.0,2
          logical name: /dev/hdc2
          capacity: 1027MB
          capabilities: primary nofs
     *-volume:2
          description: Linux filesystem partition
          physical id: 3
          bus info: ide@1.0,3
          logical name: /dev/hdc3
          capacity: 26GB
          capabilities: primary
  *-disk:1
       description: ATA Disk
       product: WDC WD3200JB-00KFA0
       vendor: Western Digital
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: 08.05J08
       serial: WD-WCAMR4491569
       size: 298GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@1.1,1
          logical name: /dev/hdd1
          capacity: 298GB
          capabilities: primary
jrodder@jrodder-desktop:~$ 


```

In case you still wanted to see. :)

---

### Post by logos34 on 2007-09-15
>   *-cdrom                 
       description: DVD-RAM writer
       product: HL-DT-STDVD-RAM GSA-H55N
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/**[COLOR="Red"]hda[/COLOR]**
       version: 1.00
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma4

just what I thought.

But if you have it working now don't touch anything!

---

### Post by DarkDemonNT on 2008-04-29
>   *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.05
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/11 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
It can't see a blank disk.
Could you help me?

---

