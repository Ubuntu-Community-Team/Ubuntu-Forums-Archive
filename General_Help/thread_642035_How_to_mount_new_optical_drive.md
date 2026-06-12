---
title: "How to mount new optical drive?"
date: 2007-12-16
forum: General Help
---

### Post by The Pinny Parlour on 2007-12-16
Hi all,

Installed a new optical drive now nothing I put in it works.  Something like, 'unable to mount media'.  Any tips?     Why can't these things just plug n play by the way?  Why does Linux have to mount everything?

---

### Post by The Pinny Parlour on 2007-12-16
Bump

---

### Post by t-bone510 on 2007-12-16
"mount" means making the drive accessible. Windows does it, its just not something that is apparent.

You have tried this???
```
sudo mount [diskpath]
```

You can try force mounting it too.

---

### Post by The Pinny Parlour on 2007-12-16
Thank you.  I got this:
mount: can't find [diskpath] in /etc/fstab or /etc/mtab

---

### Post by geraldm on 2007-12-16
Substitute "/media/cdrom" for "[diskpath]"
I am assuming that /media/cdrom directory exists on the computer you are using.  If not, then you might create it, or use another empty directory.

Gerald

---

### Post by dkruidhof on 2007-12-18
I am having problems with this as well. I recently put in a new DVD drive and I cannot access any media that I put into it.
When I run the previously mentioned command it tells me that hdc does not exist. I formerly had no CD drive in my laptop, just an empty slot.

I also noticed that in my /dev folder there is no hda files, which I thought was odd. It appears that my hard drive is a sda device? There isn't a sdc device.

Any suggestions?

---

### Post by logos34 on 2007-12-18
post the output for 

sudo lshw -C disk

cat /etc/fstab

ubuntu (since 7.04) uses the libata storage driver, which sees everything as 'sd_'

---

### Post by dkruidhof on 2007-12-18
kruidhof@kruidhof-laptop:/etc$ sudo lshw -C disk
Password:
  *-disk                  
       description: SCSI Disk
       product: FUJITSU MHT2030A
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 009B
       serial: NN15T4A1MF7D
       size: 27GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 26GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 1200MB
          capacity: 1200MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1200MB
             capabilities: nofs
  *-cdrom
       description: DVD reader
       product: CDRW/DVD SN-324F
       vendor: SAMSUNG
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: U203
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom


kruidhof@kruidhof-laptop:/etc$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a9605948-9d83-4879-a230-789683589088 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=50602449-f4a7-4f62-9e03-b4a1a1aaf0b1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



note: on this laptop I am running 7.04

---

### Post by logos34 on 2007-12-19
> **dkruidhof said:**
> 
  *-cdrom
       description: DVD reader
       product: CDRW/DVD SN-324F
       vendor: SAMSUNG
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: [COLOR="Blue"]/dev/scd0[/COLOR]
       logical name: /dev/sr0
       version: U203
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom

...

[COLOR="Red"]/dev/hdc [/COLOR]       /media/cdrom0   udf,iso9660 user,noauto     0       0


try this instead:
> 
[COLOR="Blue"]/dev/scd0[/COLOR] /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/cdrom and /dev/dvd should be pointing to scd0 

it's seeing the drive as a 'scsi disk' (again, libata)

---

