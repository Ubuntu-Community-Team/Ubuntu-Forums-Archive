---
title: "Need help with installing programs on other hard drive"
date: 2014-10-27
forum: General Help
---

### Post by Gustaf_Alhll on 2014-10-27
I just installed Linux Ubuntu on my computer and I haven't ran into problems with the system so far. But I have a problem with program installment through Ubuntu Software Center.

On my computer, I have two hard drives. I have the primary hard drive which the operating system is stored on and the secondary hard drive which is the biggest of the both. But the problem is that Ubuntu Software Center installs programs on the primary hard drive when I want it to install it on the secondary one, since it's the biggest one and has a lot of space left. Is this possible? If it is, how do I do so?

Any help is appriciated.

---

### Post by TheFu on 2014-10-27
There are many, many, different ways to accomplish this.  25G on the main OS drive should be enough for all except 1% of users.  Programs are installed under /usr with settings (system-wide) going into /etc and data for these programs normally going into /var.

So ... you can relocate the storage used by any or all of those top level directories to the other drive.

The smartest thing I can ask right now is for you to post the output from two commands:
* df -h
* sudo parted -l
Please, please use "code tags" to make it easier. When it comes time to actually move the data, if that is still your decision, it may be smarter to move any excess stuff instead to the other drive.  Having the OS, boot and programs on different drives doubles the chances that a disk failure will screw your access to the system.  Moving key files like these around is best performed using a booted liveCD (liveUSB) and being very comfortable with the recovery mode text stuff.

---

### Post by grahammechanical on 2014-10-27
Which drive do you have your data on? It would be better, in my opinion, to have your data on the biggest drive. Audio and video files can take up a lot of space. Besides, if you need to reinstall your data will not be at risk.

Regards.

---

### Post by Gustaf_Alhll on 2014-10-27
I ran both, and "df -h" gave (Sorry for the language, I'm swedish):
```
Filsystem      Storlek Använt Ledigt Anv% Monterat på
/dev/sda1          95G   5,0G    85G   6% /
none              4,0K      0   4,0K   0% /sys/fs/cgroup
udev              7,8G   4,0K   7,8G   1% /dev
tmpfs             1,6G   1,2M   1,6G   1% /run
none              5,0M      0   5,0M   0% /run/lock
none              7,9G   404K   7,9G   1% /run/shm
none              100M    72K   100M   1% /run/user
/dev/sdb1         1,9T   1,5G   1,9T   1% /media/gustav/Ny volym               -- This is the secondary drive.
```

"sudo parted -l" gave this:
```
Modell: ATA KINGSTON SH103S3 (scsi)
Disk /dev/sda: 120GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: msdos

Nummer  Början  ****   Storlek  Typ       Filsystem       Flaggor
 1      1049kB  103GB  103GB    primary   ext4            startbar
 2      103GB   120GB  17,2GB   extended
 5      103GB   120GB  17,2GB   logical   linux-swap(v1)


Modell: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sektorstorlek (logisk/fysisk): 512B/4096B
Partitionstabell: msdos

Nummer  Början  ****    Storlek  Typ      Filsystem  Flaggor
 1      1049kB  2000GB  2000GB   primary  ntfs
```

Also, when I mean hard drive, I don't mean a disk or a USB connected to the computer. What i have is a secondary disk INSIDE the computer itself, just like the primary hard drive inside the computer.
Still, any help you can give me around moving programs to another disk? Something I have to think of or is it just to move the whole thing onto the other disk?

---

### Post by sudodus on 2014-10-27
I think your 95 GB for the root partition will be enough for all the programs you will install during the lifetime of the computer. Just keep data files on the other drive, for example mounted as a ***data*** partition.

---

### Post by Gustaf_Alhll on 2014-10-27
> **sudodus said:**
> Just keep data files on the other drive, for example mounted as a ***data*** partition.
Here comes the question on how to actually get them there. I don't want to risk screwing any programs up, so that is why I ask how.
Sorry if it is a stupid question. I'm new to Linux Ubuntu.

---

### Post by sudodus on 2014-10-27
Most data files can simply be moved with any tool, for example a ***file browser*** (corresponding to Windows Explorer), for example document files, pictures, video clips, music ...

Some data files 'belong to certain application programs in a tighter way', and cannot be moved just like that. In such cases it may be possible to copy the whole directory to the second drive, and when you are sure it is there, you can rename the original directory and replace it with a ***symbolic link***. That is the linux name of what is called 'shortcut' in Windows.

Do you need to read files from the second disk from Windows? In that case it should keep the NTFS file system. Otherwise it is better to have a linux file system, for example ***ext4, which is more efficient for linux, and it also gives you the native management of file permissions***. There can be problems with permissions, if you move files that depend on them to an NTFS file system.

---

### Post by sgoranov on 2014-10-27
> **sudodus said:**
> I think your 95 GB for the root partition will be enough for all the programs you will install during the lifetime of the computer. Just keep data files on the other drive, for example mounted as a ***data*** partition.

+1

In my opinion you should not worry about that! You've got plenty of space and if you are not going to run some kind of server which keeps a lot of data (for example http server with a lot of vhosts) there is nothing to worry about. 
Install you programs and don't think about the space, just place the music, movies and so on largest hard drive.

Regards,
S.

---

### Post by Gustaf_Alhll on 2014-10-27
> **sgoranov said:**
> +1

In my opinion you should not worry about that! You've got plenty of space and if you are not going to run some kind of server which keeps a lot of data (for example http server with a lot of vhosts) there is nothing to worry about. 
Install you programs and don't think about the space, just place the music, movies and so on largest hard drive.

Regards,
S.
Well, at least I got somewhere to store the bigger things I'm going to do (I'm programming Java programs, fun fact).

So thanks for the help, everyone!

---

### Post by TheFu on 2014-10-27
> **sudodus said:**
> I think your 95 GB for the root partition will be enough for all the programs you will install during the lifetime of the computer. Just keep data files on the other drive, for example mounted as a ***data*** partition.

+1 - er ... again.

95G is HUGE for apps and OS in Linux.  Heck - I'd be surprised it those took over 20G - I'm completely serious.
It it common to move the /home partition to another drive, since that is where most big files will be placed.

However, it is absolutely critical that Linux apps/OS and /home be stored on Linux file systems - NOT NTFS. If that other drive (sdb1) is NTFS, then that will not work.

In Linux, if you make the files accessible using the old patch through symbolic links, then 99,9999% of programs won't care.  A few might, but I haven't seen any that do in about a decade and those were always proprietary software with license keys, yet still extremely rare.

Symbolic links are extremely powerful - sorta like Libraries in the microsoft world, but sym-links work everywhere, not just in the GUI. This is because they are part of the file system itself, NOT part of some GUI add-on.  There are also hard-links for file - these are really cool too, but cannot cross partition boundaries - so not useful in your situation.

Seems like you are at the point where a little directed learning might be helpful to understand the underlying OS?  Let us know. There are some great, free, resources - books. If interested.

---

