---
title: "password problems"
date: 2014-06-18
forum: General Help
---

### Post by bance2 on 2014-06-18
I've just done a fresh install of 14.04. When I edit fstab to mount my backup /home partition it won't let me login....

```
john@john-desktop:~$ sudo blkid -c /dev/null
[sudo] password for john:
/dev/sda1: UUID="48ff11e8-ce5d-470d-b890-556990d0f600" TYPE="ext4"
/dev/sda3: LABEL="/Home" UUID="34432829-1d0b-404f-b780-e75cfbc9ecca" TYPE="ext4"
/dev/sda5: UUID="09c01832-9e3a-4438-aafd-9b58a620f702" TYPE="swap"
/dev/sdb1: LABEL="New Volume" UUID="0EEE-2817" TYPE="vfat" 
```

```
john@john-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008db37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   102402047    51200000   83  Linux
/dev/sda2       621473790   625141759     1833985    5  Extended
/dev/sda3       102402048   621471743   259534848   83  Linux
/dev/sda5       621473792   625141759     1833984   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8153 MB, 8153726976 bytes
251 heads, 62 sectors/track, 1023 cylinders, total 15925248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097402

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15919925     7959932    c  W95 FAT32 (LBA)

```

fstab that works ;-

```
john@john-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=48ff11e8-ce5d-470d-b890-556990d0f600 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=09c01832-9e3a-4438-aafd-9b58a620f702 none            swap    sw              0       0
# mount /home partition
```

fstab that doesn't work:-

```
john@john-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=48ff11e8-ce5d-470d-b890-556990d0f600 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=09c01832-9e3a-4438-aafd-9b58a620f702 none            swap    sw              0       0
# mount /home partition
UUID=34432829-1d0b-404f-b780-e75cfbc9ecca /home    ext4    defaults    0    2
```

If I mount the partition at a different place...  /[COLOR=#ff0000]H[/COLOR]ome for example, then no problem I can log in. However then i have two "home" directories, I suppose I could symlink one to the other but I don't think that's the right way to do it!

Incidently this is my father's PC he's pushing 80 years old, I persuaded him to come over to the darkside about 5 years ago HEH HEH.

---

### Post by bapoumba on 2014-06-18
There cannot be two /home partitions.
If you want a storage area, you have to name it differently.

I suppose your user /home partition has been set up in the / (root system file) partition /dev/sda1. Your backup or storage area is /Home on /dev/sda3. Linux is case sensitive and thus sees it as a different partition that can be mounted as such. To have your second fstab work, you have to mount it as /Home.

---

### Post by bance2 on 2014-06-18
Thank's for the reply bapoumba,

I understand that there can't be two directories with the same name, which is why I named the back-up /Home rather than /home, what I want to do is mount the backed-up partition /Home at the mount point /home.

As I wrote the sentence above I realised how my first post may be confusing.... (back-up as opposed to backed up.)

My dad was using 10.04 and a recent update borked his set up, not surprising since 10.04 is EOL, I suppose to some extent it's my fault because I told him not to upgrade his distro just update.

 Anyway the upshot is that the consensus on fixing the 10.04 problem is a fresh install. I backed up his /home to a thumb drive and named it /Home.

I did a fresh install of 14.04 but during the install process I accepted the standard fresh install not realising that I wouldn't have the option to re-size partitions etc. So I had to use GParted to create the /Home partition, I then copied the data on the thumbdrive to the /Home partition.

When I mount the /Home partition at /home does that prevent the OS/kernel "seeing" authourisation files ot something?

Is that why I can't log in (user name and password are identical)?

Thanks for your help.

Steve.

---

### Post by steeldriver on 2014-06-18
To log in (at least, to log in to a graphical X session) a user's home directory as listed in the /etc/passwd file must exist and be owned and writeable by that user - if your backup messed with the ownership or permissions on your dad's original home dir (for example if you used a FAT or NTFS formatted thumb drive) then you will need to fix those before he can log in again. It's not always sufficient for the username to be the same since the actual underlying mapping relies on the numeric UID value.

If you mount it at /Home for the moment and then do

```

ls -l /Home

```

we can start to see what needs to be fixed

---

### Post by bance2 on 2014-06-18
steeldriver thank's for the reply,

Here is the output

```
john@john-desktop:~$ ls -l /Home
total 20
drwx------ 3 john john  4096 Jun 18 16:11 home
drwx------ 2 john john 16384 Jun 17 19:13 lost+found
```

I have to say at this point that I changed the ownership and permissions of /Home to match those in /home, at  least I thought I did, I just checked /Home and /home, and of course the permissions are not quite the same:-

```
john@john-desktop:~$ ls -l /home
total 4
drwxr-xr-x 19 john john 4096 Jun 18 18:12 john

```

Before I make anymore changes I'll wait for your reply!

Thank's for the help,

 Steve.

---

### Post by steeldriver on 2014-06-18
Hmm so it looks like it's more a question of directory structure than permissions - presumably /Home/home contains a directory /Home/home/john containing the original user files, so that when you mount that as /home you end up with /home/home/john instead of just /home/john which is what the system expects

---

### Post by bance2 on 2014-06-18
That look's like it.....

Got any idea how to remove the extra /home? Or do I need to just make a copy of /john.... on the thumbdrive and then remove all files from /Home, then copy /john back to /Home?

Is there an easier way to do it?

Thanks a bundle.... 

Thats what I love about linux you learn something new every day..... and if it's broke you can fix it!

Steve.

---

### Post by steeldriver on 2014-06-18
I think you should just be able to move everything below /Home/home up one level, then (optionally) delete the (now empty) /Home/home

[if you're currently logged in as john some of these will not actually need sudo]
```

sudo mv /Home/home/* /Home/

sudo rmdir /Home/home

```
[if the drive has enough free space you could COPY the contents up one level and NOT delete the original /Home/home until you are sure everything's working]

There should then be a /Home/john directory with ownership and permissions like

```

ls -l /Home
drwxr-xr-x 90 john john 12288 Jun 18 08:33 /Home/john

```

If it doesn't have the correct ownership/permissions then now is the time to change them e.g.

```

sudo chown john:john /Home/john

sudo chmod -R u,g=rwX,o=rX /Home/john

```
[note the UPPERCASE X]

If you have other user home dirs on the partition they will need to have their ownerships and permissions set as appropriate. 

Then your plan to unmount and mount the partition as /home instead of /Home *should* work.

---

### Post by bance2 on 2014-06-19
Thanks steeldriver worked like a treat.....

Just one more thing I'd like to do, I've got a desktop launcher for trash, which seems to be a remnant from the gnome desktop. Any idea which file I need to edit to get rid of it?

---

