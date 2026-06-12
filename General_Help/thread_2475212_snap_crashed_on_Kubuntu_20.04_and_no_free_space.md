---
title: "snap crashed on Kubuntu 20.04 and no free space"
date: 2022-05-19
forum: General Help
---

### Post by kunzhut on 2022-05-19
Hi, everyone!


I have Kubuntu 20.04 and recently I encountered a situation where there was no more free space on the disk.

There I have 2 partitions: sda2 (37GB) and sda3 (197GB)

After ```
df -h
```
```
Filesystem      Size  Used Avail Use% Mounted on
udev            7,7G     0  7,7G   0% /dev
tmpfs           1,6G   51M  1,5G   4% /run
/dev/sda2        37G   35G     0 100% /
tmpfs           7,8G  239M  7,5G   4% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           7,8G     0  7,8G   0% /sys/fs/cgroup
/dev/loop3      111M  111M     0 100% /snap/core/12834
/dev/loop2      128K  128K     0 100% /snap/acrordrdc/62
/dev/loop4      112M  112M     0 100% /snap/core/12941
/dev/loop1      133M  133M     0 100% /snap/chromium/1993
/dev/loop5       56M   56M     0 100% /snap/core18/2409
/dev/loop0      128K  128K     0 100% /snap/bare/5
/dev/loop6       18M   18M     0 100% /snap/chromium-ffmpeg/24
/dev/loop7       62M   62M     0 100% /snap/core20/1405
/dev/loop8      133M  133M     0 100% /snap/chromium/1985
/dev/loop9      249M  249M     0 100% /snap/gnome-3-38-2004/99
/dev/loop11      66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop13     170M  170M     0 100% /snap/spotify/58
/dev/loop14      67M   67M     0 100% /snap/walc/19
/dev/loop15      83M   83M     0 100% /snap/whatsdesk/25
/dev/loop16      44M   44M     0 100% /snap/snapd/15177
/dev/loop17     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop19      73M   73M     0 100% /snap/youtube-music-desktop-app/6
/dev/loop20     323M  323M     0 100% /snap/wine-platform-6-stable/14
/dev/loop21     153M  153M     0 100% /snap/skype/209
/dev/loop18      83M   83M     0 100% /snap/whatsdesk/28
/dev/loop22     248M  248M     0 100% /snap/gnome-3-38-2004/87
/dev/loop23     918M  918M     0 100% /snap/libreoffice/254
/dev/loop24     347M  347M     0 100% /snap/wine-platform-runtime/298
/dev/loop25      62M   62M     0 100% /snap/core20/1434
/dev/loop26      56M   56M     0 100% /snap/core18/2344
/dev/loop27      45M   45M     0 100% /snap/snapd/15534
/dev/loop28     170M  170M     0 100% /snap/spotify/60
/dev/loop29     161M  161M     0 100% /snap/opera/176
/dev/loop31     165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop30     153M  153M     0 100% /snap/skype/206
/dev/loop32     323M  323M     0 100% /snap/wine-platform-6-stable/19
/dev/loop33      72M   72M     0 100% /snap/walc/17
/dev/loop34     626M  626M     0 100% /snap/libreoffice/250
/dev/loop35      23M   23M     0 100% /snap/chromium-ffmpeg/26
/dev/loop36      66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/sda1       476M  5,3M  470M   2% /boot/efi
/dev/sda3       197G   75G  112G  40% /home
tmpfs           1,6G   28K  1,6G   1% /run/user/1000
/dev/loop37     347M  347M     0 100% /snap/wine-platform-runtime/299
/dev/loop12     162M  162M     0 100% /snap/opera/177

```
After ```
sudo du -sh /*
```
```
0       /0
0       /bin
2,6G    /boot
4,0K    /cdrom
0       /dev
14M     /etc
75G     /home
0       /lib
0       /lib32
0       /lib64
0       /libx32
16K     /lost+found
24K     /media
4,0K    /mnt
2,0G    /opt
4,0K    /packages.expandrive.gpg
0       /proc
94M     /root
51M     /run
0       /sbin
19G     /snap
4,0K    /srv
1,8G    /swapfile
0       /sys
303M    /timeshift
5,5M    /tmp
20G     /usr
8,4G    /var

```
I've seen that my **/snap** weights **19GB** and I wanted to remove it to **sda3(/home)** and make a link with it. 

