---
title: "Edgy root file system notshowing in df or mount"
date: 2006-11-01
forum: General Help
---

### Post by domf on 2006-11-01
HI,

I upgraded to Edgy a few days back and after a few "teething problems" thought I was OK - however I've just noticed that the root file system does not show up in df or mount

```

dom@tiny:/etc$ 
dom@tiny:/etc$ mount
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw)
/dev/hdb1 on /mnt/backups type ext3 (ro,errors=remount-ro)
/dev/hdb2 on /var/lib/vmware type ext3 (rw,errors=remount-ro)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
dom@tiny:/etc$ 
dom@tiny:/etc$ df -h
Filesystem            Size Used Avail Use% Mounted on
varrun               1014M  116K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  996M   2% /lib/modules/2.6.17-10-386/volatile
/dev/hdb1              97G   97G     0 100% /mnt/backups
/dev/hdb2              88G   66G   18G  80% /var/lib/vmware
dom@tiny:/etc$ 

```

It is in /etc/fstab and the UUID from vol_id checks out with /etc/fstab.  However if I look at /etc/mtab there is no entry for /.

Running sudo mount -av gives me:
```
mount: proc already mounted on /proc
mount: UUID=ade8e598-2183-4f31-a095-d9130a4950db already mounted on /mnt/backups
mount: UUID=2f3a65a1-88b1-44f2-b5c4-ce00173b406a already mounted on /var/lib/vmware

```


Any suggestions on how to troubleshoot this would be appreciated!


Dom

---

### Post by domf on 2006-11-01
If anyone has any ideas on how to troubleshoot this or wheer else I can look for help I'd be very grateful.


Dom

---

### Post by taurus on 2006-11-01
Maybe you want to include your /etc/fstab!!!

---

### Post by domf on 2006-11-02
fstab and dtab below.

The UUID in fstab is correct.  

All ideas welcome!

Dom 

dom@tiny:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=a3de38df-11f4-4598-bb06-adc801711814 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb1 -- converted during upgrade to edgy
UUID=ade8e598-2183-4f31-a095-d9130a4950db /mnt/backups ext3 ro,defaults,errors=remount-ro 0 1
# /dev/hdb2 -- converted during upgrade to edgy
UUID=2f3a65a1-88b1-44f2-b5c4-ce00173b406a /var/lib/vmware ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=72e6342f-3bc4-4350-9f09-b2fac1aac84d none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
dom@tiny:~$ cat /etc/mtab 
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-386/volatile tmpfs rw 0 0
/dev/hdb1 /mnt/backups ext3 ro 0 0
/dev/hdb2 /var/lib/vmware ext3 rw,errors=remount-ro 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
dom@tiny:~$

---

### Post by domf on 2006-11-02
for dtab read mtab!

---

### Post by domf on 2006-11-02
OK - some progress in troubleshooting this maybe.  I booted off thelive CD and tried to run fsck against this filesystem.  This failed with the error message:

dom@tiny:~$ sudo fsck /dev/hda1
fsck 1.39 (29-May-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/hda1

Since this isn't a ntfs file system I ran fsck.ext3 which ran sucessfully & cleanly.


I *think* that the system is trying to fsck this file system at mount time but failing for some reason as it appears to think it is nfts.  Why (or if) that rsults in it not appearing in dtab I don't know.


Any suggestions on what to try now?


Dom

---

