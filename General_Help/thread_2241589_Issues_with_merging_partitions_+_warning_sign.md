---
title: "Issues with merging partitions + warning sign"
date: 2014-08-27
forum: General Help
---

### Post by charitosha on 2014-08-27
Hello everyone.
After installing ubuntu (12.04) i realized that i haven't booted into windows for months, thus i formated the partition that windows were.
When i checked my partitions via gparted  (to merge the partitions) i saw that something was off and decided to ask you before proceeding any further.

So i attached the gparted pic so you'll see my partitions. /dev/sda1 was the one i formated, /dev/sda2 is were linux is. As you can see there is a warning sign on the linux partition, i'll attach it as well. Besides the warning this partition is unmounted as also is /dev/sda1.

The warning on the sda2 partition was because of lack of space, right?
How come and those tow partitions are unmounted??
And of course, what should i do now???

Hope that explained the situation well

[ATTACH=CONFIG]255870[/ATTACH][ATTACH=CONFIG]255871[/ATTACH][ATTACH=CONFIG]255872[/ATTACH]

---

### Post by Impavidus on 2014-08-27
sda1 is far too small to be your former Windows partition, but, seeing it still has a boot flag, I assume it was your former Windows boot partition. sda2 is your old Windows partition. Windows partitions are of type ntfs whereas Linux partitions are of type ext4. So sda5 is your Linux partition from which you are running Ubuntu right now and sda6 is your swap partition, also belonging to Linux. The warning sign on sda2 indicates it couldn't be mounted. This suggests it is damaged and may require Windows tools to fix it.

There are some ways to fix ntfs partitions from Linux, but I don't really know about them and they only fix small problems. Else you'll need to attach this hard drive to a working Windows box and run the file system checks from there.

If you want to get rid of Windows and know for sure there are no files on sda2 that you want to keep (I hope you already have backups of things you want to keep), the easiest thing to do is delete sda1 and sda2 and create a new ext4 partition in their place. Then migrate your /home directory to the new partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

BTW, Ubuntu 12.04 LTS will still be supported for a while so it's OK, but there is also a more recent LTS release of Ubuntu, 14.04. Any particular reason why you still installed 12.04?

---

### Post by charitosha on 2014-08-27
Oh you're right sda5 is the partition where linux are, my bad...
I'll try to migrate the /home directory as it's mentioned in the link. Already deleted sda1 and sda2 and made them one ext4 primary partition. 

About 12.04 LTS. I've been using 12.04 for a year, don't quite remember if 14.04 was out, think it was 13th version and it wasn't LTS. Well in the future i might upgrade to 14.04, hope that while upgrading versions i will note lose any files and folders...

---

### Post by charitosha on 2014-08-27
I need a bit of more help. I don't understand something from this guide:[https://help.ubuntu.com/community/Partitioning/Home/Moving#Technical_Notes_and_Resources](https://help.ubuntu.com/community/Partitioning/Home/Moving#Technical_Notes_and_Resources)
i'm stuck at the Setup Fstab part
first of all when i type:
```
sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
```
and 
```
cmp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)
```
nothing happens, no windows opens or anything else.

and also what defaults 0 and 2 mean here and are the necessary: 
```
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /media/home    ext3          defaults       0       2 
```

---

### Post by Impavidus on 2014-08-27
> **charitosha said:**
> About 12.04 LTS. I've been using 12.04 for a year, don't quite remember if 14.04 was out, think it was 13th version and it wasn't LTS. Well in the future i might upgrade to 14.04, hope that while upgrading versions i will note lose any files and folders...
That's OK. I assumed continuity of time, place and action in the first full sentence of your first post, and therefore that you had recently installed Ubuntu.
> **charitosha said:**
> 
nothing happens, no windows opens or anything else.That is to be expected. **cp** doesn't say anything when it succeeds copying a file, only when there is an error. **cmp** only says something when the files are not identical, so you're good to go. Most command line tools only say something when there is an error. To be really sure, you can run```
cmp file1 file2 ; echo $?
```It will return 0 if both files are identical.
> and also what defaults 0 and 2 mean here and are the necessary: 
```
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /media/home    ext3          defaults       0       2 
```
**defaults** means that the partition should be mounted with the default options. Those are:
**rw**: Mount in read-write mode.
**suid**: Allow set user ID and set group ID bits on this partition.
**dev**: Interpret character or block special devices.
**exec**: Allow execution of binaries.
**auto**: Automount at boot.
**nouser**: Only allow mounting and unmounting by root.
**async**: Use asynchonous I/O.
For more details, read **man fstab** and **man mount**. These defaults are good.

The 0 means it doesn't have to be dumped (in case of certain errors I assume) and the 2 means that it should be checked after the root partition when file systems have to be checked at boot. These settings are fine too.

