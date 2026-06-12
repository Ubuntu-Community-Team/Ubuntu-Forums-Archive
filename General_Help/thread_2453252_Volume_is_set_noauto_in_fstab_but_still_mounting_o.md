---
title: "Volume is set noauto in fstab but still mounting on boot"
date: 2020-11-06
forum: General Help
---

### Post by BarnOwl on 2020-11-06
I have a Disk/Movie/Mythtv server that is running Xubuntu with a lot of USB storage attached that was recently upgraded from Ubuntu 18.04 to 20.04.  It has two backup volumes that are in /etc/fstab but set to noauto which means they shouldn't mount on boot.  Normally, they get mounted and unmounted when different backups are run in crontab.  Before I performed the upgrade, I mounted one of them and did a backup manually.  However, I neglected to unmount that volume when I performed the in place upgrade to 20.04.  After the upgrade everything works but, the backup volume that was mounted during the upgrade mounts on boot when it shouldn't.  The lines from /etc/fstab for both volumes are below.

```
UUID=bd4e93be-e17e-4a68-872b-41f2e12dd8fe       /mnt/LocalBackup        ext4            defaults,noauto,noatime,nofail,x-systemd.device-timeout=90              0 2

/dev/mapper/MS_Backup_VG-disk1  /mnt/backup     ext4            defaults,noauto,noatime,nofail,x-systemd.device-timeout=90              0 2

```

The volume that is mouting at boot is /mnt/LocalBackup.  

It's not a big problem to unmount the volume at boot and even if I don't the next time a backup runs it'll get unmounted.  However, I'd like to know why that volume is getting mounted and how to stop it..

Thanks for any replies.

---

### Post by dinkidonk on 2020-11-06
How do you determine that the drive is mounted? Some file managers may ignore noauto and mount drives regardless, so right after boot try to open a terminal and run "lsblk" and check if the device is actually mounted.

---

### Post by BarnOwl on 2020-11-06
I haven't run lsblk but, df -h shows /mnt/LocalBackup as mounted at boot and just as importantly, it shows that /mnt/backup (The other volume that is set to no auto in /etc/fstab.) is not mounted.  That and the fact that sudo umount /mnt/LocalBackup actually unmounts a volume convinces me that the drive is indeed mounted at boot.

That actually brings up an interesting observation.  Those volumes don't show up in Thunar as being available to mount and I'm not sure why.  There actually ia another partition out there that is not in fstab that does show up.  My guess is that if it's in fstab it doesn't show up in Thunar.

---

### Post by dinkidonk on 2020-11-06
I bet this is caused by udev / udisks(2). You will most likely need to [write a udev rule]("https://askubuntu.com/questions/652905/how-to-disable-usb-automount-in-xubuntu-14-04") to prevent the USB drives from mounting.

---

### Post by BarnOwl on 2020-11-06
Thanks for the reply.  I'm not real keen on doing that.  It's not that big a problem.  Besides, that leaves a few questions.  First, the fact that it's an LVM volume might explain it but, why doesn't udev mount /mnt/backup?  Also there is another partition on a USB disk that is not in fstab and it doesn't get mounted.   So, I don't think udev is just mounting every USB partition it sees.  The other question is why would udev mount the partition at the mountpoint that is in fstab when fstab says not to mount it?

---

