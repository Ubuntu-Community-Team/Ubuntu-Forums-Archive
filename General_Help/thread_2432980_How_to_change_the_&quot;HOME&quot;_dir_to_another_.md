---
title: "How to change the &quot;HOME&quot; dir to another disk"
date: 2019-12-11
forum: General Help
---

### Post by klays on 2019-12-11
Pls, help, this is the disk where i need to move the SO: **/dev/sda4**, and in this disk is the actual HOME: **/dev/sdb2**

---

### Post by CatKiller on 2019-12-11
[https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

---

### Post by klays on 2019-12-11
i try but the "home dir" is the same.

---

### Post by TheFu on 2019-12-11
> **klays said:**
> Pls, help, this is the disk where i need to move the SO: **/dev/sda4**, and in this disk is the actual HOME: **/dev/sdb2**

Those are device names, which can change from boot to boot.  Best to use UUIDs or LABELs or by-path/ links which do not change to control where the partitions are mounted.

Where do you want to move HOME?  /users/home/klays?  Somewhere else?  To do that, just change the HOME directory location specified in the password entry field.  That won't move any data, but at the next login, the home will be in the new directory.  If you correctly mount new storage there with a unix file system (don't use NTFS or FAT-whatever, that will break things), then you can move the old /home/klays stuff over as you like.

I'm pretty certain that help.ubuntu.com has a step-by-step guide to accomplish this. Google should find it easily.

---

