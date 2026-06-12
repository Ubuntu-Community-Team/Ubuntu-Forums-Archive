---
title: "ext3 hd blaims to be ntfs"
date: 2006-07-27
forum: General Help
---

### Post by humhum on 2006-07-27
Hello everybody.
I'm trying to get my former windows xp hd work as a storage hd for ubuntu. I have first divided it into two partitions in order to be able to save some data to the other partition from the windows installation. When I had transfered the files to the ext3 partition I used gparted to format the ntfs partition to ext3 as well. And after some hair bulling I've ended up with one ext3 partition, with my files on it. So thats something about what i've done...

Now when I try to mount the hd, the system gives this message:
```

 mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
The hd will be mounted, but i won't get write permmission for it... 
In the fstab i have the line for the hd as follows:
```

/dev/hdb1	/home/ukkonen/Desktop/Varasto/	ext3	defaults	0	0

```
and sudo fdisk -l gives this information for hdb:
```

Levy /dev/hdb: 80.0 Gt, 80026361856 tavua
16 päätä, 63 sektoria/ura, 155061 sylinteriä
Yksiköt = 1008 * 512 = 516096 -tavuiset sylinterit

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/hdb1   *           1      155056    78148192+  83  Linux

```
(sorry for the finnish language, but I hope that you can figure it out)

And when I do the dmesg | tail I get this kind of information:
```

[17179625.136000] Bluetooth: RFCOMM socket layer initialized
[17179625.136000] Bluetooth: RFCOMM TTY layer initialized
[17179625.136000] Bluetooth: RFCOMM ver 1.7
[17179695.992000] Warning: /proc/ide/hd?/settings interface is obsolete, and wil l be removed soon!
[17179722.876000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179722.876000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount op tion errors=recover not used. Aborting without trying to recover.
[17179722.876000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS vo lume.
[17179722.904000] kjournald starting.  Commit interval 5 seconds
[17179722.904000] EXT3 FS on hdb1, internal journal
[17179722.904000] EXT3-fs: mounted filesystem with ordered data mode.

```
So there is some kind of boot sector problem, I've tried to write the MBR (what ever it is?) again with testdisk, but with no results. What ever I do the system still somehow thinks that the filesystem should be ntfs :sad: 

I would really appreciate some help...

---

### Post by pclogic on 2006-07-27
First, verify that your /dev/hdb1 partition is actually of type ext3 by running the command: "df -ahT".  If your parition is not listed as type ext3, you can format it using this command: "sudo /sbin/mkfs.ext3 -m 0 -j /dev/hdb1".  You will have to unmount the parition first if it is mounted.  Just run the command "sudo umount /dev/hdb1". 

FYI I just did the same thing you did where I added a former NTFS hard drive to my server.  Now, whenever I reboot, my system hangs right before GRUB should start.  However, if I power off the server using the power button and power it back on, it boots normally.  I have a forum post from a few hours ago asking about this issue, but nobody has responded yet.

Jason

---

### Post by humhum on 2006-07-27
It's ext3... hmph.. 
oh! stupid me, I had the old line in the fstab for ntfs file system...:o  
so it was messing things up..

But how come i can't get rw rights for my user account working?

I have tryed this tutorial:
[http://psychocats.net/ubuntu/mountlinux.html]("http://psychocats.net/ubuntu/mountlinux.html")

,tried to change the rights with clicking from sudo nautilus and then also tried to add umask=000 to the fstab... 
any suggestions?

thank you

edit..
so this was the problem fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
**/dev/hdb1**       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/hdb1**	/home/ukkonen/Desktop/Varasto/	ext3	defaults	0	0
```
;-)

..and after boot up the hd also mounted proberly with rw rights.
So everything is working perfectly now..

---