### Post by BarnOwl on 2020-11-06
Right now mythtv is being used (I don't want to irritate the wife.) but, when I can, I'll try commenting out the line in fstab and see if the dive still gets mounted during reboot.  That will definitively determine whether udev is misbehaving,

---

### Post by The Cog on 2020-11-06
> My guess is that if it's in fstab it doesn't show up in Thunar.
I can confirm that. I get lots of unwanted icons on the desktop unless I hide unused partitions by adding them to fstab as noauto (this is using Xubuntu).

Xubuntu has settings somewhere for behaviour (i.e. automount) of removable media. Can't remember the details and not in front of Xubuntu right now. It may be worth looking for settings like that.
Also, the "0 2" on the end is suggesting that an fsck should be run on those partitions (I think at boot time). I always use "0 0" for disks I don't automount.

---

### Post by BarnOwl on 2020-11-06
> **The Cog said:**
> Xubuntu has settings somewhere for behaviour (i.e. automount) of removable media. Can't remember the details and not in front of Xubuntu right now. It may be worth looking for settings like that.
Also, the "0 2" on the end is suggesting that an fsck should be run on those partitions (I think at boot time). I always use "0 0" for disks I don't automount.

There is a removable drive and media in settings.  I have that turned off.

You could be right about the 2 but, I'm not so sure.  From the man page:

```
This  field  is  used by fsck(8) to determine the order in which
filesystem checks are done at boot time.   The  root  filesystem
should  be  specified  with a fs_passno of 1.  Other filesystems
should have a fs_passno of 2.  Filesystems within a  drive  will
be  checked  sequentially,  but  filesystems on different drives
will be checked at the same time to utilize  parallelism  avail&#8208;
able  in  the  hardware.   Defaults  to zero (don't fsck) if not
present.

```

It's certainly possible to check the volume without mounting it.  In fact you'll likely cause problems if you fsck a mounted partition, So, I'm not certain the filesystem isn't checked with the noauto option.  I'd prefer these get checked.  As far as I know, setting it to zero will just speed up the boot a bit.  This system isn't booted all that often so, I'm okay with the wait,   Now if I wanted to get rid of the icon for that partition I'm not using, it would make sense to put it in fstab and set this to zero.  I'll eventually delete that partition, it's some stuff I backed up before t upgraded.

---

### Post by BarnOwl on 2020-11-06
I was able to comment out the line for that drive in /etc/fstab and reboot.  The drive didn't mount which pretty much rules out udev.   When I uncommented it and rebooted it mounts.  So can anyone tell me why the noauto directive isn't working on that drive but, is working on the other?  As I said in my original post, this didn't start happening till after I upgraded to 20.04.

---

### Post by Holger_Gehrke on 2020-11-06
Another rabbit hole to look down into: systemd automount units. Try 'systemctl list-units -t automount' to find out if there's one of those set up for the file system you don't want to mount automatically.

Holger

---

### Post by Morbius1 on 2020-11-06
I tried to recreate your symptom and I cannot but ...................

A couple of things to double check perhaps:

Run this command to make sure that the systemd fstab generator really lists noauto as an option:
```
systemctl cat mnt-LocalBackup.mount
```
In my experimant it does:
> tester@vxub2004:~$ systemctl cat mnt-LocalBackup.mount
# /run/systemd/generator/mnt-LocalBackup.mount
# Automatically generated by systemd-fstab-generator

[Unit]
Documentation=man:fstab(5) man:systemd-fstab-generator(8)
SourcePath=/etc/fstab
Requires=systemd-fsck@dev-disk-by\x2duuid-6b97cf75\x2d4e86\x2d475e\x2db308\x2dd147af00d990.service
After=systemd-fsck@dev-disk-by\x2duuid-6b97cf75\x2d4e86\x2d475e\x2db308\x2dd147af00d990.service
After=blockdev@dev-disk-by\x2duuid-6b97cf75\x2d4e86\x2d475e\x2db308\x2dd147af00d990.target

[Mount]
Where=/mnt/LocalBackup
What=/dev/disk/by-uuid/6b97cf75-4e86-475e-b308-d147af00d990
Type=ext4
Options=defaults,noauto,noatime,nofail
Another thing to check is to see if some other systemd service or process is dependent on this mount being active:
```
systemctl --reverse list-dependencies mnt-LocalBackup.mount
```
In my case I had none but this wouldn't include and script or application that has sudo privileges from forcing a mount on its own.

---

### Post by BarnOwl on 2020-11-06
> **Holger_Gehrke said:**
> Another rabbit hole to look down into: systemd automount units. Try 'systemctl list-units -t automount' to find out if there's one of those set up for the file system you don't want to mount automatically.

The command as you stated it only shows a single automount process: proc-sys-fs-binfmt_misc.automount

However, you did get me thinking along other lines and that's helpful.  So, I compared systemctl list-units and systemctl list-unit-files.

The list-unit-files does show both of the following generated and enabled:

mnt-LocalBackup.mount  <--The one that mounts when it shouldn't
mnt-backup.mount<--- The one that doesn't mount when it shouldn't

Neither of these show up in list-units.  My knowledge of systemd is only moderate but, I don't see anything wrong there.  My understanding is that if the drive is mounted, by systemd, it's corresponding mount will show up in list-units.  Otherwise it won't.  I need to mention that I had manually unmounted /mnt/LocalBackup after the last boot.  I did test my understanding by manuall mounting /mnt/backup and sure enough; it showed up in list-units.  Then I unmounted it so I wouldn't leave it mounted.

Perhaps there's another way to determine whether there's something in systemd that's mouting it.

---

### Post by BarnOwl on 2020-11-06
> **Morbius1 said:**
> Another thing to check is to see if some other systemd service or process is dependent on this mount being active:
```
systemctl --reverse list-dependencies mnt-LocalBackup.mount
```
In my case I had none but this wouldn't include and script or application that has sudo privileges from forcing a mount on its own.

I think that's it!!  That command came up with nfs-server.service.  So, I took a look at /etc/exports and, sure enough, /mnt/LocalBackups was there.  I have no idea when or why I put it in there but, I probably didn't intend for it to stay or I quit doing whatever I was doing that needed it.  Considering the fact that I've been unmounting it everytime I boot, I'm pretty sure I don't need it.  Something must have changed in 20.04 because I'm certain that line was in there before I upgraded.  Funny how some fool doing something like that can come back and bite you. :)

I've commented it out.  Right now myth is recording a show for the wife.  My next window for rebooting is at 4:00 PM EST.

---

### Post by BarnOwl on 2020-11-06
That was it.  Thanks to all who helped.  I would have gone a very long time before figuring that one out.

---

