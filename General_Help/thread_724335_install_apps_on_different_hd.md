---
title: "install apps on different hd"
date: 2008-03-14
forum: General Help
---

### Post by perhhk on 2008-03-14
bit of a nooby question here, but I have an ubuntu pc with two hds, is there anyway of installing some programs to a different hardrive becuase of space issues

---

### Post by forestpixie on 2008-03-14
don't think so - what sort of space issues do you have

---

### Post by perhhk on 2008-03-14
two hds - 15gb and 8.4gb


There is a dead windows partition on the 15gb hd, which I will delete, but when it fills up again I will either have to get a bigger hd or start installing on the 8gb

---

### Post by forestpixie on 2008-03-14
what does this in terminal give

```
df -h
```

if you've got an unused partition - delete as you say and format as ext3, add it to your fstab so it automounts 

perhaps you can move stuff from your /home if you're running out of / space

---

### Post by perhhk on 2008-03-14
so should i just keep stuff on the other hd so that the first one has space for programs?

---

### Post by forestpixie on 2008-03-14
That'd be the idea I'd say, so you have 2 options - leave it as ntfs and copy files to it or reformat to ext3 and copy files to it

---

### Post by koenn on 2008-03-14
> I have an ubuntu pc with two hds, is there anyway of installing some programs to a different hardrive becuase of space issues Yes, you can, but it's not very easy. There's to ways

- if you compile the packages from source, you can control where they get installed. So theoretically, you can move 'some' programs to an other disk. Not recommended because 
* you give op the ease of use of packet managers / installing binaries
* uninstalling can become messy 
* you're messing with the directory hierarchy and the location of files within it. eg. executable binaries (should) go under /usr/bin or usr/sbin - yours won't. 

1- move the /usr directory to (a partion on) your second drive. The end result will be that you mount (a partition on) that 2nd drive to /usr. Newly installed programs will go to /usr and thus end up on the 2nd drive. This also means you'd have to move/copy the content of your current /usr dir to that partition, otherwise you'll find your current programs just disappeared (including hugh parts of your operating system)

here's an untested recipe - think it through before you try it (I may have overlooked something) : 
1- put the new disk in the pc
2- create a partition and a filesystem on the disk (fdisk, Partition Manager, GPartEd, ...)
3- mount it somewhere (eg to /mnt/newdisk)
4- copy your current /usr files  (eg cp -R /usr/* /mount/newdisk). Check that this worked correctly. You don't want a /mount/newdisk/usr/[content], you want /mount/newdisk/[content of usr]
5- unmount /mount/newdisk
6- mount that partition to /usr
7- if stuff now works, edit fstab so that the new partition is mounted to /usr on boot

Since you copy the old /usr, it's still there so you can roll back
you may choose to delete the contents of the old /usr and gain some extra space on your first harddrive, but that's going to be difficult, because /usr is your second hd now, you can't easily reach the original /usr directory. Booting from a live cd may get you there.

---

### Post by perhhk on 2008-03-20
well the 8.4gbhd seemed to be causing some problems with the computer so I removed it, but I am surprised apps can only be on one hd or another with synaptic

---

### Post by koenn on 2008-03-20
> **perhhk said:**
> well the 8.4gbhd seemed to be causing some problems with the computer so I removed it, but I am surprised apps can only be on one hd or another with synaptic
that's because
1/ Linux / unix have a +/- standardized directory tree with dedicated directories for certain kinds of files : user files in /home/<username>, configuration files in /etc, binary executables (prigrams) in /bin or /user/bin and the likes, depending on the kind of program. 
You can, with some effort, have programs elsewhere, but you'd be messing with the way the OS is organised. 

2/  a program is told where to install and where its config files and so are when the source code is compiled, so you usually don't get (or need) an installer that offers you a choice of where to install. Choosing where to install a program is usually not necessary, or even not advisable, re 1/

---

### Post by gaussian on 2008-03-20
Actually, it is possible without messing with symlinks etc. But it calls for a higher order tool called LVM (logical volume manager). Using alternate installation CD you should be able to setup a logical volume that spans several disks. Then you can use those several disks as a single file system. But in order to do so you need to get little comfortable with command line and the LVM (actually LVM2) basics. I have not done this myself, but I have read about people using a single LVM system on Asus EEE with Ubuntu with an extra storage media.

Downside (especially with a failing disk): if you don't have backups and one of the disks fails you could loose all (since there is no "clean separation" between the two disks).

---

