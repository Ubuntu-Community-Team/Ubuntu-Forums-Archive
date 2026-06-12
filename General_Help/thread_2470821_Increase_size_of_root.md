---
title: "Increase size of root"
date: 2022-01-12
forum: General Help
---

### Post by oygle on 2022-01-12
KUbuntu 20.04.3 LTS

I was doing a flatpack insall and it couldn't finish as there was insufficient space in root.

```
$ sudo du -hs /*
```

> 0       /bin
299M    /boot
4.0K    /cdrom
0       /dev
9.5M    /etc
263G    /home
0       /lib
0       /lib32
0       /lib64
0       /libx32
16K     /lost+found
12K     /media
4.0K    /mnt
791M    /opt
du: cannot access '/proc/16300/task/16300/fd/4': No such file or directory
du: cannot access '/proc/16300/task/16300/fdinfo/4': No such file or directory
du: cannot access '/proc/16300/fd/3': No such file or directory
du: cannot access '/proc/16300/fdinfo/3': No such file or directory
0       /proc
2.0M    /root
du: cannot access '/run/user/1000/doc': Permission denied
1.8M    /run
0       /sbin
5.8G    /snap
4.0K    /srv
0       /sys
140K    /tmp
7.8G    /usr
5.8G    /var


Have run the following and it released about 300 Mb

```
sudo apt-get clean
```

Possibly obtain some space here ..

```
$ journalctl --disk-usage
```

> Archived and active journals take up 344.0M in the file system.

Screendump from KDE Partition Manager attached

---

### Post by &amp;KyT$0P# on 2022-01-13
With only 16 GB / partition it's probably not a good idea to use both flatpak and snap.  Try to use only deb packages where possible.  debs have much less storage overhead than snaps and flatpaks (there was [a recent thread here about storage overhead of snap]("https://ubuntuforums.org/showthread.php?t=2470573") if you're interested in the details of why).

If you can't replace all your flatpaks/snaps with debs, maybe consider picking only one of flatpak or snap and uninstalling the other.

---

### Post by oygle on 2022-01-14
> **halogen2 said:**
> With only 16 GB / partition it's probably not a good idea to use both flatpak and snap.  Try to use only deb packages where possible.  debs have much less storage overhead than snaps and flatpaks (there was [a recent thread here about storage overhead of snap]("https://ubuntuforums.org/showthread.php?t=2470573") if you're interested in the details of why).

If you can't replace all your flatpaks/snaps with debs, maybe consider picking only one of flatpak or snap and uninstalling the other.

The problem I find with using the deb packages is that the documentation on a number of apps suggest _not to_. Simply because the DEB is unstable or out of date. Take Telegram desktop, the latest DEB is version 2.1.7 . So that is why it is suggested to install with Snap or Flatpak.  

That thread was interesting. here is what i got

```
$ sudo du -cha --max-depth=1 /snap | grep -E "M|G"
```

> [sudo] password for ********: 
4.0K    /snap/README
1.3G    /snap/gnome-3-28-1804
587M    /snap/youtube-dl
596M    /snap/core
678M    /snap/gtk-common-themes
338M    /snap/core18
305M    /snap/snapd
1.8G    /snap/telegram-desktop
395M    /snap/core20
5.8G    /snap
5.8G    total

```
$ snap list
```

> Name               Version                     Rev    Tracking       Publisher         Notes
bare               1.0                         5      latest/stable  canonical&#10003;        base
core               16-2.52.1                   11993  latest/stable  canonical&#10003;        core
core18             20211215                    2284   latest/stable  canonical&#10003;        base
core20             20211129                    1270   latest/stable  canonical&#10003;        base
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  161    latest/stable  canonical&#10003;        -
gtk-common-themes  0.1-59-g7bca6ae             1519   latest/stable  canonical&#10003;        -
snapd              2.53.4                      14295  latest/stable  canonical&#10003;        snapd
telegram-desktop   3.4.3                       3544   latest/stable  telegram.desktop  -
youtube-dl         2021.06.06+gita803582       4572   latest/stable  joeborg

