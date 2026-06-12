---
title: "Moving /home to another drive"
date: 2016-11-15
forum: General Help
---

### Post by alain.roger on 2016-11-15
Hi,

i want to avoid losing data if someday i need to install another version of linux on my primary disk SDA.
in this purpose i tried to follow the tutorial available on [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) but it seems i missed something.

I understood the duplication of /home to /media/home for temporary mounting this point and to move the original /home to another disk...
however i did not understand how to tell linux that /home is not anymore on SDA1 but on SDB1.

the tutorial explains to do:
```
[COLOR=#333333][FONT=UbuntuMono]# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) [/FONT][/COLOR][FONT=inherit][/FONT]UUID=????????   /home    ext3          defaults       0       2

[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]
```

But as far as i understood, this command in fstab only says that SDB1 should be mounted as /home.... whereas i have some other directories on SDB1...

i also did not understand why such command line:
```
[COLOR=#333333][FONT=UbuntuMono]cd / && sudo mv /home /old_home && sudo mkdir /home[/FONT][/COLOR]
```
because it creates an empty /home on the same primary disk as before...so SDA1... not on SDB1...

someone can help me please ?

thx

---

### Post by TheFu on 2016-11-15
An empty directory is where you mount file systems. That is why you want to create /home - and leave it empty. It doesn't HAVE to be called /home, BTW. That is just convention for small systems that don't have centralized user management.  The OS doesn't care WHERE the HOME directory is for any specific user, just that the password DB (which can be in /etc/passwd or provided through some service like LDAP or x.500) for the userid points to a valid location for each userid.

If you don't want to change the passwd DB entry, then all that is needed is for the new storage to be mounted so it appears to be in the same location as before - /home.  There really isn't anything more to it than that.  BTW, this applies to pretty much all non-OS file systems. We can move /var to different storage pretty easily or /opt or /usr/local ... the only real caution is that some programs are needed during boot, before networking is up and those need to be placed on storage that is available early enough in the boot process.

I suspect your new partition with all the former /home data isn't ext3. It should be ext4 these days or perhaps some other file system, if there is a good reason.

BTW, case matters in Unix/Linux, so SDA1 would NOT be correct.

