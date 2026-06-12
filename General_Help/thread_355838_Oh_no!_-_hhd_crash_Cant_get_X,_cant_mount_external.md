---
title: "Oh no! - hhd crash? Cant get X, cant mount external HDD to backup!"
date: 2007-02-07
forum: General Help
---

### Post by Dr_Snapid on 2007-02-07
HI everyone.

I have an emergency... it looks like my HDD has died. Ubuntu wouldnt boot this morning, gave me a million errors about multiply claimed blocks.

It asked **clone multiply-cloned blocks?** over and over.

After holding Y to get passed all that (most reported a problem in the /dev/ and /etc/ directory i think) X refused to start. After the 2 blue screens warning that x couldnt start all i get is a flashing cursor, no command line.

So I restarted and boot into recovery mode.

Before I go chasing solutions I want my data. But I cant seem to mount my external hdd from the command line. If I can mount it I will copy my data from the internal drive to the external before attempting too much on the internal.

Can someone help me? My external drive is FAT16 I think, perhaps fat32, how do I find out, and how do I mount it in ubuntu? I have tried 
**mount -t autofs /dev/hdc /media/ ** 
but no good, i cant even be sure hdc is the correct device though. **lsusb** doesnt seem to work properly either now.

If I have to I can put the external drive inside the machine rather than using the external USB case. Will it automatically mount at bootup if i do that?

I also have another machine running ubuntu, should I instead grab the dying HDD and plug it into my other machine? how would I mount it then?

I appreciate any help i can get.

Thanks all.

---

### Post by taurus on 2007-02-07
What's the output of this command after you have plugged in your external harddrive which I assume it's USB?

```
sudo fdisl -l
```

---

### Post by Dr_Snapid on 2007-02-07
it lists hda which seems OK.
hda1 ... 
hda2 ... 
hda5 ...

Then it shows /dev/dm-0 as a 38gb disk, but my external is 80gb. So this looks like my internal disk. Then it says dm-0 has no valid partition table, though.

Then it says the same again for /dev/dm-1 but it says it is only 1.5gb, cant imagine what that is!

---

### Post by taurus on 2007-02-07
Boot from the LiveCD and post the output of that same command here.

```
sudo fdisk -l
```

---

### Post by Dr_Snapid on 2007-02-07
Thanks taurus, I tried my 6.10 livecd (which has never ever worked) in safe graphics mode and it booted! I can see my external drive, and my usb drive.

fdisk -l showed me this:

/dev/sda ... 80gb fat32   < the external usb HDD!
/dev/sdb ... 128mb fat16 < my usb memory stick

This is great progress.... and now lsusb works too.

So now do i assume that my ubuntu should see these in the same places? It looks to me like USB isnt working when I boot from HDD. So i diont know if i will get the external going.

Should I try and mount the internal drive and copy the files while booted with the livecd instead?

how would I mount it?

thanks

---

### Post by Dr_Snapid on 2007-02-07
Taurus, now that i am booted to the livecd i can copy and paste... sohere is the output!

ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 127 MB, 127926272 bytes
16 heads, 32 sectors/track, 488 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488      124911+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(486, 15, 32) logical=(487, 15, 31)

---

### Post by Dr_Snapid on 2007-02-07
PLus....

ubuntu@ubuntu:~$ mount -l
unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/VANTEC EXTE type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8) [VANTEC EXTE]
/dev/sdb1 on /media/USB DISK type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8) [USB DISK]

---

### Post by taurus on 2007-02-07
Somehow it doesn't see your internal harddrive at all?  It detects your two external ones alright though.  Is your internal a PATA or another SATA?

---

### Post by Dr_Snapid on 2007-02-07
Just plain old PATA im pretty sure. I will remove the side and check tho

---

### Post by Dr_Snapid on 2007-02-07
I dont understand how it isnt detecting a drive which it will actually boot from if I dont use the liveCD... at least it was... i wonder if it will from here on in though!

What I desperately need is my var/www/ directory and my photos. I have FTP access to the www directory if i can get FTP started. I tried FTP into the PC from upstairs when it was booted in recovery mode, but ftp mustnt start when in recovery mode. Perhaps I could get recovery mode to start the ftp daemon?

All i care about is mounting the disk or whatever i need to do so i can copy these files. After that I will get another HDD if I must.

Thanks tonnes for your help so far taurus.

---

### Post by Dr_Snapid on 2007-02-07
When i shut down the pc from recovery mode, i can see it stopping services like ftp, apache etc. So why do you think i cannot access those services from my other PC?

---

### Post by Dr_Snapid on 2007-02-07
Well well well.
I booted to the live CD, where I had access to the external drive.
I mounted the internal drive by typing
**sudo mount -t ext3 /dev/hda1 /mnt**
and it worked!

Now I am copying my files!

So - looking back to my original post, would you say this issue has in fact been a HDD failure of some kind?

Your help has been very valuable, taurus. Thanks

---