You probably have to change the ext3 in ext4.

---

### Post by charitosha on 2014-08-28
guess i will need some additional help...
from the terminal:
```
haris@Mini-210:~$ gksu gedit /etc/fstab
haris@Mini-210:~$ sudo mkdir /media/home
haris@Mini-210:~$ sudo mount -a
mount: mount point /dev/sda1 is not a directory
```

as you can see i got that /dev/sda1 is not a directory. 
perhaps it because of false editing the fstab file. This is what i added and saved:

UUID=95f5e1ba-666e-4709-9cbb-1e2eeea06fba /dev/sda1  ext4  defaults 0 2

perhaps should just have written /sda1 instead of /dev/sda1 or not write it at all?

Anyhow just for reference this is how the fstab file was before me adding the line:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=934cb3ca-9bb8-4fe5-b9fb-91776b0b6619 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cebb6afd-99e2-4cfc-b3aa-4750b5543d46 none            swap    sw              0       0

Anyway i will wait for a reply before doing anything because don't want to mess anything....

---

### Post by Impavidus on 2014-08-28
That should be```

UUID=95f5e1ba-666e-4709-9cbb-1e2eeea06fba /media/home  ext4  defaults 0 2

```The UUID=xxxxx part says which partition must be mounted, the /media/home part says where it has te be mounted. /dev/sda1 is the partition itself, not its mountpoint. The UUID is an alternative way to label the partition and is sometimes more reliable than using /dev/sda1.

---

### Post by charitosha on 2014-08-28
i was able to mount it, how ever after entering this code: 
```
sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/.
```
i got a whole list in what it differs also tried the line:cmp file1 file2 ; echo $?, that you mentioned 
got in response the number 2 if remember correctly....

Anyhow i'll post my gpatred pic, maybe it'll help

---

### Post by Impavidus on 2014-08-28
So you ran rsync, which didn't return any error messages, and then ran```
sudo diff -r /home /media/home
```which gave a lot of differences? cmp isn't useful here, as it only compares files, not entire directories.

What differences does diff give you? It seems there are 6GiB on sda1 (some of which is overhead). Can you see all your files there (in /media/home at this moment)?

---

### Post by charitosha on 2014-08-28
As you said i ran rsync and it didn't return any errors.
i got the errors when i run :
```
sudo diff -r /home /media/home
```
so, firstly there was:
```

Only in /media/home: bin
Only in /media/home: boot
Only in /media/home: cdrom
Only in /media/home: dev
Only in /media/home: etc
Only in /home/haris/adt_bundle: adt-bundle-linux-x86-20140321
diff -r /home/haris/.bash_history /media/home/haris/.bash_history
626,627d625
< sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/.
< sudo diff -r /home /media/home

```

However i rebooted my netbook, at the ubuntu loading screen, there was an error saying that could not mount, among other things it said press S to skip, so i skiped it.
When i did again the sudo diff line the only responce was:
```

haris@Mini-210:~$ sudo diff -r /home /media/home
[sudo] password for haris: 
Only in /home: haris

```

Lastly, i cannot see anymore the files in /media/home
the response is:
```

Failed to mount "205 GB Filesystem"

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/home

```

---

### Post by Impavidus on 2014-08-29
> **charitosha said:**
> 
```

Only in /media/home: bin
Only in /media/home: boot
Only in /media/home: cdrom
Only in /media/home: dev
Only in /media/home: etc
Only in /home/haris/adt_bundle: adt-bundle-linux-x86-20140321
diff -r /home/haris/.bash_history /media/home/haris/.bash_history
626,627d625
< sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/.
< sudo diff -r /home /media/home

```Where did /media/home/{bin,boot,cdrom,dev,etc} come from? You started with a fresh and empty partition and only copied files and directories there with rsync from /home. These directories come from /. Maybe you inserted an extra space and killed it when you saw the error? The adt-bundle file must have been added after you ran rsync and the differences in .bash_history are caused because you closed the terminal and opened a new one to run diff again.

> However i rebooted my netbook, at the ubuntu loading screen, there was an error saying that could not mount, among other things it said press S to skip, so i skiped it.
When i did again the sudo diff line the only responce was:
```

haris@Mini-210:~$ sudo diff -r /home /media/home
[sudo] password for haris: 
Only in /home: haris

```

Lastly, i cannot see anymore the files in /media/home
the response is:
```

Failed to mount "205 GB Filesystem"

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/home