Let's simplify this.
[LIST=1]
[*]Boot off alternate media - live CD
[*] sudo mount /dev/sdz1 /mnt # mount the partition with the /home directory - call it sdz1 here.  to a working location
[*]sudo mv /mnt/home /mnt/home-old  # move the old /home to home-old.
[*]sudo mkdir /mnt/home  # Need an empty directory as a mount location for new storage
[*]sudo mount /dev/sdy1 /mnt/home  # sdy1 is storage for the new /home files
[*]sudo rsync -avz /mnt/home-old/* /mnt/home/  # copy everything over from the old storage to the new storage; Check that both disks match.
[*]# Do not delete /mnt/home-old ... let's make sure everything is fine 1st
[*]# Edit /mnt/etc/fstab to mount the new storage, sdy1 onto the HOME at boot ; I would copy the prior line for / and change the device/UUID and mount location
[*]# reboot the live-CD; enter the normal boot
[/LIST]

See that everything is fine.
**df -h**  Both the old disk and new disk should show up.  If everything is fine, delete /home-old recursively. Be very careful on that command.
If you aren't allowed to login or the GUI looks funny, the mount is wrong in the /etc/fstab. Fix that.

I wouldn't use a GUI for any of this stuff. It would all be done from a shell prompt. Running GUI programs as root can lead to problems later.

---

### Post by Impavidus on 2016-11-15
The idea is that by mounting you connect the root of the file system on sdb1 (which contains all stuff that's supposed to be in /home) to the /home directory on sda1.

---

### Post by SeijiSensei on 2016-11-15
Unix employs a single directory tree starting from / unlike the A:, B:, etc., style of Windows.  The root filesystem resides on /dev/sda1.  If you create an empty directory under /, you can mount other filesystems to that location.

If you have other directories already on /dev/sdb1, and you mount it to /home, those directories will appear as /home/dir1, /home/dir2, etc.  (I'm assuming that /dev/sdb1 is formatted with a Linux filesystem like ext4.  You don't want to use something like NTFS for this task.)

If you've mounted the drive in the machine, and it appears as /dev/sdb, you can see how things will look by mounting it to the empty /mnt directory for starters like this:
```
sudo mount /dev/sdb1 /mnt
```
Now do a directory listing with "ls /mnt".  You should see all the directories in the /dev/sdb1 filesystem.

You would do the same thing to mount the filesystem as /home.  First, move /home to /oldhome or some similar name, then as root create an empty /home directory and mount /dev/sdb1 there:
```

cd /
sudo mv home oldhome
sudo mkdir home
sudo mount /dev/sdb1 home

```
Now the contents of /dev/sdb1 will appear as /home.

To have the device mounted automatically at boot, you need to add an entry in /etc/fstab like this:
```
/dev/sdb1   /home     ext4    defaults   0 0 
```
However using /dev/sdb1 is less reliable if you use things like USB sticks and the like.  They can occasionally change the naming scheme.  So Linux now typically uses a scheme that relies on the "UUID" of the partition, a unique hexadecimal sequence that is invariant regardless of what devices are connected.  To take this route, you first need to identify the UUID that corresponds to /dev/sdb1.  Use the command "sudo blkid -l".  You'll get a result like this:
```
/dev/sda1: UUID="7d5eb78b-9387-031d-01c4-2ba3dd74ca7e" TYPE="ext4" 
/dev/sdb1: UUID="023e302e-6396-490a-aaab-f10845a312b4" TYPE="ext4" 
/dev/sdb2: LABEL="WIN7" UUID="1E1E81AF1E81808F" TYPE="ntfs" 

```
Here there is a root filesystem on /dev/sda1 and two filesystems in partitions /dev/sdb1 and /dev/sdb2, one formatted with ext4 and one containing Win7 formatted as NTFS.  If /dev/sdb1 contains /home, then you can rewrite the entry in /etc/fstab like this:
```
UUID=023e302e-6396-490a-aaab-f10845a312b4   /home   ext4   defaults   0 0
```
using the UUID instead of /dev/sdb1.

---

### Post by TheFu on 2016-11-15
Think I'll be saving this thread as a link for "how-to" - nice, useful, info all around. Thanks!

I see now that my use of sdz and sdy could be confusing. Used those to limit problems on most systems (sometimes people copy/paste without understanding), since few people would actually have enough drives to get passed d (sdd).

To get the partition-to-device mapping, use **sudo parted -l** or a modern version of fdisk that supports GPT disks. Either of those commands will show both the partition size AND the partition number. Then use the **blkid** cmd to get the UUID that maps to the device. When you see the output, it will be clear.

Also worth mentioning that if LVM and/or encryption are used, then things get a little more complicated.

---

### Post by Drate on 2016-11-16
Don't forget to mark as solved if indeed your question has been resolved.

---

### Post by alain.roger on 2016-11-17
> **SeijiSensei said:**
> Unix employs a single directory tree starting from / unlike the A:, B:, etc., style of Windows.  The root filesystem resides on /dev/sda1.  If you create an empty directory under /, you can mount other filesystems to that location.

If you have other directories already on /dev/sdb1, and you mount it to /home, those directories will appear as /home/dir1, /home/dir2, etc.  (I'm assuming that /dev/sdb1 is formatted with a Linux filesystem like ext4.  You don't want to use something like NTFS for this task.)

If you've mounted the drive in the machine, and it appears as /dev/sdb, you can see how things will look by mounting it to the empty /mnt directory for starters like this:
```
sudo mount /dev/sdb1 /mnt
```
Now do a directory listing with "ls /mnt".  You should see all the directories in the /dev/sdb1 filesystem.

You would do the same thing to mount the filesystem as /home.  First, move /home to /oldhome or some similar name, then as root create an empty /home directory and mount /dev/sdb1 there:
```

cd /
sudo mv home oldhome
sudo mkdir home
sudo mount /dev/sdb1 home

```
Now the contents of /dev/sdb1 will appear as /home.


First of all, thanks to all of you for explaination. i know that it is sda1 and not SDA1 in capital letter. i just wrote it this way that make clear i had 2 different drives. so no problem.

In fact, you answered to a hidden question but i guess i did not correctly ask the question.
i know about mounting drives to empty folder, but i was wondering if on sdb1 (2nd drive) that already have different folders, i i could link it to an empty /home...like if it was mounted, but in fact just linked to that folder...
so if i do a ll -a on /dev/sdb1 i would see:
- /download
- /home
- /backups

and the /home of /dev/sdb1 would be linked to /dev/sda1/home folder

so basically when i save a file/folder in /home, it is in fact saved/created into /dev/sdb1/home directory :)
Because i really do not want to have 2TB /home folder.... (as my drive /dev/sdb1 is 2TB)
i want to move on /dev/sdb1 my /home folder in order to avoid losing data in case i must reinstall on /dev/sda1 my OS. that's all.
But i really do not want to have a huge /dev/sdb1/home folder with other folders (download, backup, etc...) inside it.

Am I clearer? :)

for sure i use UUID as i agree that different versions of same distro or different distro can mix /dev/ device naming..

---

### Post by TheFu on 2016-11-17
You can do any of those things, but it becomes more complicated the more you don't go the standard, normal, device (really partition in your case) --> mount way.
You can make multiple partitions on sdb, but if you aren't certain about the required sizing, then I'd use LVM. That way you can start out with small LVs (effectively logical partitions) and grow them as needed, where needed, usually on a live file system.  

Of course, to switch from a straight partition into a partition + LVM does require some fandangling and a slight amount of skill.  Basically, doing a full backup, then setup the partition as you like and LVM on top of that, as you like.  None of this removes the requirement to have backups. Screwing around with partitions and/or LVM requires backups. It is just too easy to make a mistake and lose everything.

But ... pretty much anything you can think of is possible. However, possible doesn't mean simple.

LVM is extremely flexible, but we don't need to use it that to get the best parts from it.  All my primary physical disks use LVM.  None of my backup disks do. I just don't want the hassles when it is time to restore.  This also forces me to consider primary storage sizing AND backup storage sizing together.  I don't want to be in a situation where the primary storage/partition/LV is larger than the backup partition available to hold that data.

I should also point out that LVM misuse is how I lost 80% of my data about 15 yrs ago.  I had merged 3 physical disks into a single LV - it was very convenient.  Then one of those disks failed.  I hadn't gotten backup religion by that point.  All the data on all three disks was unavailable becuse 1 disk failed.  Today, I might have been able to restore some of the data from the other 2 disks, but not back then.

With great power comes great responsibility.  Get backup religion soon, if you don't already have it.  I'd feel better helping, if I knew you had versioned, backups, already.

Of course, you can use symbolic links for all of this too. That would be very easy, but considered "a hack."  I've used them (and still do) for convenience. Just have to be aware when you go down a symlink that it exists.  Hardlinks don't work across file systems, but symlinks do.

I kinda don't see the issue with having /home and /downloads on the same physical disk. I am concerned that you'd put the /home on the same disk as /backups. That really isn't smart for more than a few days, until you can get another physical disk.  And if you are doing that, why not just get one for /home instead and leave the other stuff where it is?  There are probably valid reasons, just from here it may be an issue.

---

### Post by alain.roger on 2016-11-17
In fact i could use GParted to split into 2 partitions my 2 TB drive and to have 1 partition (sdb1) used as /home and the other partition as sdb2 for /download, /backup, /books etc...

by the way i wrote /backup as example. in fact this directory is used only for local copy from my NAS in case i'm offline and i can get access to NAS shared folders.

it is not used for laptop or any data backup...if i lose it, it does not matter.

my goal is to have a partition only for /home and as on my laptop i have only 2 HDD, one is for the system and the other for data (/home, /and_other_stuff, /and_so_on)
so i would be able in case of OS reinstallation on primary disk, to not lose data from drive 2 (so having /home there)

only /home is sync with my NAS shared forlders.

---

### Post by javierdl on 2016-12-28
I finally had the time to work on this.
Unfortunately this does not work while system files are open: "*cannot move 'home' to 'oldhome': Device or resource busy*".
I found that I could 1. [COLOR=#111111][FONT=Ubuntu]Log out, and [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]go to a virtual terminal. Or 2. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] Run this in recovery mode to be very sure no file to a user is open, by [booting into single-user mode from GRUB.]("http://askubuntu.com/questions/132965/how-do-i-boot-into-single-user-mode-from-grub")
But what about booting up from a Live USB?

Thanks[/FONT][/COLOR]

---

### Post by TheFu on 2016-12-28
I wouldn't use move/mv.  I'd use rsync.  

Also, I'd boot off alternate media, as you ask. That would be easiest. The actual version of Linux isn't too important unless encryption is used.  File systems, partitions, LVM are all pretty standard.

Regardless, always, always, always, have a backup that can be restored before attempting any work like this.  That way, if 1 tiny mistake is made, you can restore and try again.

---

