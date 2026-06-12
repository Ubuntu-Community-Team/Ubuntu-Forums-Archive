---
title: "unable to mount ntfs software raid - failed to read last sector"
date: 2008-03-24
forum: General Help
---

### Post by zarbon on 2008-03-24
I am trying to mount an ntfs software raid (mdadm) on 7.1 command line (no X).  I have tried over and over to get the software raid working, which it does, but I am unable to mount the partition!

I have 2 identical 500GB drives which have the same partition information on each one.  I have data that I would like to keep on the drives which I pulled out of another computer on an nvidia raid.  My current motherboard has a via fakeRAID which I couldn't get to work either.  When I used dmraid, I was left with no hard disk devices after a reboot, including my ide (non raid) hard disk and was left with a busybox initramfs prompt.  Nothing I tried would allow me to see my drives.  I tried modprobe ide-disk and modprobe ide-generic, which have worked in the past, but no luck.  Hence, I have created a software raid by using:

```
sudo mdadm --create /dev/md0 --chunk=128 --level=1 --raid-devices=2 /dev/hd[ab]1
```

its happy:
mdadm: array /dev/md0 started.

when I try to mount the /dev/md0 partition I get:

```
sudo mount /dev/md0 /mnt/raid
Failed to read last sector (976767992): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

I understand that mdadm uses the last sector for its superblock.  I thought I could just resize the ntfs partition after mdadm and it would leave it's superblock outside the ntfs partition but it didn't.  I resized the volume with ntfsresize and then used fdisk to repartition accordingly. Should I not resize the partition but resize the ntfs volume?  

I have tried doing:
```
sudo mdadm --build /dev/md0 --chunk=128 --level=1 --raid-devices=2 /dev/hd[ab]1
```

which creates the same array successfully and I can mount the partition successfully.  Unfortunately I can't figure out how to restart the raid array after a reboot.  I would have to do the mdadm --build and remount after each boot.

Can anyone help me to either fix my software raid so that it will mount properly, or show me how to use the mdadm --build so that it starts the raid and mounts after a reboot?

Edit:  I made a couple of errors above for anyone reading this.  It seems that you can only do a software raid with a Linux RAID auto partition type per this post: [http://www.dslreports.com/forum/r19909344-CentOS-5-create-RAID1-with-existing-ntfs-filesystem](http://www.dslreports.com/forum/r19909344-CentOS-5-create-RAID1-with-existing-ntfs-filesystem)

Also, according to the mdadm usage instructions, you can only use --build with "raid0, linear, multipath, or faulty, or one of their syn-onyms" per [http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

---

### Post by fjgaude on 2008-03-24
Did you ever create a filesystem for the array after it was created by mdadm?

Like so, but for the ntfs:

```
sudo mkfs -t ntfs /dev/md0
```

I'm not too sure how you create ntfs in Linux, but you likely can find out. Using --build in mdadm leaves us without superblocks which means they cannot be automounted. Thus the build after every re-boot.

The more normal way to get an array up and running is to use the --assemble command:

```
sudo mdadm --assemble --scan
```

Let us know how you are doing.

---

### Post by zarbon on 2008-03-24
Thanks for the reply.  No I did not create a file system since there was an existing NTFS file system on the drives.  I could in fact access them when I created the mdadm array using the --build option.  I was able to mount and use the files perfectly.  But as you mentioned, that would mean I would have to rebuild the array after each reboot.

I did use the --assemble option but I stopped doing that after the create command would start the array anyway.

---

### Post by fjgaude on 2008-03-24
The only way I know of is for you to use a script to mount the array after it builds it after each re-boot.

As said, you have to place the filesystem on the array after it is created for it to be recognized by md in the kernel and have it then place in the fstab file for auto mounting like any other drive.

I can't suggest the script to use. Maybe someone else here could write one if you can't.

---

### Post by zarbon on 2008-03-25
I don't know how to automatically run a script during the boot process.  That sounds like good information to know though.

Instead of recreating the file system after creating the md array, and losing all my data, I decided to give the fakeRAID another try.  When I lost all of my ide devices I had set the bios raid controller to "RAID".  I tried running it with "IDE" mode in bios and it seems to work ok.

It seems a little silly that you can't use drives with a file system already on them with a software raid array.  I guess that's just my 2 cents though.  I had been more partial to the fakeRAID option over sofware raid in the even that I ever wanted to use another OS.

Thanks for your help.

---

