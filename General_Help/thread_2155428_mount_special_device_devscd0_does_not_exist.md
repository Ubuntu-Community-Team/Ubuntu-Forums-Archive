---
title: "mount: special device dev/scd0 does not exist"
date: 2013-06-18
forum: General Help
---

### Post by ColombianBootloader on 2013-06-18
Hello there..

Well, I have checked about my issue here but, I did not find a suitable answer in any of the threads. I have a IBM R52 machine and I am running Ubuntu 12.04 LTS. I am trying to mount my cdrom
but I have the error "mount: special device dev/scd0 does not exist". I have done the following and I am not sure if I am missing something. 

1) /etc/fstab/ output for my cdrom is the following:
   /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
   
   As far as I understand I can execute mount like this:

   mount /media/cdrom0  

   and that should be enough for me to be able to access the cdrom in the /media/cdrom0 mount point. 

2) I have checked the output of the following command.

   sudo lshw -short

   and this is what I get in return  ( I have just pasted the part related to the cdrom)

   /0/100/1f.2/1      /dev/cdrom  disk           DVD-RAM UJ-830S
  /0/100/1f.2/1/0    /dev/cdrom  disk           

 I am new to linux and I think that I understand the mechanics of mount, but I am just wondering if I am missing something here.
any help will be really appreciated.

Kind regards

---

### Post by steeldriver on 2013-06-18
First of all is this the Server or Desktop edition? The Desktop edition should automount CDROMs by default (in /media/cdrom), only the Server edition should need manual mounting

If you *do* have the server edition, then how did you determine the block device name /dev/scd0? are you sure it's correct? Since lshw is telling you that the block device is (or at least has a symlink to) /dev/cdrom you should be able to use that e.g. on my system the 'real' block device is /dev/sr0 but I can use the symlink /dev/cdrom to mount it

```

$ $ sudo lshw -C disk
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-842
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: RB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
$
$
$ sudo mount /dev/cdrom /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only

```

---

### Post by ColombianBootloader on 2013-06-19
Hi there

it is a desktop ediiton. I have tried your post but I have the following error.

  *-disk                  
       description: ATA Disk
       product: IC25N080ATMR04-0
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MO4O
       serial: MRG4W9K7G3USKH
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=cccdcccd
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-830S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
wilson@w:~$ sudo mount /dev/sr0 /media/cdrom0
mount: you must specify the filesystem type

---

