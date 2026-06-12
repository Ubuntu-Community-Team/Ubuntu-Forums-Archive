---
title: "Unable to access DVD/CD R/RW drive"
date: 2007-09-09
forum: General Help
---

### Post by Uncle_Grombor on 2007-09-09
I've looked through google, the forums, even tried the Chat room, but I cannot find any information on my problem.  I have an internal DVD/CD R/RW drive that before ubuntu was installed I could access with Redhat and XP.  Ubuntu won't recognize it at all.  I'm not sure where to begin or what to do.  This drive is not giving me any errors, it's just not there, but it should be.  Thanks for the help and have a great week.

---

### Post by Alex1770 on 2007-09-09
We need to find out what kind of problem it is.

What is the output of 
```

dmesg|grep CD
cat /etc/fstab
cat /proc/ide/hd*/model
cat /proc/scsi/scsi

```?

(The first of these will only be useful if you have recently booted. The third command will probably give nothing if you are using a later version of Ubuntu.)

After putting in a CD which you know to be good, what is the output of ```
cat /etc/mtab
```?

When you put in a CD, do any messages appear at the end of a log file (/var/log/messages, /var/log/syslog, /var/log/kern.log) which look like they are giving errors?

---

### Post by Uncle_Grombor on 2007-09-09
grombor@grombor-desktop:~$ dmesg|grep CD
[   33.049446] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8240B  1.06 PQ: 0 ANSI: 5
[   33.211931] Uniform CD-ROM driver Revision: 3.20
[   33.212429] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2430.475925] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 2619.487235] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 3004.185104] sr0: CDROM not ready.  Make sure there is a disc in the drive.
grombor@grombor-desktop:~$ dmesg|grep CD
[   33.049446] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8240B  1.06 PQ: 0 ANSI: 5
[   33.211931] Uniform CD-ROM driver Revision: 3.20
[   33.212429] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 2430.475925] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 2619.487235] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 3004.185104] sr0: CDROM not ready.  Make sure there is a disc in the drive.
grombor@grombor-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=eb88a8d9-3689-49dd-8cda-b3956609f38d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=a4191948-81d3-4280-8eea-47e968724e8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
grombor@grombor-desktop:~$ cat /proc/ide/hd*/model
cat: /proc/ide/hd*/model: No such file or directory
grombor@grombor-desktop:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 4D060H3   Rev: DAH0
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: Maxtor 6Y060L0   Rev: YAR4
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: CD-RW GCE-8240B  Rev: 1.06
  Type:   CD-ROM                           ANSI SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: HP       Model: Photosmart C4240 Rev: 1.00
  Type:   Direct-Access                    ANSI SCSI revision: 02
grombor@grombor-desktop:~$ cat /etc/mtab
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
grombor@grombor-desktop:~$ 


From my limited knowledge, it looks like the second CD/DVD drive isn't even there.  The rest of it is pretty much greek to me.  Hope you can make sense of it, thanks.  There should be another drive then just Vendor: HL-DT-ST Model: CD-RW GCE-8240B  Rev: 1.06.  If I'm not mistaken, I think I have them set to cable select on the jumpers for the drives.  Could this make a difference?  It's never been an issue before though.  Thanks again.

---

### Post by Alex1770 on 2007-09-10
Looks like the problem is quite early in the chain: the drive is not being recognised at all. If you look through the output of dmesg, does it look like there is anything relevant near the CD lines (such as "device not responding", or something)?

As you say, it's hard to imagine it's a problem with the jumpers if it worked with other OSes. You could try disconnecting the working CD drive and connecting the non-working CD drive in its place to see if the problem is to do with having two drives or to do with not recognising that particular model of CD drive. If there is a problem with that particular drive then you could try searching the internet for that model to see if there are any known issues.

You could also take a look in the BIOS to see if there are any options which look like they might be disabling a second CD drive (though again this is unlikely since it worked before).

Have you tried it recently with XP? If not, then you could try that to make sure the CD drive hasn't just died.

---

### Post by Uncle_Grombor on 2007-09-11
I checked the bios and both drives are being recognized in bios.  My next step will be to open it and switch drive.  Oh, how I hate physically working with the hardware.  Oh, well.  Not that I'm afraid to or can't, just don't like it.  On the offshoot that dosen't work, does anyone know what else the problem mya be?  When I first got ubuntu from a friend I kept getting tty control errors and I couldn't even get the live cd version to run.  It would act like it was starting up then go to a black screen and give me I/O errors with a buch of gibberish that looked like it may be hex code, or memory location!?  This gibberish would randomly appear every few seconds.  This happened with mint also.  He told me it was a hardware issue.  Something I had wasn't compatable with ubuntu.  Mabey it was that drive, but if I remember right it seemed like it was trying to access my floppy drive for some reason.  I also posted about a modem problem if this might also have an effect on what is going on.  I find it strange that a DVD/CD drive would not be compatible.  I'm not sure what brand it is, but I'll see if I can find out.  Thanks all.

---

