---
title: "Some Partitions not mounting on startup"
date: 2008-05-03
forum: General Help
---

### Post by b0ng0 on 2008-05-03
I have just installed Hardy and after restarting, none of my other partitions (apart from swap and the ubuntu one) are mounted. How can I get them to mount everytime I start up into ubuntu? They are NTFS partitions btw.

Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5b122d67-79ff-4a67-9aa7-ccb7980d7cdb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=023029b7-39c4-4a04-93b3-faabe4dd8c7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



Thank you.

---

### Post by DaddyX3 on 2008-05-03
post your: 
```
sudo fdisk -l
```
paste back here.

---

### Post by b0ng0 on 2008-05-04
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440088+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7650       19131    92229165    7  HPFS/NTFS
/dev/sda3           19132       20023     7164990    5  Extended
/dev/sda5           19132       19896     6144831   83  Linux
/dev/sda6           19897       20023     1020096   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x8baf2b92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      484521   244198552+  42  SFS


Thanks

---

### Post by DaddyX3 on 2008-05-04
Before you change your fstab file to the following, do a 
```
cp /etc/fstab /etc/fstab_backup
```


First you will need to create mount points in your /media directory (most common). So you should issue a command to create them, like this: 

```
sudo mkdir /media/sda1 /media/sda2 /media/sda3 /media/sdb1
```

Then go ahead and open up your fstab file and erase everything (after your backup!!!!) and paste the following in. 
It should look something like this: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=5b122d67-79ff-4a67-9aa7-ccb7980d7cdb / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=023029b7-39c4-4a04-93b3-faabe4dd8c7b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/sda1    defaults   ntfs   0  2
/dev/sda2 /media/sda2    defaults   ntfs   0  2
/dev/sda3 /media/sda3    defaults   ntfs   0  2
/dev/sdb1 /media/sdb1    defaults   ntfs   0  2


```
Now save your fstab file before closing. Reboot your computer and see what happens:)
Good Luck! If you run into trouble post back here and I'll see what we can do about it.

---

### Post by b0ng0 on 2008-05-06
Hmm okay now when I rebooted and try to load the partitions it doesn't even mount them and says "You do not have permissions to mount this partition" :confused:

---

### Post by dbrine on 2008-05-06
I'm not an expert but, you could try chmod 0777 /media/sdb1, do this for all the partions

---

### Post by vanadium on 2008-05-06
Probably, your drives are already mounted. You can access them navigating to /media/sda1, sda2, etc.

For convenient access, you might want to create symbolic links to these drives from within your home directory, for example:

cd
ln -s /media/sda1 mydata

will let you access /media/sda1 right by navigating to "mydata" in your home directory.

To enable write support on these drives, in /etc/fstab, replace "ntfs" with "ntfs-3g" for these drives where you want write support.

---

### Post by didac on 2008-05-06
Instead of the following lines in /etc/fstab

/dev/sda1 /media/sda1    defaults   ntfs   0  2
/dev/sda2 /media/sda2    defaults   ntfs   0  2

write this:

/dev/sda1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       0
/dev/sda2 /media/sda2     ntfs    defaults,umask=007,gid=46 0       0

umask will make these partitions writable. The last zero in each line indicates "don't check the hard disks when booting." I like it that way. If you don't feel comfortable, write 2

Also, if you like changing hard disks -- I love it, just my personal mania -- better use UUID instead of the device name. To get UUID type in a terminal

blkid

Mine says:

/dev/sda1: UUID="58C03290C032747A" LABEL="XP" TYPE="ntfs" 
/dev/sdb1: UUID="68d7a351-fc99-4d0f-838c-bd8c8ef4d52c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="6e5b4e05-7b33-46e3-9b08-b56fb15bb51c" 
/dev/sdb3: LABEL="DIDAC" UUID="A4CE-AADD" TYPE="vfat" 

Now substitute /dev/sda1 in fstab for the UUID without inverted commas, like this:

UUID=58C03290C032747A /media/sda1     ntfs    defaults,umask=007,gid=46 0       0

By now you'll be able to see the hard disks on the Desktop, with the volume label under the icons. If not, launch gconf-editor from the terminal. Navigate to /apps/nautilus/desktop and in the right panel check volumes_visible

Hope it helps

---

### Post by b0ng0 on 2008-05-06
Thanks. I know they're not mounted on startup because they appear as little USB icons in the Places menu and when I click on them to open them, it changes to a mounted drive icon. Never had this problem with previous versions of buntu :p

---

### Post by vanadium on 2008-05-06
To check what is wrong with your current fstab, execute the command

sudo mount -a

and post the output here.

---

### Post by b0ng0 on 2008-05-06
mount: unknown filesystem type 'defaults'
mount: unknown filesystem type 'defaults'
mount: unknown filesystem type 'defaults'
mount: unknown filesystem type 'defaults'

Thanks

---

### Post by wrgb2 on 2008-05-06
I'm no expert, but I used the NTFS Configuration Tool (Applications>Add/Remove>System Tools>NTFS Configuration Tool, will install to Applications>System Tools>NTFS Configuration Tool).  After using this utility to specify which partitions to mount on startup, they are mounted automatically on startup.

---

### Post by vanadium on 2008-05-07
You did not follow up on the advise of didac. DaddyX3 made a slight mistake in proposing the changes to your /etc/fstab. didac corrected this and proposed to add some more options.

In my opinion, there is no need for the gid and umask options. I support the suggestion to change "2" to "0", though: if you must use ntfs, you should also have MS Windows and perform the disk checking there.

If you want write support, you must use the ntfs-3g driver (the uid option does not serve that purpose). Thus, the relevant lines might be changed to

```

/dev/sda1 /media/sda1 ntfs-3g defaults 0 0
/dev/sda2 /media/sda2 ntfs-3g defaults 0 0

```

Apply the changes, then execute "mount -a" to check if it is all OK (you can also reboot if you prefer). If the command does not produce an error, you should be able to navigate to the drives through the /media directory. Moreover, an icon will appear on your desktop because you mounted under /media.

As a further step, you might follow the advice of didac to mount using the UUID because on some systems, the device names might change between different reboots.

---

### Post by DaddyX3 on 2008-05-07
Well, at least you guys came in to give a hand :) I don't even have a ntfs drive anymore :) Haven't had to deal with Windows in quite a while. I will remember the whole "ntfs-3g" thing.

-b0ng0, I'm very sorry I got you mixed up on the order of things in your fstab. It should have been listed as drive type first then defaults. Like vanadium has said it should be listed as;
```
/dev/sda1  /media/sda1  ntfs-3g defaults 0  0#or 2 if you want it checked
/dev/sda2  /media/sda2  ntfs-3g  defaults  0  0
```
--once again, sorry for the confusion. And thanks for clearing it up vanadium.

---

