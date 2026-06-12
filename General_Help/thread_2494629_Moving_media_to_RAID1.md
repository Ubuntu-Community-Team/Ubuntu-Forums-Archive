---
title: "Moving /media to RAID1"
date: 2024-01-22
forum: General Help
---

### Post by SBFree on 2024-01-22
I am trying to build a web server. It has one SSD for the OS and a pair of drives that are a RAID1 array created with mdadm (/mnt/md0). The single drive has to remain the boot drive, apparently the RAID1 array is not recommended to be a boot drive and it also contains another OS. In particular, /media needs to be on the RAID1 array. The learning curve is steep for me on this. If I use

```
mkdir /mnt/md0/media
mv /media /mnt/md0/media
mount --bind /media /mnt/md0/media
```

Will this cause any references that the server software to /media point to files/directories on the RAID array? Will there be duplicate information in /media & /mnt/md0/media? Is a better approach just to re-install this instance of Ubuntu with the RAID1 partitioned to have a mount point as /media?
Thanks in advance for any replies
scott

---

### Post by TheFu on 2024-01-22
Use a subdirectory under /media to mount.  Almost all Linux OSes with a GUI are setup to assume gio/gvfs own /media/ and have full control over it, so all sorts of bad things are likely if you ever connect any storage to the system that any GUI tool (or udev) decides to mount under /media/.

The better answer is to mount your RAID storage **anywhere else** than /media/.  I mount all my storage into directories that I control under /d/.  
```
$ dft     # <---- this is a fancy alias that only shows real storage
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01                  ext4   35G  7.1G   26G  22% /
/dev/nvme0n1p3                           ext4  672M  283M  340M  46% /boot
/dev/nvme0n1p2                           vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-var01                   ext4   20G  4.2G   15G  23% /var
/dev/mapper/vg01-libvirt--01             ext4  134G  131G  2.8G  98% /var/lib/libvirt
/dev/mapper/vg01-home01                  ext4   20G  5.9G   13G  32% /home
/dev/mapper/vg01-tmp01                   ext4  3.9G  270M  3.4G   8% /tmp
/dev/md1                                 ext4  1.8T  1.7T   43G  98% /raid1
/dev/md2                                 ext4  1.3T  383G  811G  33% /raid2
/dev/mapper/vg--rom01-lv--rom--data--1tb ext4  196G  125G   62G  68% /d/rom/Data/1TB
/dev/mapper/vg--rom01-lv--rom--data--r2  ext4  1.5T  249G  1.2T  18% /d/rom/Data/r2
/dev/mapper/vg--rom01-lv--rom--misc--2tb ext4  1.5T  1.4T   50G  97% /d/rom/misc/2TB
/dev/mapper/vg--rom01-lv--rom--raid      ext4  2.0T  1.7T  214G  89% /d/rom/raid
/dev/mapper/vg--rom01-lv--rom--videos    ext4  197G  148G   40G  79% /Backups
/dev/mapper/vg--rom01-lv--rom--export    ext4  196G  120G   67G  65% /d/rom/export
istar:/d/D1                              nfs4  3.5T  3.5T   45G  99% /d/D1
istar:/d/D2                              nfs4  3.6T  3.6T   38G  99% /d/D2
istar:/d/D3                              nfs4  3.6T  3.6T   23G 100% /d/D3
istar:/d/D6                              nfs4  3.6T  3.4T   55G  99% /d/D6
istar:/d/D7                              nfs4  3.6T  1.1T  2.4T  31% /d/D7
```
The /raid1 and /raid2 are left over from some really old drives pre-2010.  As you can see, I use LVM now. Extra storage is under /d/{somthing}/ . Both local and remote/NFS.  I also use autofs to mount USB connected storage under /d/ to avoid gio and gvfs screw-ups.

Took me decades of administration to decide this was the best compromise for my needs.   I mount /tmp/ with specific mount options for better system-wide security, unlike the default way that Ubuntu does it too.

---

### Post by SBFree on 2024-01-22
Thanks for the reply. I'm sad that it is above my current level of understanding at the moment. My RAID1 is mounted at /mnt/md0. Even if I mount it at /media/md0, I am assuming that the webserver manager, [runtipi]("https://runtipi.io/"), will still store media in /media. That's what the install docs seem to [indicate]("https://runtipi.io/docs/guides/customize-app-config").
> Mount an existing volume on your host into a media app such as Jellyfin. By default, media apps will only be able to see files within runtipi/media, but you can add other volumes.
An alternative approach to mounting a volume into an app would be to symlink your host volume into runtipi/media. However, that would make it visible to all apps that mount the media folder, which may not be desirable.
Scott

---

### Post by SeijiSensei on 2024-01-22
I would use rsync to move the contents to the array.

Is the content directly under /media/, or is it another subdirectory? The former makes moving stuff a bit more complicated. 

```

sudo mkdir /mnt/tmp
sudo mkdir /media/raid
sudo mount /dev/md0 /mnt/tmp
cd /media
sudo rsync -av . /mnt/tmp
sudo rm -rf .
cd /mnt/tmp
sudo rsync -av . /media/raid

```
This moves the contents of /media/ to a temporary location, then copies the contents of the temporary directory to the RAID device.

/media should never contain ordinary files, just directories that can be used as mount points.

---

