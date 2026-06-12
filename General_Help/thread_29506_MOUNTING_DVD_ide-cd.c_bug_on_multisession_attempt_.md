---
title: "MOUNTING DVD: ide-cd.c bug on multisession: attempt to access beyond end of device"
date: 2005-04-24
forum: General Help
---

### Post by floogy on 2005-04-24
Hello everyone,

Sorry, this is a crosspost ([ ide-cd.c bug on multisession: attempt to access beyond end of device](http://ubuntuforums.org/showthread.php?t=29396&highlight=ide-scsi)). 
Is there a active usenet newsgroup for ubuntu?

I simply don't know where this post suits the best. Yes, I do have some problems with forums like this, where I often doesn't know where's the best place for what kind of Question. 

Anyway: I got the following error in the kern.log when mounting a multisession dvd:

```
attempt to access beyond end of device
hdc: rw=0, want=18446744073707837316, limit=7533056
```

It's due to a bug in ide-cd.c of the kernel.
I use 2.6.11-1-amd64-k8.

Please read [To: Andy Polyakov Re: [ISOFS] Troubles with multi session DVDs.](http://lists.debian.org/cdwrite/2004/06/msg00086.html) and
[dvd+rw-tools: As for multi-session ISO9660 [DVD] recordings!](http://http://www.fifi.org/doc/dvd+rw-tools/#isofs4gb) .

So** I have to route my dvd device trough ide-scsi**, to read my multisession backup-dvd, because the first session is bigger than 2,2 GiB. the second is >1,3GiB.

Unfortunately I don't** know how to setup the ide-scsi emulation for 2.6.x Kernels** for that dvd-drive.

I followed this howto:
[ HOWTO: Run DVD Decrypter with Wine for backing up DVDs](http://ubuntuforums.org/showthread.php?t=27369&highlight=dvd+ide-scsi) 
and got this kernel line:
```
Kernel command line: root=/dev/sda9 ro console=tty0 quiet splash hdc=ide-scsi
```

But the kernel failed to route hdc through ide-scsi.

There was an error message at boot time, but dmesg didn't capture it.
I have to edit:
vi /etc/default/bootlogd.
```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
```

And post more details later.

Update:
bootlog.d wasn't able to log that error either, so I had to write it down by hand:

[COLOR=Red]```
modprobe -k ide-mod options "hdc=ide-scsi"
FATAL: module ide_mod not found!
```[/COLOR]

I use** s-ata** for root. and there are no sdc? build in /dev by **udev**
```
ls /dev/sd*
/dev/sda /dev/sda10 /dev/sda2 /dev/sda5 /dev/sda7 /dev/sda9
/dev/sda1 /dev/sda11 /dev/sda3 /dev/sda6 /dev/sda8
```

And also **hal **and the **gnome-volume-manager** are mounting the dvd as /dev/hdc on /media/cdrom0 :```

/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=gerhard)
```

```
lsmod |grep id
video 18824 0
ide_scsi 17284 0
ide_generic 1792 0
ide_disk 18240 0
ide_cd 44680 1
ide_core 148996 5 amd74xx,ide_scsi,ide_generic,ide_disk,ide_cd
cdrom 43176 2 ide_cd,sr_mod
scsi_mod 153584 5 ide_scsi,sbp2,sr_mod,sd_mod,libata
```

 ```
cdrecord dev=/dev/hdc -scanbus
Cdrecord-Clone 2.01a38 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
[...]
cdrecord: Warning: Running on Linux-2.6.11-1-amd64-k8
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) 'HL-DT-ST' 'DVDRAM GSA-4163B' 'A100' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

```
I found this thread, but there was no useful answer for solving the problem:
[ubuntu Forums: ide-scsi+dvd](http://ubuntuforums.org/showthread.php?t=7606&highlight=ide-scsi+dvd) 


So, I need to know how to setup routing an ATAPI device properly on Ubuntu Horay with 2.6.x kernels. What do I have to do for the kernel modules, udev.rules hal and the gnome-volume-manager are working properly with ide-scsi instead of the recommended, but in this case not working ide-cd ?

Kind regards

floogy

---

### Post by floogy on 2005-04-25
[QUOTE=floogy]modprobe -k ide-mod options "hdc=ide-scsi"
FATAL: module ide_mod not found![/QUOTE]

Hello all,

Sorry for posting to myself , but I found some older debian bug-reports regarding the line above:

[Bug#240734: initrd-tools tries to pass ide kernel paramaters to non existent ide-mod module](http://groups.google.de/groups?hl=de&lr=&threadm=1ESvV-6GZ-23%40gated-at.bofh.it&rnum=4&prev=/groups%3Fq%3D%2522FATAL%253A%2520module%2520ide_mod%2520not%2520found%2522%26hl%3Dde%26lr%3D%26scoring%3Dd%26sa%3DN%26tab%3Dwg) 
[Bug#240886: module-init-tools: modprobe pass wrong ide options to insmod](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=%23240886) 

 I use 2.6.11-1-amd64-k8 and module-init-tools from Hoary 5.04 amd64.

Where should I post this? How to solve these problems?

Here one can find other related bugs:
[google search for "module ide_mod not found" ](http://groups.google.de/groups?hl=de&lr=&scoring=d&q=%22+module+ide_mod+not+found%22&btnG=Suche) 

I want to use scsi emulation, because this will speed up things, and also the author of growisofs suggests it for 2.6.x kernels, and it's a workaround for the bug in ide-cd.c , which makes proper mounting of some multisession dvd impossible.

See:[ide-scsi](http://ubuntuforums.org/showthread.php?t=7606&highlight=ide-scsi+dvd) 

Kind regards

Gerhard

---

### Post by floogy on 2005-04-25
[QUOTE=floogy] I use 2.6.11-1-amd64-k8 and module-init-tools from Hoary 5.04 amd64.[/QUOTE]

Hello again,

Additional Info:

It's the same with the 2.6.10 kernel which comes with Horay amd64. 

Kind regards

Gerhard

---

### Post by floogy on 2005-04-29
> It's due to a bug in ide-cd.c of the kernel.
I use 2.6.11-1-amd64-k8.

Please read To: Andy Polyakov Re: [ISOFS] Troubles with multi session DVDs. and
dvd+rw-tools: As for multi-session ISO9660 [DVD] recordings! .
Here are the related Kernel Bugs and bugfixes. I'm wondering if they are already in the mentioned ubuntu kernels. Anyway, I'm stopping now to talk with myself before it'll get rediculous ;-) , and I'll compile now vanilla kernels from kernel.org. I think that is much more convenient than looking here for a solution...

[http://bugzilla.kernel.org/show_bug.cgi?id=1930](http://bugzilla.kernel.org/show_bug.cgi?id=1930)
2.6.1 fails to mount large iso9660 dvd discs with ATAPI drivers, succeeds with SCSI.

and the changelog of 2.6.10-rc3-bk13
[http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/old/patch-2.6.10-rc3-bk13.log](http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/old/patch-2.6.10-rc3-bk13.log)

where this patch is applied:
[http://bugzilla.kernel.org/attachment.cgi?id=4283&action=view](http://bugzilla.kernel.org/attachment.cgi?id=4283&action=view)

Kind regards

Gerhard Gaußling

---

