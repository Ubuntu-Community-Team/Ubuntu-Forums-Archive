---
title: "Media on NTFS: performance"
date: 2014-01-22
forum: General Help
---

### Post by Captain_Envious on 2014-01-22
Hi, I was wondering whether storing all my documents and media files on an NTFS partition would impact performance. My question is actually pretty similar to this one (which is unanswered):
[http://askubuntu.com/questions/246814/ext4-vs-mounted-windows-ntfs-for-hdd-data-storage](http://askubuntu.com/questions/246814/ext4-vs-mounted-windows-ntfs-for-hdd-data-storage)

Note that this thread is not intended to be a (general) ext4 vs NTFS discussion. ;)

Right now I have an 1TB HDD and am dual-booting Ubuntu 13.10 and Windows 7. This is more or less how the HDD is partitioned:
Windows 7 OS (NTFS, 150GB)
Media (NTFS, 700GB)
Ubuntu / (ext4, 10GB)
Ubuntu /home (ext4, 100GB)
Ubuntu swap (8GB)

A huge chunk of my media files is stored on the NTFS Media partition because I need to access them from Windows. I store other media files and documents (mostly audio files, pictures and LibreOffice and PDF files which I usually only need on Ubuntu) on my 100GB /home partition. The downside is that around 30GB is unused on my /home partition, while I sometimes run short of disk space on my NTFS Media partition. I can't just increase the Media partition and reduce the /home partition by 30GB, because I might have more media files and documents for use on Ubuntu over time and my /home partition would then be too small. That's why I was wondering if I wouldn't be better off increasing my Media partition and storing *all *my media on it so I could make more efficient use of my HDD's capacity. All the configuration files and applications (e.g. programs in my .wine folder) would remain on the ext4 /home partition. Would that result in overall lower performance?

Thanks in advance!

---

### Post by TheFu on 2014-01-22
FUSE file systems are much, much slower to access than native, kernel accessed file systems.  For files that are only read, not edited, I wouldn't worry too much about that difference, especially for videos and audio.  Office-type documents that are edited need file locking, so a native file system would be helpful, but for average sized files, it probably doesn't matter too much.

If file permissions are important - programs and sensitive docs - then I'd leave those under Linux.  Not that it is any safer - after all, anyone with a boot flash drive can access Linux disks and completely ignore any of the main permissions ... unless encryption is used, but casual users will be stopped.

For normal desktop use, with no video editing, I wouldn't worry about the performance difference too much.

---

### Post by Impavidus on 2014-01-22
I think the ntfs partition will be slower, but for documents and media files this usually shouldn't matter. Still, moving all to the same partion for some extra flexibility (in general a nice idea) will give you just 30GB of extra space, which, compared to the 770GB currently in use on media and home combined, isn't much.

---

### Post by Captain_Envious on 2014-01-22
Great! I hardly ever do video editing. I think I'll go for a compromise: most video and audio files on the NTFS partition, but other (mostly work-related) documents on /home. Since those documents (and of course the config files) might increase in size and number, I'll still give the /home partition some breathing space. It definitely won't need to be 100GB large though.

Thanks for the input!

edit: That being said, it's true that an extra 30GB isn't that much, though it might have made an appreciable difference when the Media partition was running short of space. I guess I could have been more economical with the partition's space anyway.

It's worth mentioning that I'm planning to get a 120GB SSD sometime this year. In fact I should probably have included that information in my original question. In light of what has been said, I'm considering the following options:
**a)**
SSD:
Windows 7 (NTFS, 100GB OR 90GB)
Ubuntu / (ext4, 10GB)
Ubuntu /home (ext4, 10GB OR 20GB): config files and programs only OR config files and programs + work-related documents

HDD:
Ubuntu swap
Media (NTFS): all media + documents OR media only