```That is because the system couldn't mount sda1. You told it to  skip, so now /media/home appears as an empty directory. Which makes me  wonder how you mounted it the first time. Something must be wrong with your fstab.

Let's go back a few staps. Run these commands and post their output:```
sudo blkid
cat /etc/fstab
```Then we can fix your fstab so that it mounts sda1 at the temporary mountpoint /media/home. Next we'll wipe it clean and run rsync again and then continue following the tutorial.

---

### Post by charitosha on 2014-08-30
> Maybe you inserted an extra space and killed it when you saw the error?
well i don't think that i added an extra space

> The adt-bundle file must have been added after you ran rsync
I haven't installed anything for at least a month, and specifically the adt-bundle is almost one year old

> the differences in .bash_history are caused because you closed the terminal and opened a new one to run diff again
this is true.

```

haris@Mini-210:~$ sudo blkid
[sudo] password for haris: 
/dev/sda1: UUID="95f5e1ba-666e-4709-9cbb-1e2eeea06fba" TYPE="ext4" 
/dev/sda5: UUID="934cb3ca-9bb8-4fe5-b9fb-91776b0b6619" TYPE="ext4" 
/dev/sda6: UUID="cebb6afd-99e2-4cfc-b3aa-4750b5543d46" TYPE="swap" 

```

```

haris@Mini-210:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=934cb3ca-9bb8-4fe5-b9fb-91776b0b6619 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cebb6afd-99e2-4cfc-b3aa-4750b5543d46 none            swap    sw              0       0
UUID=95f5e1ba-666e-4709-9cbb-1e2eeea06fba /media/home  ext4  defaults 0 2

```

the last UUID is the one that i added as i read from the tutorial.

---

### Post by Impavidus on 2014-08-30
Your fstab looks perfect. So let's redo the rsync (as something went wrong there). Execute these commands:```
#Mount sda1 at /meda/home, if you hadn't done so already
sudo mount -a

#Clear the contents of sda1. Careful, a typo here can have serious consequences.
sudo rm -rf --one-file-system /media/home

#Copy your /home directory to /media/home
sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/.

#Check the copy
sudo diff -r /home /media/home
```In case of any errors (except some errors by rsync if it appears to have problems with some files or directories, but copies everything important), stop and report the error.

If you feel confident, you can continue with the swap:```
#Edit /etc/fstab to change /media/home into /home
gksu gedit /etc/fstab
#Alternatively you can use a different text editor, but you need root permissions.

#Rename the old home into old_home and create a fresh mountpoint for the /home partition
cd / && sudo mv /home /old_home && sudo mkdir /home

#Mount the home partition
sudo mount -a
```Don't do anything else between those last two commands. Also, don't reboot between editing fstab and the other commands.

In case something went wrong, you can still access the old home directory at /old_home. Once everything works, you can delete it.

---

### Post by charitosha on 2014-08-30
Hey Impavidus what exactly should i type instead --one-file-system from the ```
sudo rm -rf --one-file-system /media/home
```
Should it be sda1? it's UUID? or what exactly, because as i understand the point is to delete everything that's in sda1, right?
I'm asking because rm -rf, as i read from the net, is a bit of serious stuff, deletes everything and all that...

The reply from ```
sudo mount -a
``` is:
```

haris@Mini-210:~$ sudo mount -a
[sudo] password for haris: 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

haris@Mini-210:~$ dmesg | tail
[ 3802.812499] r8169 0000:03:00.0: PME# enabled
[ 3802.995133] r8169 0000:03:00.0: PME# disabled
[ 3803.204767] r8169 0000:03:00.0: eth0: link down
[ 3803.204806] r8169 0000:03:00.0: eth0: link down
[ 3803.207253] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3804.836443] r8169 0000:03:00.0: eth0: link up
[ 3804.837054] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3815.426049] eth0: no IPv6 routers present
[ 3868.451378] EXT4-fs (sda1): ext4_check_descriptors: Checksum for group 8288 failed (50689!=0)
[ 3868.451389] EXT4-fs (sda1): group descriptors corrupted!

```

---

### Post by Impavidus on 2014-08-30
> **charitosha said:**
> Hey Impavidus what exactly should i type instead --one-file-system from the ```
sudo rm -rf --one-file-system /media/home
```
Should it be sda1? it's UUID? or what exactly, because as i understand the point is to delete everything that's in sda1, right?
I'm asking because rm -rf, as i read from the net, is a bit of serious stuff, deletes everything and all that...Nothing, just use the --one-file-system verbatim. You can copy-paste it into your terminal. I don't think you really need it, but it's just to be sure it will only delete files on that partition. But first we have to solve a different problem:> 
The reply from ```
sudo mount -a
``` is:
```

haris@Mini-210:~$ sudo mount -a
[sudo] password for haris: 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

