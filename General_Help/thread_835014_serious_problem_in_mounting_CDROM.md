---
title: "serious problem in mounting CDROM"
date: 2008-06-20
forum: General Help
---

### Post by a.dehqan on 2008-06-20
In the name of God ;
Hello;

I will be Thankfull if you Guide me to mount This CD .
I haven't problem with any other Cd's and they mount automatically .
Now with one cd it gives just this error when i mount cdrom :

```
debian:~# mount /dev/hdd /media/cdrom1
mount: block device /dev/hdd is write-protected, mounting read-only
mount: Not a directory

```

note that just this Cd has problem in mounting .
this is the line in fstab :
```
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto  0  0
```

i have dir Cdrom1 and it's permition is 777 .

and this is log of "/var/log/messages":

```
Jun 20 10:46:53 debian kernel: hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun 20 10:46:53 debian kernel: hdd: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun 20 10:46:53 debian kernel: ide: failed opcode was: unknown
Jun 20 10:46:53 debian kernel: ATAPI device hdd:
Jun 20 10:46:53 debian kernel:   Error: Medium error -- (Sense key=0x03)
Jun 20 10:46:53 debian kernel:   "28 00 00 01 4b a1 00 00 01 00 00 00 00 00 00 00 "
Jun 20 10:46:53 debian kernel: end_request: I/O error, dev hdd, sector 339588
Jun 20 10:46:53 debian kernel: ISOFS: unable to read i-node block
Jun 20 10:53:06 debian kernel: hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun 20 10:53:06 debian kernel: hdd: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun 20 10:53:06 debian kernel: ide: failed opcode was: unknown
Jun 20 10:53:06 debian kernel: ATAPI device hdd:
Jun 20 10:53:06 debian kernel:   Error: Medium error -- (Sense key=0x03)
Jun 20 10:53:06 debian kernel:   "28 00 00 01 4b a2 00 00 01 00 00 00 00 00 00 00 "
Jun 20 10:53:06 debian kernel: end_request: I/O error, dev hdd, sector 339592
Jun 20 10:53:06 debian kernel: ISOFS: unable to read i-node block
Jun 20 10:53:10 debian kernel: hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun 20 10:53:10 debian kernel: hdd: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun 20 10:53:10 debian kernel: ide: failed opcode was: unknown
Jun 20 10:53:10 debian kernel: ATAPI device hdd:
Jun 20 10:53:10 debian kernel:   Error: Medium error -- (Sense key=0x03)
Jun 20 10:53:10 debian kernel:   "28 00 00 01 4b a1 00 00 01 00 00 00 00 00 00 00 "
Jun 20 10:53:10 debian kernel: end_request: I/O error, dev hdd, sector 339588
Jun 20 10:53:10 debian kernel: ISOFS: unable to read i-node block
```

Debian etch 4 kernel & CPU 32 bit .

Thanks

---

### Post by VMC on 2008-06-20
Not sure I understand. You shouldn't have to mount a cd drive. Is it apaticular media that you put into the cd rom drive that can't be seen? In other words. After you boot up try and insert a media into the cd rom and it should automatically mount.

---

### Post by a.dehqan on 2008-06-20
In The name of God;
hello;

Thanks for you'r attention 
I don't know what is in CD .But Cd does not have problem with windows and works .
It does not boot automatically .
What does that LOG mean ?

ThanKS

---

### Post by ddales on 2008-06-20
Can you mount other CDs with that same drive?

How can you not know what's on the CD if it works under Windows?

---

### Post by a.dehqan on 2008-06-21
In the name of GOD
Hello;

Thanks for you'r attention .
I have used CD Writer(Asus) to read media .
But I Used CDROM (ASUS) and it could read folder of media.
I don't know what was the folder named that when CDROM could read it ,it's name was shown ???????? ,like this .

It was wonderful that CDROM could AND CD witer couldn't mount it .

Thanks

---

