---
title: "Harddrive Nightmares"
date: 2008-03-17
forum: General Help
---

### Post by Voorhees1979 on 2008-03-17
Hi there

I have 3 hd's in my pc. One is where ubuntu is stored. I cant make folders or anything on this drive. Thats my first problem. Second problem, I open Opera click on a file to download, save but I cant save to any drive, None of my other drives show up in the save as location box. So I used Gparted and formatted one of the drives to ext3 they were ntfs before. Thinking that would cue it. Rebooted. Goto computer I can see and open all drives. But as soon as I try to download from opera or filezilla the only drive I can select is the Ubuntu install drive.

Anyhelp would be great

Many thanks Voorhees

---

### Post by askreet on 2008-03-17
First, to help us better understand your setup, paste the outputs from the following commands:

```
sudo fdisk -l
```

```
mount
```

```
df -h
```

Second of all, you cannot write to NTFS under Linux, at all.  If you find software to do this it is very unreliable and will probably damage the filesystem.

Third, your ubuntu partition should be mounted as / by default, and your home folder is contained within this.  You should be able to save any fiiles under /home/<your user name>/.  If you cannot do this there are further problems.

---

### Post by Voorhees1979 on 2008-03-17
Hi

Thanks for the quick reply. You are correct I can save in /home/

This is the full output from your requested cmds:

joe@joe-desktop:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe30ce30c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            3825       24791   168417427+   f  W95 Ext'd (LBA)
/dev/sda5            3825       24791   168417396    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a0ea5d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0baa0ca5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3579    28748286   83  Linux
/dev/sdc2            3580        3738     1277167+   5  Extended
/dev/sdc5            3580        3738     1277136   82  Linux swap / Solaris
joe@joe-desktop:~$ mount
/dev/sdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda5 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev)
/dev/sdb1 on /media/Archive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
joe@joe-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              27G  2.1G   24G   9% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5             161G   16K  161G   1% /media/disk
/dev/sda1              29G  173M   28G   1% /media/disk-1
/dev/sdb1             466G  141G  326G  31% /media/Archive
joe@joe-desktop:~$ 

Many thanks yet again

---

### Post by abalone on 2008-03-17
> **askreet said:**
> Second of all, you cannot write to NTFS under Linux, at all.

Actually, I could write to NTFS partitions right after upgrading to Ubuntu 7.10 and without installing any additional tools (I think Ubuntu uses the NTFS-3G drivers - [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)?) Seems to replace existing Windows ACLs with "full access for everyone" though so unless I want to clean-sweep hopelessly tangled-up Windows permissions I stick with FAT32 for shared data.

---

### Post by Voorhees1979 on 2008-03-17
I have one in fat32 and another in ntfs format. But still why I save as on a web page or from filezilla. I can only access the drive ubuntu is installed on, none of my other drives.

---

### Post by prshah on 2008-03-17
> **askreet said:**
> 

Second of all, you cannot write to NTFS under Linux, at all.  If you find software to do this it is very unreliable and will probably damage the filesystem.



Nope Nope Nope... and you are a Gutsy 7.10 user...

Of course you can write to and read from NTFS partitions with perfect safety... prior to 7.10 you have to setup ntfs3g manually... but now... no need!

---

### Post by prshah on 2008-03-17
> **Voorhees1979 said:**
> Hi

joe@joe-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              27G  2.1G   24G   9% /
/dev/sda5             161G   16K  161G   1% /media/disk
/dev/sda1              29G  173M   28G   1% /media/disk-1
/dev/sdb1             466G  141G  326G  31% /media/Archive
joe@joe-desktop:~$ 

Many thanks yet again

I hope that you know in linux all drives/partitions are mounted under a directory (folder).

In your case, your drives are mounted on /media/... as above. And mounted rw (read-write) so thats not a problem.

You have to be a member of the group plugfs to access these drives. That should have been done for you by default.

I think you are being confused by "drives" as presented in Windows. There are no "drives" in linux; all drives are mounted to a particular directory/folder.

Am I wrong in assuming you are looking for drives as in Windows; drive c:, d:, etc etc.?

---

### Post by Therion on 2008-03-17
> **Voorhees1979 said:**
> I have one in fat32 and another in ntfs format. But still why I save as on a web page or from filezilla. I can only access the drive ubuntu is installed on, none of my other drives.
Have you mounted these drives?

And yes, reading/writing to NTFS (or FAT32) formatted drives is as safe and easy as it gets.

---

### Post by mridkash on 2008-03-17
Are you aware that your hard drives are located in /media folder. When downloading files from browser, the file browser doesn't show other partitions as in 'My Computer'. It is located in Filesystem > /media

EDIT: You beat me [prshah]("http://ubuntuforums.org/member.php?u=394709")

---

### Post by prshah on 2008-03-17
> **mridkash said:**
> Are you aware that your hard drives are located in /media folder. When downloading files from browser, the file browser doesn't show other partitions as in 'My Computer'. It is located in Filesystem > /media

EDIT: You beat me [prshah]("http://ubuntuforums.org/member.php?u=394709")

All that "Klavaro Touch Typing Tutor" work seems to be finally paying off.

---

### Post by askreet on 2008-03-17
My apologies, I'm working with outdated information (my head) that states that NTFS reading and writing is a no-no.  Good news :D

---

### Post by Voorhees1979 on 2008-03-17
Yes thanks very much for the help. It was the /media/archive/ etc

I wasnt expecting it to say C: D: etc. I was just trying /archive/ 

Thanks ever so much for all the help. Now I just need to find a ftp client with gui that allows raw commands

:)

---

### Post by prshah on 2008-03-18
> **Voorhees1979 said:**
> Yes thanks very much for the help. It was the /media/archive/ etc

I wasnt expecting it to say C: D: etc. I was just trying /archive/ 

Thanks ever so much for all the help. Now I just need to find a ftp client with gui that allows raw commands

:)

Hey if you're REALLY REALLY keen on c: d: e: etc, try these:

```

alias c:='cd /media/disk'
alias d:='cd /media/Archive'

```

But usable only in a terminal; and if you want to make it permanent, you have the add the above lines to the .bashrc file in your home folder. While you're at it, why not:

```

alias cls=clear
alias dir='ls -l'

```

---

### Post by mridkash on 2008-03-19
> Now I just need to find a ftp client with gui that allows raw commands

Gftp, FileZilla
Both good, get them from Applications > Add/Remove > Search for ftp

---

