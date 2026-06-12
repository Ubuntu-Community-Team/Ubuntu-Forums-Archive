---
title: "3 HDDs"
date: 2007-05-29
forum: General Help
---

### Post by nami on 2007-05-29
If you look at the screenshot below, you will notice that I have 3 HDDs but only 1 of them is mounted.  Why don't the other 2 get mounted when I login?

---

### Post by tszanon on 2007-05-29
> **nami said:**
> If you look at the screenshot below, you will notice that I have 3 HDDs but only 1 of them is mounted.  Why don't the other 2 get mounted when I login?
Check /etc/fstab. Probably:
1. The other 2 drives are not listed there;
2. The mount point indicated does not exist.

---

### Post by nami on 2007-05-29
I just installed the harddrives and formattted them as ex3.  shouldn't they mount automatically, or so i have to manually set them up to mount automatically?

---

### Post by stchman on 2007-05-29
> **nami said:**
> If you look at the screenshot below, you will notice that I have 3 HDDs but only 1 of them is mounted.  Why don't the other 2 get mounted when I login?

Edit your fstab file.  I have a mini tutorial here:

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Once you edit the fstab file, reboot.  You will then have your HDDs mounted.

---

### Post by tszanon on 2007-05-29
> **nami said:**
> I just installed the harddrives and formattted them as ex3.  shouldn't they mount automatically, or so i have to manually set them up to mount automatically?
No. Since the disks were installed after Ubuntu installation, they are not mounted automatically.
Follow the above tutorial to edit your /etc/fstab file and everything shall work fine.

---

### Post by nami on 2007-05-31
thanks, i'll try this out tonight hopefully.

---

### Post by nami on 2007-06-01
ok i tried it out and restarted the computer.  the hdd's mounted automatically but i can't write to them.  here is a screenshot showing the 2 drives on the desktop hdd2 and hdd3 and when i right click on the drive and create a new folder, you can see that option is grayed out so i can't selected it.

why can i not use those drives?

[[IMG]http://img463.imageshack.us/img463/4253/screenshot1ve7.th.png[/IMG]](http://img463.imageshack.us/img463/4253/screenshot1ve7.png)

---

### Post by jimbob on 2007-06-01
Please post your /etc/fstab file.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by nami on 2007-06-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=15163f8a-00c8-4d45-a46e-333fd883bf0a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3f45d2c7-7c4f-49df-a3b5-66be617c953c none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/HDD2 ext3  auto,defaults,rw  0   0
/dev/hdb1       /media/HDD3 ext3  auto,defaults,rw  0   0

---

### Post by jimbob on 2007-06-02
Try changing the fstab lines to this:

  dev/hda1 /media/HDD2 ext3 auto,rw,users,umask=000  0 0
  dev/hdb1 /media/HDD3 ext3 auto,rw,users,umask=000  0 0
 
Also, make sure that the mount points have full rwx privileges:

  chmod -R 777 /media

Re-boot and give it a try.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by nami on 2007-06-02
I tried the command:

> nami@nami-desktop:~$ chmod -R 777 /media

and it was not happy as it returned:

> chmod: changing permissions of `/media': Operation not permitted
chmod: changing permissions of `/media/.hal-mtab-lock': Operation not permitted
chmod: changing permissions of `/media/cdrom0': Operation not permitted
chmod: changing permissions of `/media/floppy0': Operation not permitted
chmod: changing permissions of `/media/iso': Operation not permitted
chmod: changing permissions of `/media/.hal-mtab': Operation not permitted
nami@nami-desktop:~$ 

---

### Post by jimbob on 2007-06-02
Sorry, you'll have to use sudo in front of those commands ...

---

### Post by nami on 2007-06-02
i tried that and now it's not mounting the hdds at all...

---

### Post by jimbob on 2007-06-02
Can you mount them manually and write to them?  Try:

[COLOR="RoyalBlue"]sudo mount /dev/hda1 /media/HDD2[/COLOR]

Post the output of [COLOR="RoyalBlue"]ls -al /media[/COLOR] please.  

Do you have any boxes checked under System->Preferences->Removable Drives & Media->Removable Storage?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by tszanon on 2007-06-02
> **nami said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=15163f8a-00c8-4d45-a46e-333fd883bf0a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3f45d2c7-7c4f-49df-a3b5-66be617c953c none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/HDD2 ext3  auto,defaults,rw  0   0
/dev/hdb1       /media/HDD3 ext3  auto,defaults,rw  0   0
My fstab looks like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           reiserfs notail          0       2
/dev/md1        /home           ext3    defaults        0       2
/dev/sdc1       /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
**/dev/sdc5       /media/sdc5     ext3    defaults**        0       2
/dev/md2        none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Maybe now you can mount automatically and have write access to the partitions?

---

