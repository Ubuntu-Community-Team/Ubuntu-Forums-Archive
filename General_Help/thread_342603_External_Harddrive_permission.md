---
title: "External Harddrive permission"
date: 2007-01-20
forum: General Help
---

### Post by Lowfront on 2007-01-20
Alright on my external harddrive I don't have the ability to write to it.  I just reformated it from ntsf to ext 2 so I could write to it.  And now I can't

---

### Post by taurus on 2007-01-20
Where did you mount that external harddrive?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Lowfront on 2007-01-20
lowfront@lowfront-x60:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  3.4G  5.8G  37% /
varrun                502M  144K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shmlowfront@lowfront-x60:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  3.4G  5.8G  37% /
varrun                502M  144K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   18M  484M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda6              31G   23G  7.1G  76% /Media
/dev/sda5              31G  1.2G   29G   4% /home
/dev/sdb5              22G  6.6G   15G  31% /media/ACRONIS SZ
/dev/sdb2             7.8G  6.9G  829M  90% /media/FAT32
/dev/sdb1             201G   17G  174G   9% /media/Media

lrm                   502M   18M  484M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda6              31G   23G  7.1G  76% /Media
/dev/sda5              31G  1.2G   29G   4% /home
/dev/sdb5              22G  6.6G   15G  31% /media/ACRONIS SZ
/dev/sdb2             7.8G  6.9G  829M  90% /media/FAT32
/dev/sdb1             201G   17G  174G   9% /media/Media





the 201 g /media/Media     is the one with the problem all the other partitions on the external work fine.

---

### Post by taurus on 2007-01-20
And you're sure /dev/sdb1 is ext2, right!

```
sudo chown -R **username**:**username** /media/Media
sudo chmod -R 755 /media/Media
```
(Replace **username** with your actual **username** that you log in with.)

Now, see if you can write to /media/Media.  Or reboot after those two commands if you want.

---

### Post by Lowfront on 2007-01-20
Thanks so much!!!

---

### Post by altonbr on 2007-01-22
Didn't work for me. Says mine is a read-only file system. I think it's Fat32.

---

### Post by taurus on 2007-01-22
> **altonbr said:**
> Didn't work for me. Says mine is a read-only file system. I think it's Fat32.

Can't change permission or ownership for ntfs or fat32.  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Sirhanz on 2007-03-24
I get 

root@Office:/media/sdf1# sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+  83  Linux
/dev/sda2   *       12749       24906    97659135   83  Linux
/dev/sda3           29958       30401     3566430    5  Extended
/dev/sda5           29958       30401     3566398+  82  Linux swap / Solaris

Disk /dev/sdf: 5000 MB, 5000970752 bytes
255 heads, 63 sectors/track, 608 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         608     4883728+   b  W95 FAT32

SDF1 is the drive I am getting read only access messages for. I have tried all steps listed. This is a iRiver H10, I am trying to put Rockbox on it because i dont use Winblows anymore, but i cant change the H10.MI4 file name. Please help!:confused:

---

### Post by Norrbagge on 2007-10-20
> **taurus said:**
> And you're sure /dev/sdb1 is ext2, right!

```
sudo chown -R **username**:**username** /media/Media
sudo chmod -R 755 /media/Media
```
(Replace **username** with your actual **username** that you log in with.)

Now, see if you can write to /media/Media.  Or reboot after those two commands if you want.

I JUST FUCKIN LOVE YOU MAN... holy ****... i am sitting here tired as hell, my eyes hurt and i am starving... been fuckin around with my internal 2nd ext3 harddrive for, i dont know how many hours (atleast 5+hrs)... FINALLY, i found your post. and thank "insert whatever god" i tried it... Now i FINALLY have read/write permission too it... 

i just want to add that i used this one on a internal hard drive on a Ubuntu 7,10 Gutsy installation... So if you have formatted your extra harddrive to ext3 (dont know if it works with extra partitions) and dont have read/write permission. then use his code... atleast for me it worked like a charm... its fuckin amazing... 

now i can finally move on... :guitar:

thanks a million, again... this made me so happy (even though the code was to help someone else)... Only let down now is that i have to drive my girfriend to work in a about 5hrs...

---

### Post by zmjjmz on 2007-10-22
I'm having the same problem...
I have an external LaCie, which is NTFS, (so I can't really write to it...), but I've tried installing the ntfs-config thing, and after rebooting many times, I still can't write to it, even as root...

Just in case it helps, from sudo fdisk -l, I get 
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075091

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```
the filesystem is /dev/sdb6, just incase that's also necessary...

---