I made 
```
sudo mv /snap /home/snap
ln -s /home/snap /snap

```
Checking: ```
ls -la /

```
```
lrwxrwxrwx   1 root root         snap -> /home/snap

```
And after that, which is very surprising on **sda2** did not appear more free space:
```
pydf
```
```
Filesystem  Size  Used Avail Use%              Mounted on                                         
/dev/sda2    36G   32G 2370M 88.5 [#########.] /                                                  
/dev/sda1   475M 5356k  470M  1.1 [..........] /boot/efi                                          
/dev/sda3   197G   45G  142G 22.8 [##........] /home                                              
/dev/sdb2  2705G   74G 2494G  2.7 [..........] /media/zephyr/c0166034-738b-483a-b012-e4593a9a36991
/dev/sdb2  2705G   74G 2494G  2.7 [..........] /run/timeshift/backup                              
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_2yNIqG                            
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_6C3MMF                            
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_80WMVW                            
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_PhovB1                            
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_UpT73j                            
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_lXNz2g                            
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_mjn9Kw                            
/dev/sda2    36G   32G 2370M 88.5 [#########.] /tmp/snap.rootfs_uf53ft 

```
(some free space freed up after 
```
sudo apt autoremove
sudo apt autoclean

```but just a few GB not 19GB) 
And I've lost few my applications: Spotify, YouTube Music, Skype, WhatsApp (their icons disappeared after reboot), they aren't launch and:
```
snap list --all | grep spotify
``` return nothing
Some of my apps from **/snap** are working: Chrome, Opera, but anyway:
```
snap list --all | grep opera

```return 
```
opera - 177 latest/stable  opera-software*  broken

```
As I understtod, these **19GB** are splitted in these 8 parties by **2370Mb** and when I tryed to erase it: 
```
sudo rm -rf /tmp/snap.rootfs_2yNIqG/
```
I had 
```
rm: cannot remove '/tmp/snap.rootfs_2yNIqG/': Device or resource busy
```
Right now I still have the same situation with not enough free space on **sda2** (where is my **19 GB**?) and I can't re-install Spotify from Discover application, for example.

Guys, any ideas what can do useful in this case? Is this possible to get back these apps and solve not enough space problem on **sda2**?
Thanks in advance!

---

### Post by Impavidus on 2022-05-19
Nothing is stored in /snap. /snap is used as a mountpoint for your snaps, but the actual disk space of those snaps is in /var – and as they are compressed, the storage they need in /var is less than their apparent size in /snap. It must be around 8GB. After moving /snap, the snap applications can no longer be found.

More remarkable is your /usr at 20GB. It's usually closer to 10GB. You must have quite a lot there.

---

### Post by SeijiSensei on 2022-05-19
You didn't include /var in that list. Often /var/log can be large if either you have recurring hardware issues or the logs aren't rotated with something like logrotate.  How big is /var?

On a recent installation of KDE Neon, which uses 20.04 as the base, I have about 9 GB in /usr. I'd run "cd /var; du -s *" to see what's hiding in there.

---

### Post by kunzhut on 2022-05-19
> **Impavidus said:**
> After moving /snap, the snap applications can no longer be found.
And I can't re-move /snap back on /sda2, bcz there are just 2.3GB free, but /snap is 19GB.