### Post by SBFree on 2024-01-22
Thanks for this info, > /media should never contain ordinary files, just directories that can be used as mount points. 
The array is already mounted at /mnt/md0 and is empty since I have yet to install the server manager, [runtipi]("https://runtipi.io/")
While I can choose directories for each docker container it installs, the server manager uses /media to create directories for media that is shared by all containers.
It's ok for my application if the information is shared but I want it to be on the RAID array.
This subject is just beyond my current level of understanding, so please forgive me if I present information that seems confusing.
scott

---

### Post by TheFu on 2024-01-22
This seems to be a question more about runtipi than Linux.  I've never heard of runtipi before. Sorry.  Also, I don't use docker, but with the linux container solution I use, lxc, making additional storage available to a specific container is pretty trivial - it is just a config file setting for that container startup and can be set to anything - pretty much.

As for jellyfin, I've used that about 3 yrs and jellyfin can access media storage using all sorts different methods. Multiple locations for each library are supported.  For example, I have a number of HDDs with different content types on them, just stored in subdirectories by the type.  Inside the Jellyfin web-gui, I just add the same types of media to the specific library and all that content gets merged into a single view.  Administration --> Dashboard --> Libraries  --> Manage Library.

Basically, I have 
```
/d/D1/M
/d/D2/M
/d/D3/M
/d/D6/M
/d/D7/M
```
all in the "Movies" Library.  For the "TV" library, there is:
```
/d/D1/T
/d/D2/T
/d/D3/T
/d/D6/T
/d/D7/T
```

See the pattern?  Can you guess what my backup disks for all this data looks like?  Bet you can.
```
/d/b-D1
/d/b-D2
/d/b-D3
/d/b-D6
/d/b-D7
```

K.I.S.S. at work.  [https://en.wikipedia.org/wiki/K.I.S.S](https://en.wikipedia.org/wiki/K.I.S.S).

I mount this storage to other systems using NFS.  Because I'm often stupid, I ensure those mounts are to exactly the same place on all clients as they are on the NFS server.  On the NFS client:
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
istar:/d/D1                              nfs4  3.5T  3.5T   45G  99% /d/D1
istar:/d/D2                              nfs4  3.6T  3.6T   38G  99% /d/D2
istar:/d/D3                              nfs4  3.6T  3.6T   23G 100% /d/D3
istar:/d/D6                              nfs4  3.6T  3.4T   57G  99% /d/D6
istar:/d/D7                              nfs4  3.6T  1.1T  2.4T  31% /d/D7

```
And on the NFS server:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-lv_media              ext4  3.5T  3.5T   45G  99% /d/D1
/dev/mapper/istar--vg2-lv_media2            ext4  3.6T  3.6T   38G  99% /d/D2
/dev/mapper/istar--vg3--back-lv_media3_back ext4  3.6T  3.6T   23G 100% /d/D3
/dev/mapper/WDBLK_8T-lv_d6                  ext4  3.6T  3.4T   57G  99% /d/D6
/dev/mapper/WDBLK_8T-lv_d7                  ext4  3.6T  1.1T  2.4T  31% /d/D7

```
You get the idea. Sorry for the inconsistent LVM LV names. I've been changing my naming convention for LVM stuff over the decades.  And, just as proof that I'm not joking about backups ....  I'm not:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB-istar--back3--a      ext4  3.6T  3.5T  155G  96% /d/b-D1
/dev/mapper/istar--8TB-istar--back3--b      ext4  3.6T  3.6T   42G  99% /d/b-D2
/dev/mapper/istar--vg2--back-lv_media2_back ext4  3.6T  3.6T   28G 100% /d/b-D3
/dev/mapper/istar--8TB--B-lv4_back          ext4  3.6T  3.4T  923M 100% /d/b-D6
/dev/mapper/istar--8TB--B-lv5_back          ext4  3.4T  1.1T  2.2T  33% /d/b-D7

```
Also note that I don't use any RAID for this stuff.  I have RAID elsewhere, but media just isn't that important. Backups are 1000x more important.

---

### Post by SeijiSensei on 2024-01-22
There are issues with the code I gave you above. Is there enough space on the device where the root filesystem is stored to make a copy of /media/? If so, I'd try this instead.
```

# back up /media to /opt/media
cd /
sudo rsync -av media /opt

# empty /media of old files
cd /media
sudo rm -rf *

# make a mount point for the RAID device and mount it
sudo mkdir /media/raid
sudo mount /dev/md0 /media/raid

# copy the files to the RAID device
cd /opt/media
sudo rsync -av . /media/raid

```

When you're sure everything is okay, you can delete /opt/media.

If you add the "n" switch to rsync (rsync -avn ...) it will do a "dry-run" and show you what will be transferred without doing anything. Useful to make sure you have the right directory specification.

---

### Post by SBFree on 2024-01-23
Thanks everyone. I'm going to address this by reinstalling the OS with different mount points for the RAID array. That should solve my concerns. Apologies for being confusing/confused.
s

---

### Post by TheFu on 2024-01-23
> **SBFree said:**
> Thanks everyone. I'm going to address this by reinstalling the OS with different mount points for the RAID array. That should solve my concerns. Apologies for being confusing/confused.
s

It is easy to be confused because so many things are possible and everyone does it a bit different, based on their specific needs.  
There is no "this 1-way" for Unix systems. That's both a good thing and a terrible thing.  
There are usually 50 choices, if not 500 or 50,000, all of which can be fine. 

As an admin, most of my job is avoiding issues, current and future, BEFORE they happen. Over the decades doing this, I've learned some things to avoid either from mentors or by living through the failure.  So have the other people posting here.  Everyone has different backgrounds and different experiences, so we've hit different issues and likely solved them differently. That's why you'll see different answer.

Good luck with the learning curve.

---

