---
title: "[SOLVED] Flash drive does not read"
date: 2007-07-10
forum: General Help
---

### Post by boldexplorer on 2007-07-10
I have two flash drives both work in Windows but the one is not seen and unmountable in Ubuntu.

I have formatted the drive, drive through windows to FAT and FAT32 nothing.
I would really like it to work.
Is there anything I can do?

---

### Post by vineethbs on 2007-07-10
Hi boldexplorer, could you please copy paste what is seen when you try to mount your drives ? (i meant errors,messages from a terminal)

---

### Post by boldexplorer on 2007-07-10
there is nothing! 
the drive and my laptop simply do not even see each other. I know that the drive works, just not with my ubuntu.

the little light that flashes to show you that there is some semblance of life does not even blink!

---

### Post by vineethbs on 2007-07-10
hi,

after you plug in the flashdrive, did you try mounting it, with 

mount /dev/**** /<some directory 

where **** is usually sda<number> or sdb<number>

---

### Post by boldexplorer on 2007-07-10
If I just type mount then I get 

[I]brett@brett-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=brett)
[/I]

if I type mount/dev/sda1 which is I think the flash drive then I get:

[I]brett@brett-laptop:~$ mount/dev/sda1/
bash: mount/dev/sda1/: No such file or directory
[/I]

---

### Post by vineethbs on 2007-07-10
hi,
1) sda1 is your root filesystem device, so see (3)
2) its not /dev/sda1/ ,its /dev/sda1 (no / character)
3) try /dev/sdb*, where * is the partition number (obviously your hdd is SCSI [:)])
4) I think the mount command would take the file mount point from the /etc/fstab file, but you need to check whether a corresponding file mount point exists for your device.

---

### Post by boldexplorer on 2007-07-10
> **vineethbs said:**
> )
3) try /dev/sdb*, where * is the partition number (obviously your hdd is SCSI [:)])
4) I think the mount command would take the file mount point from the /etc/fstab file, but you need to check whether a corresponding file mount point exists for your device.

With regards to points 3 and 4.
3) How do I determine what the partition number is?
4) how do I check if there is a mount point for the drive in the /etc/fstab file and how do I correct it if there is not a mount point for the device.
Sorry I am still quite new to Linux so what exactly am I looking for and how do I fix/replace it if it is not there. 

Thanks

---

### Post by vineethbs on 2007-07-10
To be frank, I am not sure about (3), but looking in the /sys directory would help. (I have always relied upon brute forcing it :p)

4) You can edit /etc/fstab as root
sudo vim (or editor of your choice) /etc/fstab

each line in the fstab file consists of the following fields (this can be very well understood from the entries already there)

essentially you need to add the device name which is /dev/sdb*, the mount point, filesystem type etc, further info @ [http://www.debianhelp.co.uk/fstab.htm](http://www.debianhelp.co.uk/fstab.htm)

but under a normal installation of ubuntu, I think this is automatically done (when you plug in your device). So your problem should be because of some other reason. I think either the kernel is not recognising the device or its simply related to the partitioning or the filesystem. You said you had formatted using FAT32, so at this point, I do not know really what is happening.

---

### Post by boldexplorer on 2007-07-12
vineethbs thank you very much for all your help.
Unfortunately I am either too stupid or the problem is more complex than I thought. 

My fstab file looks ok so I am clueless as to what might be the problem between my flash and computer! I also do not have loads of time at the moment to try and solve this so I am going to abandon it since my other flash drive works.

Thanks again for all your help! 
I am going to mark this as resolved even though it technically isn't but I am not taking it further and do not wish to waste anyone else's time on it!

ciao!

---