> **SeijiSensei said:**
> How big is /var?
8.4GB
> **SeijiSensei said:**
> I'd run "cd /var; du -s *" to see what's hiding in there.
```
[FONT=monospace][COLOR=#000000]du: cannot read directory './spool/rsyslog': Permission denied[/COLOR]
du: cannot read directory './spool/cups': Permission denied
du: cannot read directory './spool/cron/crontabs': Permission denied
du: cannot read directory './log/cups': Permission denied
du: cannot read directory './log/private': Permission denied
du: cannot read directory './log/samba/cores': Permission denied
du: cannot read directory './tmp/systemd-private-4960bc7d1c624d688bed32ccfb76ca65-systemd-resolved.service-zR
mf4i': Permission denied
du: cannot read directory './tmp/systemd-private-4960bc7d1c624d688bed32ccfb76ca65-ModemManager.service-ddpepi
': Permission denied
du: cannot read directory './tmp/systemd-private-4960bc7d1c624d688bed32ccfb76ca65-systemd-logind.service-01Vk
Ah': Permission denied
du: cannot read directory './tmp/systemd-private-4960bc7d1c624d688bed32ccfb76ca65-haveged.service-eNip8i': Pe
rmission denied
du: cannot read directory './tmp/systemd-private-4960bc7d1c624d688bed32ccfb76ca65-switcheroo-control.service-
2ugqHg': Permission denied
du: cannot read directory './tmp/systemd-private-4960bc7d1c624d688bed32ccfb76ca65-upower.service-dl9pji': Per
mission denied
du: cannot read directory './tmp/systemd-private-4960bc7d1c624d688bed32ccfb76ca65-systemd-timesyncd.service-Z
cM9li': Permission denied
du: cannot read directory './cache/apt/archives/partial': Permission denied
du: cannot read directory './cache/apparmor/26b63962.0': Permission denied
du: cannot read directory './cache/cups': Permission denied
du: cannot read directory './cache/ldconfig': Permission denied
du: cannot read directory './cache/private': Permission denied
du: cannot read directory './lib/apt/lists/partial': Permission denied
du: cannot read directory './lib/colord/.cache': Permission denied
du: cannot read directory './lib/AccountsService/users': Permission denied
du: cannot read directory './lib/mysql': Permission denied
du: cannot read directory './lib/mysql-files': Permission denied
du: cannot read directory './lib/NetworkManager': Permission denied
du: cannot read directory './lib/update-notifier/package-data-downloads/partial': Permission denied
du: cannot read directory './lib/mysql-keyring': Permission denied
du: cannot read directory './lib/private': Permission denied
du: cannot read directory './lib/sddm': Permission denied
du: cannot read directory './lib/polkit-1': Permission denied
du: cannot read directory './lib/bluetooth/D4:6A:6A:DF:05:14': Permission denied
du: cannot read directory './lib/snapd/snapshots': Permission denied
du: cannot read directory './lib/snapd/cache': Permission denied
du: cannot read directory './lib/snapd/cookie': Permission denied
du: cannot read directory './lib/snapd/void': Permission denied
du: cannot read directory './lib/udisks2': Permission denied
du: cannot read directory './lib/strongswan': Permission denied
du: cannot read directory './lib/fwupd/gnupg': Permission denied
du: cannot read directory './lib/samba/winbindd_privileged': Permission denied
du: cannot read directory './lib/samba/private/msg.sock': Permission denied
du: cannot read directory './lib/lightdm': Permission denied
du: cannot read directory './lib/ubuntu-advantage/private': Permission denied
4135932 .
[/FONT]
```

---

### Post by Impavidus on 2022-05-19
> **kunzhut said:**
> And I can't re-move /snap back on /sda2, bcz there are just 2.3GB free, but /snap is 19GB.No, /snap is really (mostly) empty. Just as you gained no free space by moving it to /home, it won't cost you free space if you move it back.