haris@Mini-210:~$ dmesg | tail
[ 3802.812499] r8169 0000:03:00.0: PME# enabled
[ 3802.995133] r8169 0000:03:00.0: PME# disabled
[ 3803.204767] r8169 0000:03:00.0: eth0: link down
[ 3803.204806] r8169 0000:03:00.0: eth0: link down
[ 3803.207253] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3804.836443] r8169 0000:03:00.0: eth0: link up
[ 3804.837054] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3815.426049] eth0: no IPv6 routers present
[ 3868.451378] EXT4-fs (sda1): ext4_check_descriptors: Checksum for group 8288 failed (50689!=0)
[ 3868.451389] EXT4-fs (sda1): group descriptors corrupted!

```Somehow the partition became corrupted. That's something that has never happened to me. Maybe running fsck can fix it```
sudo fsck /dev/sda1
```Or the easy way, as we want that partition empty anyway, you can delete it and create a new partition. If you do that the UUID will change though, so you'll have to modify your fstab again for the new UUID.

File system damage on a partition where you haven't really done anything is uncommon. Let's hope it's nothing serious.

---

### Post by charitosha on 2014-09-05
Ok Impavidus I managed to mount my partition! Thank you for the info!!

So, what happened so far:
```
haris@Mini-210:~$ sudo fsck /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Group descriptors look bad... trying backup blocks...
One or more block group descriptor checksums are invalid.  Fix<y>?
Group descriptor "5-digit-number" checksum is invalid.  FIXED.
Pass 1: Checking inodes, blocks, and sizes
Group 1's inode table at 546 conflicts with some other fs block.
Relocate<y>? 
```

Didn't want to relocate, because don't know if it'll mess up with the "healthy" partition.
So, via gparted, i tried to delete the partition. When clicked "Apply All Operation" that's the reply i got:
```

An error occurred while applying the operations
See the details for more information.

IMPORTANT
If you want support, you need to provide the saved details!
See http://gparted.org/save-details.htm for more information.
```

Afterwards the only file system available for this partition is:unformatted (for now i kept it unallocated).
Here are the details of the error from the gparted:
```


GParted 0.11.0 --enable-libparted-dmraid

Libparted 2.3
Delete /dev/sda1 (ext4, 190.87 GiB) from /dev/sda  00:00:03    ( ERROR )
         
calibrate /dev/sda1  00:00:01    ( SUCCESS )
         
path: /dev/sda1
start: 2,048
end: 400,279,551
size: 400,277,504 (190.87 GiB)
delete partition  00:00:02    ( ERROR )
libparted messages    ( INFO )
         
Partition(s) 1 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) will remain in use. You should reboot now before making further changes.

```

Anyway, I rebooted and then i was able to format it in ext4 as primary partition.
Changed it's UUID in the fstab, made the new directory /media/home.
The code:
```
sudo mount -a
```
didn't reply anything.

From gparted I can see that the partition is now mounted on /media/home!!!

---

### Post by Impavidus on 2014-09-05
Great. The partition should be empty now, with the possible exception of a lost+found directory. You can resume the tutorial from (including) the sudo rsync command.

---

### Post by charitosha on 2014-09-05
I was so happy that i could mount that partition that i completely forgot about the tutorial....
Anywayzzzz ](*,)
I resumed the tutorial from (including) the sudo rsync command. Everything went well except of 2 things:
i couldn't delete the old_home directory(the last step):
```
haris@Mini-210:/$ sudo rm -r /old_home
rm: cannot remove `/old_home/haris/.gvfs': Is a directory

```
And the second is that from gparted i see that /dev/sda1 is still mounted in 2 points. In /home and in /media/home, although i edited the fstab file and changed the location from /media/home to /home

---

### Post by Impavidus on 2014-09-06
The second thing should be solved when you have rebooted. About the first, I don't know why rm -r doesn't want to remove a directory. I'm not really familiar with the .gvfs directory either. Could have something to do with encrypted stuff mounting there. Have you tried after rebooting?

---

### Post by charitosha on 2014-09-06
So, the second thing was solved when I switched on the netbook today, as also the deletion of old_home directory...
I guess have to learn to keep my frustration at low when working with this kind of stuff...

P.S. Impavidus, out of topic question: Is it possible to mount a cd-driver on a laptop via modifying the fstab file, and using some necessary lines of code in the terminal?

---

### Post by Impavidus on 2014-09-06
Some things were still mounted at the old locations, but they were all unmouted at shutdown and not remouted at boot because you had changed your fstab.

What you mount is a device containing a file system (or a file containing a file system, really, but every device is a file). So what you mount is the cd, addressing it via the drive, as only the combination of a drive with a cd inside is a mountable device. Mounting removable file systems is usually left to the desktop environment, which can automount it for you using some user specific settings. But if you wish it can be handled through fstab too.

---