### Post by oldfred on 2019-12-11
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Skaperen on 2019-12-12
did you try [COLOR=#0000cd][FONT=courier new]**usermod**[/FONT][/COLOR]?  that's what i used to move a few home directories to another partition.

---

### Post by klays on 2019-12-12
ready, but when i download a app from app center this saves in the old disk, (2.1GB) and i need to save in the new disk (500GB), how i can do?

---

### Post by TheFu on 2019-12-12
> **klays said:**
> ready, but when i download a app from app center this saves in the old disk, (2.1GB) and i need to save in the new disk (500GB), how i can do?

We need some facts to help. 

What facts?
[LIST]
[*]What partitions are mounted?
[*]Where are those partitions mounted?
[*]Did the previous partition/directory with the HOME directories get moved to the new partition?
[*]Did the password entry for the relevant usernames get updated?
[/LIST]

Please help us to help you, by answering those questions.  Nothing is all that hard, but asking questions without answering ours isn't going to work.  The output from these commands will be very helpful:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -o name,size,type,fstype,mountpoint
getent passwd  klays

```
Please, please wrap them in 'code tags' like I've done, so the post here is lined up correctly and columns look like they do in the terminal.  Too hard to read/interpret without that.

---

### Post by klays on 2019-12-12
```
klays@klays:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
S.ficheros     Tipo    Tamaño Usados  Disp Uso% Montado en
/dev/sdb2      ext4       14G    12G  1,9G  86% /
/dev/sda2      vfat      296M    55M  242M  19% /boot/efi
/dev/sda1      ext4      441G   1,8G  417G   1% /home
/dev/sdc1      fuseblk   932G   520G  413G  56% /media/klays/DISCO
klays@klays:~$ lsblk -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE   MOUNTPOINT
loop0  149,9M loop squashfs /snap/gnome-3-28-1804/67
loop1   14,8M loop squashfs /snap/gnome-characters/296
loop2   53,1M loop squashfs /snap/instagramport/5
loop3  137,7M loop squashfs /snap/code/22
loop4   68,5M loop squashfs /snap/ghost-desktop/80
loop5   54,4M loop squashfs /snap/core18/1066
loop6   44,2M loop squashfs /snap/gtk-common-themes/1353
loop7  156,7M loop squashfs /snap/gnome-3-28-1804/110
loop8    3,7M loop squashfs /snap/gnome-system-monitor/100
loop9   1008K loop squashfs /snap/gnome-logs/61
loop10  54,6M loop squashfs /snap/core18/1279
loop11  89,1M loop squashfs /snap/core/8213
loop12 181,1M loop squashfs /snap/spotify/36
loop13  42,8M loop squashfs /snap/gtk-common-themes/1313
loop14  88,5M loop squashfs /snap/core/7270
loop15  14,8M loop squashfs /snap/gnome-characters/367
loop16     4M loop squashfs /snap/gnome-calculator/406
loop17   217M loop squashfs /snap/atom/242
loop18   4,2M loop squashfs /snap/gnome-calculator/544
loop19   956K loop squashfs /snap/gnome-logs/81
loop20   108M loop squashfs /snap/mc-installer/447
loop21  65,9M loop squashfs /snap/discord/101
loop22   3,7M loop squashfs /snap/gnome-system-monitor/111
loop23 140,7M loop squashfs /snap/gnome-3-26-1604/98
sda    465,8G disk          
&#9500;&#9472;sda1 448,8G part ext4     /home
&#9500;&#9472;sda2   300M part vfat     /boot/efi
&#9500;&#9472;sda3   128M part          
&#9492;&#9472;sda5    16G part ntfs     
sdb     14,6G disk          
&#9500;&#9472;sdb1   512M part vfat     
&#9492;&#9472;sdb2  14,1G part ext4     /
sdc    931,5G disk          
&#9492;&#9472;sdc1 931,5G part ntfs     /media/klays/DISCO
sr0     1024M rom           
klays@klays:~$ getent passwd  klays
klays:x:1000:1000:Tomás Barros,,,:/home/klays:/bin/bash
klays@klays:~$ 


```

Yes, the home directory has been moved.

---

### Post by Skaperen on 2019-12-12
so you have a very small old disk and a much larger new disk.  i'd suggest doing a complete fresh new install on the new disk (then do dist-upgrade to bring it fully up to date).  do not format the old disk, for obvious reasons.  create all the old users as new users on the new disk.  copy each home directory from old to new.  copy the entire old disk raw, sector by sector, as a compressed image file on the new disk as an archival backup.

---

### Post by TheFu on 2019-12-12
So, it seems we have a failure to communicate, perhaps.  A HOME directory is a specific thing for each username/login.  It is not system-wide. 
**echo $HOME **
will show the HOME for the current userid. That is where individual settings and data are stored.  

Where software gets installed depends on the type of packaging, but it is NOT in any HOME directory.  Debian/APT packages almost always are installed under /usr/, with system-wide configuration files placed into /etc/.  Before snap packages were recently forced onto Ubuntu users, this was always the way it worked.  I think snap packages are stored in /var/ somewhere, but really don't know.

In general, / (the root directory) would hold the OS and application files.  25G was the recommended size for most desktop users.  It you are cautious, you can fit a desktop in 10G or 15G, but that takes work, mostly by not installing lots of GUI programs.  14GB is small for many users.  I've been moving the same desktop forward since the beginning of Ubuntu and it fits into 17GB - that's everything except the swap.

There isn't any way to tell new install programs to be installed outside /usr/.  When that partition gets full, add a new partition+file system with the necessary space for all the old files AND all the new files and copy/move all the files over. This is best performed using a Try Ubuntu boot flash drive.  In reality, as long as the files "appear" to be in the correct directory, with the correct owner, group, permissions and ACLs, where they are actually stored doesn't matter.

I think /home/ should be about 50G per userid, assuming they are full desktop users.  Media files should be stored elsewhere, IMHO, but snap packages don't like when files to be accessed are outside the HOME.

I cannot provide guidance about snap packages. I'm not prepared to deal with those at all, so that entire subsystem is purged from my machines.

I suppose the next step you might take is to figure out which directories are using most of the 14G of space on /.
Or
if your install is using a swapfile - probably in /, then you can disable that, create a swap partition almost anywhere else, and free up the storage the /swapfile was using.  That would be my first hope for solving something like this.  I'm not a fan of swapfiles.

---

### Post by TheFu on 2019-12-12
BTW, the first post says you want to use sda4, but there isn't any sda4.  What's up with that?

---

### Post by rsteinmetz70112 on 2019-12-13
I thin the OP was referring to /home/ not /home/user, but I can't figure our why the OP needs to move /home at all . According to the information posted it is only 1 % is used.

```
S.ficheros     Tipo    Tamaño Usados  Disp Uso% Montado en
/dev/sdb2      ext4       14G    12G  1,9G  86% /
/dev/sda2      vfat      296M    55M  242M  19% /boot/efi
/dev/sda1      ext4      441G   1,8G  417G   1% /home
/dev/sdc1      fuseblk   932G   520G  413G  56% /media/klays/DISCO
```

There are partitions not mounted;
```
sda    465,8G disk          
&#9500;&#9472;sda1 448,8G part ext4     /home
&#9500;&#9472;sda2   300M part vfat     /boot/efi
&#9500;&#9472;sda3   128M part          
&#9492;&#9472;sda5    16G part ntfs     
sdb     14,6G disk          
&#9500;&#9472;sdb1   512M part vfat     
&#9492;&#9472;sdb2  14,1G part ext4     /
sdc    931,5G disk          
&#9492;&#9472;sdc1 931,5G part ntfs     /media/klays/DISCO
```

Something I've done to expand a users home directory is to mount a partition as /home/user then allow other users to use /home for their home directories. 
The OP seems to need to reorganize his storage but I'm not sure of the point of this exercise. 

If it were me I'd simply get a new bigger hard drive and move everything there, a new 2TB drive should cost less than $40.00.

---

### Post by TheFu on 2019-12-13
I think the "HOME" move already happened, but old packages and a swapfile are eating into  the / partition.  /boot/ is nearly full, so older kernels need to be removed too:
```
sudo apt autoremove
sudo apt autoclean

```will clear out old packages and leave 2 old kernels. I haven't a clue how to remove old snaps which seem to hang around.  /boot/ under 500MB is scary to me. I prefer almost 1G for /boot/, but I've gotten into an ugly no-room-can't-install-new-kernel problem before.

And doing something about the swapfile in / would help too, if there is a swapfile there.

---

### Post by rsteinmetz70112 on 2019-12-14
> **TheFu said:**
> I think the "HOME" move already happened, but old packages and a swapfile are eating into  the / partition.  /boot/ is nearly full, so older kernels need to be removed too:
```
sudo apt autoremove
sudo apt autoclean

```will clear out old packages and leave 2 old kernels. I haven't a clue how to remove old snaps which seem to hang around.  /boot/ under 500MB is scary to me. I prefer almost 1G for /boot/, but I've gotten into an ugly no-room-can't-install-new-kernel problem before.

And doing something about the swapfile in / would help too, if there is a swapfile there.

I've had trouble with autoclean not removing old kernels, when they were from old upgrades. It's worth looking to see if there are old kernels hanging around. Removing the kernel packages sometimes leaves files in /boot. but once the underlying packages are gone deleting the files from /boot the updating grub should fix that.

---

### Post by TheFu on 2019-12-14
> **rsteinmetz70112 said:**
> I've had trouble with autoclean not removing old kernels, when they were from old upgrades. It's worth looking to see if there are old kernels hanging around. Removing the kernel packages sometimes leaves files in /boot. but once the underlying packages are gone deleting the files from /boot the updating grub should fix that.

NEVER delete files that are part of packages without using the package manager *remove* or *purge* function.
Old kernels from a prior release left over by upgrades can be manually removed using the package manager later. I like to wait 3-5 weeks (patch cycles) before doing that.  I patch weekly.

---

### Post by rsteinmetz70112 on 2019-12-16
> **TheFu said:**
> NEVER delete files that are part of packages without using the package manager *remove* or *purge* function.
Old kernels from a prior release left over by upgrades can be manually removed using the package manager later. I like to wait 3-5 weeks (patch cycles) before doing that.  I patch weekly.

I've at times been unable to remove files in /boot which were left behind when old kernels were removed. Neither 'purge" nor "remove" would remove them. I'm mostly talking about "initrd" and "config" files.  I've waited months and tried all sorts of stuff and still sometimes the files, are still left. In recent versions autoremove seems to be doing a better job.

---

### Post by TheFu on 2019-12-16
> **rsteinmetz70112 said:**
> I've at times been unable to remove files in /boot which were left behind when old kernels were removed. Neither 'purge" nor "remove" would remove them. I'm mostly talking about "initrd" and "config" files.  I've waited months and tried all sorts of stuff and still sometimes the files, are still left. In recent versions autoremove seems to be doing a better job.

Yep, I've been there too.

sudo apt autoremove is much better.

In the old days (14.04), I had a kernel-cleanup-script  [https://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](https://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) probably not very interesting anymore. It all started with a simple problem and finished with a simple script because I’m lazy.  Then I decided to make the script like I would for a client, not some hacked stuff.

---

