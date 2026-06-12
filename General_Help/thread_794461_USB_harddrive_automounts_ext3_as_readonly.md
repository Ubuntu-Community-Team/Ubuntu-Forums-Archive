---
title: "USB harddrive automounts ext3 as readonly"
date: 2008-05-14
forum: General Help
---

### Post by RyanGT on 2008-05-14
I just got a new usb hard drive and partitioned it into one fat32 partition and one ext3 partition.  I think I did this right, though gparted gave me trouble with the ext3 and I had to format using mkfs.ext3 from the command line.  Here is the output of dmesg | tail after I plug it in:

ryan@am2:/mnt$ dmesg | tail
[16687.652000] sd 6:0:0:0: [sdb] Write Protect is off
[16687.652000] sd 6:0:0:0: [sdb] Mode Sense: 34 00 00 00
[16687.652000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[16687.652000]  sdb: sdb1 sdb2
[16687.660000] sd 6:0:0:0: [sdb] Attached SCSI disk
[16687.660000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[16688.272000] kjournald starting.  Commit interval 5 seconds
[16688.276000] EXT3 FS on sdb2, internal journal
[16688.276000] EXT3-fs: mounted filesystem with ordered data mode.
[16689.808000] IN-world:IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1d:5a:c2:2a:a1:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=28357 PROTO=2 


The fat partition mounts correctly, but the ext3 is read only (and it has the very descriptive mount point of /media/disk.

How do I get the ext3 partition to be writable?  

I tried adding this line to fstab:
UUID=7168e795-2849-4718-babf-df35b2b89f93 /mnt/IOMEGA_ext3/ ext3 rw,user  0       0

and playing around with the options, but still couldn't get it to mount as writable.

Any thoughts?

Ryan

---

### Post by ibuclaw on 2008-05-14
Ext3, if I remember correctly should remember the permissions you give it.

So, go to the USB-Stick Mount Point, and chmod and chown the permissions to a reasonable number and a reasonable group.
That should just about to the trick for you!

ie (Just having a look at your fstab mount:
```

sudo chmod 750 /mnt/IOMEGA_ext3/ -R
sudo chown users:users /mnt/IOMEGA_ext3/ -R

```
Then add yourself to the users group
```
sudo usermod -a -G users fooname
```

Alternatively, you could just chown the folder to **plugdev** and ignore step three altogether!

[EDIT]
Perhaps you should first put your fstab line line this:
```
UUID=7168e795-2849-4718-babf-df35b2b89f93 /mnt/IOMEGA_ext3/ ext3 **defaults,users,exec** 0 2
```

Regards
Iain

---

### Post by RyanGT on 2008-05-14
Thanks for your help.  This mostly works.  There are two issues.  First, for some reason I cannot create a new folder or paste into the top level of the partition from Nautilus.  I copied some things  to the drive from the command shell and then Nautilus acts normally on the subfolders.  Second, when I right click and choose unmount, it says the drive is mounted multiple times and cannot be unmounted.

Thanks for your help,

Ryan

---

### Post by ibuclaw on 2008-05-14
Open in the terminal where the directory above the mounted folder is, and type in:
```
ls -l
```
If the owner ship is set to root, this needs changing (use my example again in my previous thread).

And secondly, try using:
```
sudo umount /mnt/IOMEGA_ext3
```

Else, reboot your system, and see how things go when you plug it back in.

Regards
Iain

---

### Post by RyanGT on 2008-05-14
Thanks, I think I am happy with how this is working.  I moved the mount point to /media/IOMEGA_ext3 and it ejects cleanly.  I think rebooting was the main (remaining) issue.

Thanks again,

Ryan

---

### Post by RyanGT on 2008-05-15
One last question and a little more info for the sake of completeness.  If anyone tries to do what I did, here is the command to find the UUID:
sudo /sbin/vol_id --uuid /dev/sdb2

I played around with difference fstab settings and finally settled on these as the best:
UUID=7168e795-2849-4718-babf-df35b2b89f93 /media/IOMEGA_ext3/ ext3 rw,user  0       0

My final question is this: I don't always intend to have this drive connected when I boot.  It is a minor annoyance, but I get a message that mounting the drive failed during boot up if it is not connected.  Is there a way to make that message go away?  It seems that the device can't be automounted correctly without the fstab entry (I think because it is ext3), but having the fstab entry causes my computer to try and mount it at boot up.  Is there a way to solve both issues?

Thanks again,

Ryan

---

