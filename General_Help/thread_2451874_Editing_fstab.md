---
title: "Editing fstab"
date: 2020-10-12
forum: General Help
---

### Post by helen314 on 2020-10-12
I am adding my RAID data to fstab.
I understand fstab  entries have to be in specific sequence, or the entry has to be labeled. 

 Can I include /dev/... data and if so how ?

/dev/md122p1: LABEL="ECLIPSE_BACKUP"

Should invalid entry generate some kind of error somewhere ? 


[HTML]

# modified 10/12/2020 to mount md0 RAID
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdg6 during installation
UUID=dae12eb3-dd41-4262-98c3-83b3f9f8501c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdg2 during installation
UUID=D6E9-0180  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdg3 during installation
UUID=357de9dc-1696-40db-927a-6d258aa135d7 none            swap    sw              0       0
#manually adding
#/dev/md123p1: LABEL="NEW_MD_00" UUID="04893c76-3018-4414-90af-bbd15646e1e8" TYPE="ext4" PARTLABEL="NEW_MD_00"
PARTUUID="2f38c6f7-0079-48aa-b40a-b91cd3e26a9a"
# UUID="04893c76-3018-4414-90af-bbd15646e1e8" TYPE="ext4" PARTLABEL="NEW_MD_00" PARTUUID="2f38c6f7-0079-48aa-b40a-b91cd3e26a9a"

#ARRAY /dev/md/a-SATA:00 level=raid5 num-devices=3 metadata=1.2 name=a-SATA:00 UUID=49f4606c:d78a0b52:2e1386f4:25a96772
#   devices=/dev/sdb10,/dev/sde13,/dev/sdf24

/dev/md122p1: LABEL="ECLIPSE_BACKUP" UUID="92f91148-a6dd-4d06-9276-83ba2e39ec07" TYPE="ext4" PARTUUID="6a551d9f-01"
/dev/md122p2: LABEL="DEV_MD2" UUID="506d7ca6-b09c-415b-a681-f7f71ec62513" TYPE="ext4" PARTUUID="6a551d9f-02"
/dev/md122p3: LABEL="MISC_MD2" UUID="922f42e6-6ab1-4cd0-bc82-2aee9868187f" TYPE="ext4" PARTUUID="6a551d9f-03"
/dev/md122p4: LABEL="BACK_TEMP_MD2" UUID="d2af4a0a-ecaa-48bc-a80c-5dae8b20e5af" TYPE="ext4" PARTUUID="6a551d9f-04"

/dev/md126p1: LABEL="NEW_MD_00" UUID="04893c76-3018-4414-90af-bbd15646e1e8" TYPE="ext4" PARTLABEL="NEW_MD_00" PARTUUID="2f38c6f7-007$







[/HTML]

---

### Post by TheFu on 2020-10-12
Use comments for any extra data.
In theory, the system logs would have errors, but since systemd took over reading the fstab, I don't know.

fstab files don't allow extra "live" data. A single line, no wrap allowed. Only comments on other lines. The live lines must be in the prescribed format. No exceptions. 

Only one of these is allowed per line:
UUID=
LABEL=
/dev/... device

There are other ways to mount storage.

---

### Post by grahammechanical on 2020-10-12
This is what I use to get my Data partition mounted at startup.

> # to automount Data partition
UUID=311676c4-ca3e-46d7-8b81-a1a577f601d7 /media/Data ext4 auto,users,rw,relatime 0 2

The UUID is the Universally Unique Identifier of my Data partition. The utility Disks will provide the UUID of your Data partition. I got my information from this Ubuntu wiki page. Look for the part about Data partition

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

> # Data partition
# /dev/sda8
UUID=3f8c5321-7181-40b3-a867-9c04a6cd5f2f  /media/data  ext3  relatime,noexec  0  2


It tells the OS to mount the Data partition at /media/data. The media folder already exists but the data or Data folder has to be created by us. You may already know all this but the information may help others who read this thread.

Regards

---

### Post by helen314 on 2020-10-12
FYI 
mount -a 

will validate  fstab 


From discussion and man - fstab  format / sequence is fixed .
Somewhere there is a doc explaining allowable labels , not sure if using labels allows for "free hand  sequence " of options.

---

### Post by TheFu on 2020-10-12
You can use UUID=
or
you can use LABEL=
or
you can use a device reference.  

Since I don't know your level of expertise, I'm loath to get into that, but stuff like /dev/sda6 or most links under /dev/desk/by-*/  should work as will the /dev/mapper/ and /dev/{VG}/{LV} methods.

Any 1, one, uno, of those can be used in the first field.  Using 2 or more is not allowed.

These are documented in the fstab manpage. Most config files on any Unix system will have a manpage. Relevant part of the fstab manpage from a 20.04 system.  Manpages are created with the tool version and the correct version gets installed when the package gets installs.  Some manpages don't change for years and years.  Others change every 6 months. It just depends on how active the development is for a project.  In short, if you don't need the exact answer for your system, a websearch for manpage {cmd} will usually be close enough ... until it isn't.
```

       The first field (fs_spec).
              This field describes the block special device or remote filesystem to be mounted.

              For  ordinary  mounts, it will hold (a link to) a block special device node (as created by mknod(8)) for the
              device to be mounted, like `/dev/cdrom' or `/dev/sdb7'.  For NFS mounts, this field is  <host>:<dir>,  e.g.,
              `knuth.aeb.nl:/'.   For  filesystems with no storage, any string can be used, and will show up in df(1) out&#8208;
              put, for example.  Typical usage is `proc' for procfs; `mem', `none', or `tmpfs' for tmpfs.   Other  special
              filesystems, like udev and sysfs, are typically not listed in fstab.

              **LABEL=<label>  or UUID=<uuid> may be given instead of a device name.**  This is the recommended method, as de&#8208;
              vice names are often a coincidence of hardware detection order, and can change when other disks are added or
              removed.   For example, `LABEL=Boot' or `UUID=3e6be9de-8139-11d1-9106-a43f08d823a6'.  (Use a filesystem-spe&#8208;
              cific tool like e2label(8), xfs_admin(8), or fatlabel(8) to set LABELs on filesystems).

              It's also possible to use PARTUUID= and PARTLABEL=. These partitions identifiers are supported  for  example
              for GUID Partition Table (GPT).

              See mount(8), blkid(8) or lsblk(8) for more details about device identifiers.

              Note  that  mount(8)  uses  UUIDs as strings. The string representation of the UUID should be based on lower
              case characters.
```

---