**b)**
SSD:
Windows 7 (NTFS, 100GB OR 90GB)
Ubuntu / (ext4, 10GB)
Ubuntu /home (ext4, 10GB OR 20GB): config files and programs only OR config files and programs + documents

HDD:
Ubuntu swap
Ubuntu "home 2" (ext4): media needed on Ubuntu + documents OR media needed on Ubuntu only
Media (NTFS): media needed on Windows only

---

### Post by Impavidus on 2014-01-22
I wouldn't make a 10 or 20GB /home partition. If that small it will be easier (more flexible, as you noted yourself) to just include it in the / partition. It's easy to backup the entire /home directory if it's that small.

Most people combining an SSD and an HDD put their entire /home directory on an ext4 partition on the HDD. The dual booters have an ntfs data partition next to it. Only the operaring system(s) itself is on the SSD. Others don't use a separate /home partition, storing their configuration files on the root partition and symlinking to their shared data partition, where their documents and media files are stored. Your choice, both options are OK.

---

### Post by Captain_Envious on 2014-01-23
I'd rather store config files on the SSD because I've heard it may improve performance. If you put them on the root partition, won't that mess with file permissions, e.g. can you still edit programs' settings without launching them as root?

---

### Post by Impavidus on 2014-01-23
Even if you store your (personal) config files on the root partition, they will be in your home directory. You just don't have a home partition that way. In your home directory (/home/username/) all files are owned by you, not by root, and you have full permission to modify any of those files. Else the whole security model would miss its purpose.

---

### Post by mastablasta on 2014-01-23
i am using Raspbery pi as media server. i've attached NTFS external drive to it. no major speed issues so far. rtorrent service didn't work but that's about it. 

later on i plan something similar for PC, since i plan to keep windows XP.

---

### Post by TheFu on 2014-01-23
> **Captain_Envious said:**
> I'd rather store config files on the SSD because I've heard it may improve performance. If you put them on the root partition, won't that mess with file permissions, e.g. can you still edit programs' settings without launching them as root?

The running OS cares very little about "partitions."  It cares very much about file systems, directories and file permissions.  As long as the "home" directory specified in the passwd file points somewhere that the userid can access and has enough privileges inside (can't be NTFS or FAT-whatever), there isn't any issue. That "home" can be named anything.  It can be a symlink to another location, the same or different partition, provided the access is setup correctly. Each entry in the passwd file can point to completely different storage locations for home directories, users do not need to be under /home, though that is a good, expected, location on non-shared, non-workgroup, systems.

File and directory permissions are the cornerstone of Linux security. The way this works is simple, elegant, effective. Gaining a better understanding is a 20-minute tutorial away.  On UNIX/Linux systems almost everything is "a file" with permissions, owner, groups. The monitor, keyboard, mouse, sound card, device drivers, directories, symlinks, and files .... all of those are "files" with permissions. 
Work through [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) to gain a better understanding.

I would still split up the OS/Apps and /home partitions.  It makes system updates between releases less hassle, provided the /home partition doesn't get overwritten accidentally.  There is a risk of filling /, which can be really bad, but that will always exist. I don't have an direct knowledge of SSDs - too new for my consideration still. Maybe in 3 or 5 more years, I'll make the switch. ;)

---

### Post by Captain_Envious on 2014-01-24
I think I'll keep storing the files I use on Ubuntu on an ext4 partition as opposed to an NTFS partition, because of the various advantages in  terms of security, file naming etc. (mind you, those are part of the reason I'm using a Linux OS in the first place ;)) even if it makes little difference  performance-wise.

> **TheFu said:**
> I would still split up the OS/Apps and /home partitions.  It makes system updates between releases less hassle, provided the /home partition doesn't get overwritten accidentally.

This and the fact that I'm almost positive 20GB are more than enough for my /home partition (the config files and documents altogether are currently about 10GB large) make it more convenient for me to have a separate /home partition with the config files and the documents but without the media. So basically it's the aforementioned option b).

---