Certainly SNAP is using up a lot of space. What can be deleted ?  For now I will d/load the tar/archive from [https://telegram.org/dl/desktop/linux](https://telegram.org/dl/desktop/linux) , it is the latest. There are no instructions so I assume I just untar and run 'Telegram'.  That is only 117 Mb, a far cry from the 1.8Gb now allocated when using Snap. So, once that's installed, I can use Snap to remove it.

Similar with Tor browser. That is when I got into trouble with disk space. It was using Flatpak, yet if I dowload the arhive/tar it is minimal space. Of course there is no automatic updating by **NOT** using a package manager, but at least I have the latest stable release. Synaptic has "tor-browser-launcher' but it is dated Sept 2020.

So I can easily see hwta snap has installed. I assume there is a similar command with Flatpak.

---

### Post by LuddDjur on 2022-01-14
This is a quite unusual partitioning setup. What I usually do when disk space does not fit:

boot the sysresccd: [https://www.system-rescue.org/](https://www.system-rescue.org/) after boot running "startx" to have a graphical interface and then start gparted.

In this setup you can also decrease partitions with ext4 filesystems (this is not easily possible when they are still mounted)

Suggestion would be to decrease size of your home partition -> delete the swap partition -> increase your root partition to something around 50G -> add swap partition.

Don't forget to mount the / partition within sysrescue and check your /etc/fstab to have the new swap partition mounted instead of the old one and the /home partition is mounted by UUID= instead of /dev/sda6

---

### Post by &amp;KyT$0P# on 2022-01-14
> **oygle said:**
> So I can easily see hwta snap has installed. I assume there is a similar command with Flatpak.

The equivalent of the output you posted for snap would be
```
flatpak list --all
```
Refer to [FONT=Courier New]man flatpak-list[/FONT] for more info.

To see total disk space taken by flatpaks, you can run
```
du -shx /var/lib/flatpak
```

For what it's worth, based on cursory [searching flathub]("https://flathub.org/home") I think the two actual apps you have installed as snaps are both also available as flatpaks.  If you have other flatpaks installed, and Tor browser is not available as a snap, and its tarball from official website does not have the internal updater like Firefox, you might check this.  Again, if you pick only one of flatpak or snap, you won't have two sets of runtimes taking up GBs of space in your / partition.

---

### Post by ActionParsnip on 2022-01-14
What is the output of:
```

df -h

```
Thanks

---

### Post by oygle on 2022-01-14
> **LuddDjur said:**
> This is a quite unusual partitioning setup. What I usually do when disk space does not fit:

boot the sysresccd: [https://www.system-rescue.org/](https://www.system-rescue.org/) after boot running "startx" to ....{SNIIP}


Thanks. Definitely I need to increase /root , and for now, short term, I'll see what can be done with snap/flatpak . I do have a live boot from **mkusb** , so I assume I can boot with that to make partition changes. Of course backup all the data first.

> **halogen2 said:**
> The equivalent of the output you posted for snap would be
```
flatpak list --all
```
Refer to [FONT=Courier New]man flatpak-list[/FONT] for more info.

To see total disk space taken by flatpaks, you can run
```
du -shx /var/lib/flatpak
```

{snip}


Thanks, here is what I got with htose two commands ..

```
flatpak list --all
```

> Name                   Application ID                                     Version          Branch              Installation
Mesa                   org.freedesktop.Platform.GL.default                21.3.3           21.08               system
nvidia-470-86          org.freedesktop.Platform.GL.nvidia-470-86                           1.4                 system
Intel                  org.freedesktop.Platform.VAAPI.Intel                                21.08               system
openh264               org.freedesktop.Platform.openh264                  2.1.0            2.0                 system
Adwaita theme          org.kde.KStyle.Adwaita                                              5.15-21.08          system
Locale                 org.kde.Platform.Locale                                             5.15-21.08          system

```
du -shx /var/lib/flatpak
```

> 1.6G    /var/lib/flatpak

I checked out  [searching flathub]("https://flathub.org/home") and will definitely use Flatpak to install Telegram Desktop and Tor browser, and also remove them from snap.

> **ActionParsnip said:**
> What is the output of:
```

df -h

```


> Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           787M  1.8M  785M   1% /run
/dev/sda1        17G   16G  346M  98% /
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0      128K  128K     0 100% /snap/bare/5
/dev/loop2      100M  100M     0 100% /snap/core/11993
/dev/loop1      100M  100M     0 100% /snap/core/11798
/dev/loop4       56M   56M     0 100% /snap/core18/2253
/dev/loop3       56M   56M     0 100% /snap/core18/2284
/dev/loop5       62M   62M     0 100% /snap/core20/1242
/dev/loop6       62M   62M     0 100% /snap/core20/1270
/dev/loop7      163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop10      43M   43M     0 100% /snap/snapd/14066
/dev/loop9       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop8      165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop12      44M   44M     0 100% /snap/snapd/14295
/dev/loop13      66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop11     324M  324M     0 100% /snap/telegram-desktop/3530
/dev/loop15      93M   93M     0 100% /snap/youtube-dl/4568
/dev/loop16      93M   93M     0 100% /snap/youtube-dl/4572
/dev/loop14     324M  324M     0 100% /snap/telegram-desktop/3544
/dev/sda6       895G  263G  587G  31% /home
tmpfs           787M   20K  787M   1% /run/user/1000

So, it seems using **SNAP** is almost like bloating out the disk space. Thanks @halogen2 for ref to that post -  [a recent thread here about storage overhead of snap]("https://ubuntuforums.org/showthread.php?t=2470573"). Even a mount command, there are a lot there referring to **snap** mounts

---

### Post by oygle on 2022-01-15
In the process of removing **SNAP** packages, but because of the disk space limitations on /root, and several attempts at removing **telegram-desktop** (ran out of disk space), I used this type of command initially

```
sudo snap remove telegram-desktop --revision=3530
```

and did it for all the other packages that had 'disabled' besides them. There was now 1.1 Gb free, so surely that was enough to remove telegram-desktop. It started the remove and was copying to some sort of '_snapshot'_ file and used up all the 1.1 Gb. Waiting for it to crash again, but fortunately it finished. By that stage, I was totally _over_ **SNAP**, so used [https://techwiser.com/remove-snap-ubuntu/](https://techwiser.com/remove-snap-ubuntu/) to clean up cache and remove everything else. Now there is 3.5 Gb free on /root

Will use either Flatpak or simply download tars/archives and follow instructions for the other packages that _were_ maintained by SNAP.. I would prefer everything to be simply under APT, but a lot of the .DEB's are old and unstable versions.

This quote - > It’s been hailed by Canonical and Ubuntu as the best package management and installation repository on Linux ..hmm.

---

### Post by DuckHook on 2022-01-16
> **oygle said:**
> The problem I find with using the deb packages is that the documentation on a number of apps suggest _not to_. Simply because the DEB is unstable or out of date. Take Telegram desktop, the latest DEB is version 2.1.7 . So that is why it is suggested to install with Snap or Flatpak.

> **oygle said:**
> …Will use either Flatpak or simply download tars/archives and follow instructions for the other packages that _were_ maintained by SNAP.. I would prefer everything to be simply under APT, but a lot of the .DEB's are old and unstable versions.
I got here from your update to that other thread. The Telegram PPA is: [https://launchpad.net/~atareao/+archive/ubuntu/telegram](https://launchpad.net/~atareao/+archive/ubuntu/telegram)

The usual caveats apply: use at your own risk, research the PPA maintainers, yada-yada-yada…

Good Luck and Happy Ubuntu-ing!

---

### Post by oygle on 2022-01-23
> **DuckHook said:**
> I got here from your update to that other thread. The Telegram PPA is: [https://launchpad.net/~atareao/+archive/ubuntu/telegram](https://launchpad.net/~atareao/+archive/ubuntu/telegram)


Thanks, I'll take a look at that.

---