Try the other command with sudo:```
sudo du -sk /var/*
```But I'm also interested in /usr, which is remarkably large:```
du -sk /usr/*
```

---

### Post by TheFu on 2022-05-19
Appreciate the data, but it has a bunch of junk.  Let's get exactly the stuff we need and not the other junk.

```
df -hT -x squashfs -x tmpfs -x devtmpfs
du -sh /* |sort -h
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Loop mounts don't use storage.  They point at already used locations on real storage.
Sorting output let's us ignore trivial areas.  That's what the du command above does well.
If the system was installed in 20.04 or later, you probably have a swapfile using space in / that just isn't needed there. If you have other storage, you can either move that swapfile there or switch back to the swap partition/LVM-LV method and never worry about it again.  GPT partitioning removed the dumb limitation on primary partitions, so there really isn't any need to have swapfiles.

Anyway, you have some options.

Almost everything related to snaps is hardcoded and they won't work if moved. Beware. Unless the snaps are single-user installed, not system-installed.

/var on my 22.04 system is 367M. If you don't have any virtual machines, there is little reason to allow var larger than 2G.

---

### Post by kunzhut on 2022-05-19
> **Impavidus said:**
> Just as you gained no free space by moving it to /home, it won't cost you free space if you move it back.
But, anyway, when I've tried to copy it back via Midnight Commander after sudo and after some time I had error «No more free space», something like that.
> **Impavidus said:**
> Try the other command with sudo:```
sudo du -sk /var/*
```
```
[FONT=monospace][COLOR=#000000]8036    /var/backups[/COLOR]
232304  /var/cache
4       /var/crash
6776952 /var/lib
4       /var/local
0       /var/lock
7468    /var/log
4       /var/mail
4       /var/metrics
4       /var/opt
0       /var/run
11532   /var/snap
52      /var/spool
60      /var/tmp[/FONT]
```
> **Impavidus said:**
> But I'm also interested in /usr, which is remarkably large:```
du -sk /usr/*
```
```
[FONT=monospace][COLOR=#000000]544560  /usr/bin[/COLOR]
2320    /usr/games
24848   /usr/include
12855524        /usr/lib
4       /usr/lib32
16      /usr/lib64
15864   /usr/libexec
4       /usr/libx32
116     /usr/local
101340  /usr/sbin
2435164 /usr/share
3523896 /usr/src[/FONT]
``` 
> **TheFu said:**
> 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
```
[FONT=monospace][COLOR=#000000]Filesystem     Type     Size  Used Avail Use% Mounted on[/COLOR]
/dev/sda2      ext4      37G   33G  2,3G  94% /
/dev/sda1      vfat     476M  5,3M  470M   2% /boot/efi
/dev/sda3      ext4     197G   45G  142G  25% /home
/dev/sdb2      ext4     2,7T   74G  2,5T   3% /run/timeshift/backup
/dev/sdb1      fuseblk  977G  322G  656G  33% /media/zephyr/My Passport1[/FONT]
``` 
> **TheFu said:**
> ```
du -sh /* |sort -h lsblk -e 7 -o name,size,type,fstype,mountpoint
```
```
[FONT=monospace][COLOR=#000000]sort: invalid option -- 'e'[/COLOR]
Try 'sort --help' for more information.
du: cannot read directory '/boot/efi': Permission denied[/FONT]
```

> **TheFu said:**
> 
If the system was installed in 20.04 or later, you probably have a swapfile using space in / that just isn't needed there. If you have other storage, you can either move that swapfile there or switch back to the swap partition/LVM-LV method and never worry about it again.  GPT partitioning removed the dumb limitation on primary partitions, so there really isn't any need to have swapfiles.

I made ```
sudo swapoff -a && sudo swapon -a
``` but anyway in my / is located 1.7 GB swapfile. 
> **TheFu said:**
> If you don't have any virtual machines, there is little reason to allow var larger than 2G.
I had VirtualBox but uninstall it before these operations.

---

### Post by TheFu on 2022-05-19
> **kunzhut said:**
> 
```
[FONT=monospace][COLOR=#000000]sort: invalid option -- 'e'[/COLOR]
Try 'sort --help' for more information.
du: cannot read directory '/boot/efi': Permission denied[/FONT]
```


I made ```
sudo swapoff -a && sudo swapon -a
``` but anyway in my / is located 1.7 GB swapfile. 

I had VirtualBox but uninstall it before these operations.

When I look at my post, I see 3 separate lines, not 2.  Somehow, in your use, the lsblk was merged with the command on the line above. That isn't correct. Should be 2 separate lines.
```
du -sh /* |sort -h

lsblk -e 7 -o name,size,type,fstype,mountpoint
```
These commands make it easier to zoom in on the issues. Other posters have manually done that already, probably.  I like to have the computer sort things for me so my stupid human brain doesn't get confused.

Disabling and re-enabling swap doesn't do anything but waste time. If you don't move the swapfile and fix the /etc/fstab, it wasn't helpful.

Virtualbox puts VMs into a HOME directory, doesn't it?  Other hypervisors like Xen or KVM with libvirt use /var/lib/libvirt/ for VM storage if file-based VMs are used. It is an enterprise vs hobbyist difference.

---

### Post by kunzhut on 2022-05-19
> **TheFu said:**
> Should be 2 separate lines. Oh, yeah, my bad.
> **TheFu said:**
> ```
du -sh /* |sort -h
```
```
[FONT=monospace][COLOR=#000000]du: cannot read directory '/boot/efi': Permission denied[/COLOR]
du: cannot read directory '/dev/vboxusb': Permission denied
du: cannot read directory '/etc/ipsec.d/private': Permission denied
du: cannot read directory '/etc/ssl/private': Permission denied
du: cannot read directory '/etc/cups/ssl': Permission denied
du: cannot read directory '/etc/polkit-1/localauthority': Permission denied
du: cannot read directory '/home/lost+found': Permission denied
du: cannot read directory '/home/snap/core18/2344/var/cache/ldconfig': Permission denied
du: cannot read directory '/home/snap/core18/2344/var/lib/private': Permission denied
du: cannot read directory '/home/snap/core18/2344/root': Permission denied
du: cannot read directory '/home/snap/core18/2344/etc/ssl/private': Permission denied
du: cannot read directory '/home/snap/core18/2409/var/cache/ldconfig': Permission denied
du: cannot read directory '/home/snap/core18/2409/var/lib/private': Permission denied
du: cannot read directory '/home/snap/core18/2409/root': Permission denied
du: cannot read directory '/home/snap/core18/2409/etc/ssl/private': Permission denied
du: cannot read directory '/home/snap/core20/1405/var/cache/private': Permission denied
du: cannot read directory '/home/snap/core20/1405/var/cache/ldconfig': Permission denied
du: cannot read directory '/home/snap/core20/1405/var/lib/private': Permission denied
du: cannot read directory '/home/snap/core20/1405/var/lib/snapd/void': Permission denied
du: cannot read directory '/home/snap/core20/1405/root': Permission denied
du: cannot read directory '/home/snap/core20/1405/etc/ssl/private': Permission denied
du: cannot read directory '/home/snap/core20/1434/var/cache/private': Permission denied
du: cannot read directory '/home/snap/core20/1434/var/cache/ldconfig': Permission denied
du: cannot read directory '/home/snap/core20/1434/var/lib/private': Permission denied
du: cannot read directory '/home/snap/core20/1434/var/lib/snapd/void': Permission denied
du: cannot read directory '/home/snap/core20/1434/root': Permission denied
du: cannot read directory '/home/snap/core20/1434/etc/ssl/private': Permission denied
du: cannot read directory '/home/snap/core/12941/var/cache/ldconfig': Permission denied
du: cannot read directory '/home/snap/core/12941/var/spool/cron/crontabs': Permission denied
du: cannot read directory '/home/snap/core/12941/var/spool/rsyslog': Permission denied
du: cannot read directory '/home/snap/core/12941/var/lib/private': Permission denied
du: cannot read directory '/home/snap/core/12941/var/lib/waagent': Permission denied
du: cannot read directory '/home/snap/core/12941/var/lib/snapd/void': Permission denied
du: cannot read directory '/home/snap/core/12941/var/lib/machines': Permission denied
du: cannot read directory '/home/snap/core/12941/root': Permission denied
du: cannot read directory '/home/snap/core/12941/etc/ssl/private': Permission denied
du: cannot read directory '/home/snap/core/12834/var/cache/ldconfig': Permission denied
du: cannot read directory '/home/snap/core/12834/var/spool/cron/crontabs': Permission denied
du: cannot read directory '/home/snap/core/12834/var/spool/rsyslog': Permission denied
du: cannot read directory '/home/snap/core/12834/var/lib/private': Permission denied
du: cannot read directory '/home/snap/core/12834/var/lib/waagent': Permission denied
du: cannot read directory '/home/snap/core/12834/var/lib/snapd/void': Permission denied
du: cannot read directory '/home/snap/core/12834/var/lib/machines': Permission denied
du: cannot read directory '/home/snap/core/12834/root': Permission denied
du: cannot read directory '/home/snap/core/12834/etc/ssl/private': Permission denied
du: cannot read directory '/lost+found': Permission denied
du: cannot read directory '/media/zephyr/My Passport': Permission denied
du: cannot read directory '/media/zephyr/c0166034-738b-483a-b012-e4593a9a3699': Permission denied
du: cannot read directory '/media/zephyr/AOMEI_PE': Permission denied
du: cannot read directory '/media/zephyr/c0166034-738b-483a-b012-e4593a9a36991/lost+found': Permission denied
du: cannot read directory '/media/zephyr/c0166034-738b-483a-b012-e4593a9a36991/timeshift/snapshots/2022-02-14
_21-00-01/localhost/boot/efi': Permission denied
du: cannot read directory '/media/zephyr/c0166034-738b-483a-b012-e4593a9a36991/timeshift/snapshots/2022-02-14
_21-00-01/localhost/root': Permission denied[/FONT]
```
> **TheFu said:**
> ```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
```
[FONT=monospace][COLOR=#000000]NAME     SIZE TYPE FSTYPE MOUNTPOINT[/COLOR]
sda    238,5G disk         
&#9500;&#9472;sda1   476M part vfat   /boot/efi
&#9500;&#9472;sda2  37,3G part ext4   /
&#9492;&#9472;sda3 200,8G part ext4   /home
sdb      3,7T disk         
&#9500;&#9472;sdb1 976,6G part ntfs   /media/zephyr/My Passport1
&#9492;&#9472;sdb2   2,7T part ext4   /run/timeshift/backup[/FONT]
```

---

### Post by deadflowr on 2022-05-19
Your /boot is huge for some reason.

---

### Post by Impavidus on 2022-05-20
> **kunzhut said:**
> But, anyway, when I've tried to copy it back via Midnight Commander after sudo and after some time I had error «No more free space», something like that.I suppose that Midnight Commander isn't smart enough to move mountpoints, so it may have made a full copy. I don't use snaps myself, so I can't test this, but maybe it works if you delete /snap (the symlink or directory, whatever it is now), reinstall snapd and reboot. Maybe it will properly rebuild whatever was in /snap. Or you may have to reinstall the snaps too.
> 
```
[FONT=monospace]6776952 /var/lib[/FONT]
```Almost 7GB in /var/lib. That is the real storage used by those snap packages. Not much you can do about it, other than removing some.
> 
```
[FONT=monospace][COLOR=#000000]544560  /usr/bin[/COLOR]
2320    /usr/games
24848   /usr/include
**[COLOR=red]12855524        /usr/lib[/COLOR]**
4       /usr/lib32
16      /usr/lib64
15864   /usr/libexec
4       /usr/libx32
116     /usr/local
**[COLOR=red]101340  /usr/sbin[/COLOR]**
2435164 /usr/share
**[COLOR=red]3523896 /usr/src[/COLOR]**[/FONT]
```I highlighted the lines that appear remarkably large: your /usr/lib is almost 3 times what I've got, your /usr/sbin too and your /usr/src is even 12 times what I've got. You may have some old packages that you can remove.

---

### Post by kunzhut on 2022-05-20
Thanks for all, guys, for your help!

What I did: 

1. Uninstalled snapd 
```
sudo snap remove chromium snap-store
sudo systemctl stop snapd
sudo apt remove --purge --assume-yes snapd gnome-software-plugin-snap
rm -rf ~/snap/
sudo rm -rf /var/cache/snapd/
```

2. Installed snap
```
snap install
```

3. Installed from [https://snapcraft.io/store](https://snapcraft.io/store) all apps I needed (Spotify, Skype, WhatsApp etc.)
```
sudo snap install spotify
```

4. Rebooted, and after that everything worked well! Right now I have 7GB/37GB free and it's enough.
5. Next step will be removing swapfile (1.7GB)

---

### Post by TheFu on 2022-05-20
> **kunzhut said:**
> 
5. Next step will be removing swapfile (1.7GB)

You probably don't want to remove it. Instead just relocate it to different storage.  If this is a desktop, you'll likely want to make it 4.1G to handle modern browsers being swapped out.  In my testing of Ubuntu desktop/laptop computers with 2, 4, 6, 8, 16 and 32G of RAM, I found that less than 4G of swap was bad, sometimes crashing, for systems with 8G or less RAM.  As more RAM is added, whether a system needed a larger swap depended on the RAM demands based on workload.  I run virtual machines and linux containers, so having the system become slower as memory over-commits happen during swap use periods is a good hint that I need to close some programs. With that slowness in the system, I can "feel" this slowdown before it becomes bad enough to crash.

Of course, if you have 16G or more of RAM and don't run memory intensive programs, then a smaller swap area could be fine.  Some swap, say 1G is what I do on servers that shouldn't need any swap at all, but having a little bit is actually helpful to system performance because some kernel code for performance is only enabled if swap exists.  Perhaps I could make that 500MB. Hummmm.  This applies to extremely well-known workloads on servers, not for desktops running desktop applications.
[https://haydenjames.io/linux-performance-almost-always-add-swap-space/](https://haydenjames.io/linux-performance-almost-always-add-swap-space/)

---

### Post by kunzhut on 2022-05-20
I have a i5-laptop with 16 GB RAM and most heaviest apps I will have to use is VirtualBox for access to Windows-world (likely Photoshop-world).
Do I need swap in my case?

---

### Post by Impavidus on 2022-05-20
> **kunzhut said:**
> 4. Rebooted, and after that everything worked well! Right now I have 7GB/37GB free and it's enough.
You only really removed some unneeded or duplicate snaps (old versions). After some updates, the problem will be back.

I suggest you have a look at deb packages you no longer need. Most of /usr/lib, /usr/sbin and /usr/src is filled from deb packages. Maybe there are some old kernels or kernel headers that can be autoremoved.

---

### Post by TheFu on 2022-05-20
> **kunzhut said:**
> I have a i5-laptop with 16 GB RAM and most heaviest apps I will have to use is VirtualBox for access to Windows-world (likely Photoshop-world).
Do I need swap in my case?

Probably.  Hard to tell from the information provided. How much RAM gets used peak over each month?

---

### Post by kunzhut on 2022-05-22
> **Impavidus said:**
> 
I suggest you have a look at deb packages you no longer need. Most of /usr/lib, /usr/sbin and /usr/src is filled from deb packages. Maybe there are some old kernels or kernel headers that can be autoremoved.
Thanks, I will.

---

### Post by kunzhut on 2022-05-22
> **TheFu said:**
> Probably.  Hard to tell from the information provided. How much RAM gets used peak over each month?
My clear loaded system without ordinary apps weights 1GB RAM, with Telegram+Viber+WhatsApp+Chrome(many pages opened)+Opera+Spotify it will be 7GB/16GB.
When I quite rare want VirtualBox for Windows 7 I have to close browsers.

---

### Post by TheFu on 2022-05-22
> **kunzhut said:**
> My clear loaded system without ordinary apps weights 1GB RAM, with Telegram+Viber+WhatsApp+Chrome(many pages opened)+Opera+Spotify it will be 7GB/16GB.
When I quite rare want VirtualBox for Windows 7 I have to close browsers.

Seem like a 4.1G swap would be reasonable, then.  Or the resources provided to the VM can be less.  I find that most Windows people over think how much RAM is needed for Windows to run.  I give my Win7 VM just 1.5G of RAM under kvm. Never had any issues. For years, it was running Windows Media Center.

---

