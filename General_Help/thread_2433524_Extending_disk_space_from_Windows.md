---
title: "Extending disk space from Windows"
date: 2019-12-20
forum: General Help
---

### Post by flex567 on 2019-12-20
I have dual boot installation of Windows and Ubuntu. For ubunt I have reserved space of ~100GB and the rest for windows.

Now I would like to expand my storage space for Ubuntu and would like to take away from Windows.

I would like to expand the root partition on Ubuntu (see image below)

How can I expand my storage space?

I am receiving messages from the system that storage is low and on the image I have marked what I believe is the issue.

---

### Post by TheFu on 2019-12-20
When it comes to expanding a partition, the physical disk layout matters.  This applies to NVMe too, even though the actual storage layout is really 100% logical, but the OS and users don't have a few into which storage chips are actually being used.

```
sudo parted -l
```
is what we need to see, wrapped in code tags so the columns line up.  If the install used LVM, it would be easier.  Expanding an LV, assuming the VG has empty storage, is 5 seconds of effort and not really tied to physical storage layout.

---

### Post by Holger_Gehrke on 2019-12-20
While resizing partitions and file systems can be done, I'd first clean up a bit and see whether this clears up the problem. From the image you posted I can see that you have several large applications installed as snaps. snap keeps at least one old version of an application on disk when it updates in case the new version doesn't work. Removing the older versions of various snaps should free up about 1G-1.5G. The classic apt package manager also keeps a cache which keeps on growing. Cleaning that out can also clear up a lot of space.
```

snap remove --revision 1313 gtk-common-themes
snap remove --revision 91 gnome-3-28-1804
snap remove --revision 107 gnome-system-monitor
snap remove --revision 536 gnome-calculator
snap remove --revision 359 gnome-characters
snap remove --revision 73 gnome-logs
snap remove --revision 8213 core
snap remove --revision 130 phpstorm
snap remove --revision 188 intellij-idea-ultimate
snap remove --revision 1279 core18

```
Should remove the older snap-revisions. Check the revision numbers I've given against the output of 'snap list -all' before executing these. The ones to remove should be marked as 'deactivated' (or words to that effect) in the column 'Notes'
```

sudo apt-get clean

```
This will clean out the package cache from /var/cache/apt/archives.
Taken together these should free up 2 G or more of space on your root. Since the root partition is 22 G of the ~100 G that should give you more than 20% free disk space. 

Another thing to look at could be the logs in /var/log. The various text logs shouldn't take more than a hundred or so megabytes, but the journal is by default set to take up to 4 GB. You can use journalctl with the option --vacuum-size= to reduce the space currently used and edit /etc/systemd/journald.conf to set a limit that's more appropriate. See the manual pages for journalctl and journald.conf for details.

Holger

---

### Post by TheFu on 2019-12-20
Excellent ideas Holger.  Definitely to that stuff first.

---

### Post by flex567 on 2019-12-20
this allready looks a bit better.

But I think I could expand it a bit more as I don't really use windows at all.

---

### Post by TheFu on 2019-12-20
a) please use code tags when posting here.  Images are a waste when text is available.  We can copy/paste text into our answers, but not images.
It is easy to do, but harder to explain. How-to .... [https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

b) boot into Windows.  Run a defrag job on all the Windows partitions.  However that is done. 

c) Inside Windows, reduce the size of the Windows partitions. Do not touch any Linux partitions.

d) Because of the way things are laid out, if you want to add a quick 8GB, you can move the Linux swap partition, then use that storage which is after the OS partition for more OS space.  It is also a good time to rethink the current size of swap.  In my world, 4.1GB is the only size for swap on any desktop.  I do not hibernate. If you do, then your swap size needs to be 1.1x the size of RAM.  

Text with code tags, please.

---

### Post by flex567 on 2020-02-16
I would like to delete the flatpak folder but I am not sure if it is safe to delete it. Is this folder system related or can I just delete it. It takes 2 GB which I would really need.

How do I delete the folder(flatpak) and its related folders/files and is it safe to delete it?

```

sudo du -h --max-depth=1 /var/lib/ | sort -rh
8,2G    /var/lib/
5,0G    /var/lib/snapd
2,7G    /var/lib/flatpak
314M    /var/lib/docker
168M    /var/lib/apt
73M    /var/lib/dpkg
18M    /var/lib/app-info
4,1M    /var/lib/aspell
3,0M    /var/lib/command-not-found
1,7M    /var/lib/gdm3
1,3M    /var/lib/dkms
688K    /var/lib/systemd
604K    /var/lib/usbutils
384K    /var/lib/ucf
328K    /var/lib/fwupd
148K    /var/lib/containerd
140K    /var/lib/NetworkManager
84K    /var/lib/libvirt
76K    /var/lib/php
64K    /var/lib/polkit-1
56K    /var/lib/colord
44K    /var/lib/PackageKit
36K    /var/lib/upower
36K    /var/lib/ghostscript
32K    /var/lib/dictionaries-common
32K    /var/lib/apache2
28K    /var/lib/pam
24K    /var/lib/update-notifier
24K    /var/lib/shim-signed
24K    /var/lib/emacsen-common
20K    /var/lib/update-manager
20K    /var/lib/binfmts
20K    /var/lib/AccountsService
16K    /var/lib/nfs
16K    /var/lib/libreoffice
16K    /var/lib/gconf
16K    /var/lib/boltd
12K    /var/lib/ubuntu-fan
12K    /var/lib/openvpn
12K    /var/lib/locales
12K    /var/lib/initramfs-tools
12K    /var/lib/grub
8,0K    /var/lib/xkb
8,0K    /var/lib/xfonts
8,0K    /var/lib/whoopsie
8,0K    /var/lib/vim
8,0K    /var/lib/ubuntu-drivers-common
8,0K    /var/lib/ubuntu-advantage
8,0K    /var/lib/ubiquity
8,0K    /var/lib/sudo
8,0K    /var/lib/plymouth
8,0K    /var/lib/os-prober
8,0K    /var/lib/logrotate
8,0K    /var/lib/ispell
8,0K    /var/lib/gems
8,0K    /var/lib/docker-engine
8,0K    /var/lib/bluetooth
4,0K    /var/lib/usb_modeswitch
4,0K    /var/lib/unattended-upgrades
4,0K    /var/lib/udisks2
4,0K    /var/lib/ubuntu-release-upgrader
4,0K    /var/lib/snmp
4,0K    /var/lib/rpm
4,0K    /var/lib/python
4,0K    /var/lib/private
4,0K    /var/lib/misc
4,0K    /var/lib/man-db
4,0K    /var/lib/hp
4,0K    /var/lib/git
4,0K    /var/lib/geoclue
4,0K    /var/lib/fprint
4,0K    /var/lib/dhcp
4,0K    /var/lib/dbus
4,0K    /var/lib/BrlAPI
4,0K    /var/lib/avahi-autoipd
4,0K    /var/lib/alsa
4,0K    /var/lib/acpi-support

```

The main problem
```

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7,7G     0  7,7G   0% /dev
tmpfs           1,6G  2,1M  1,6G   1% /run
/dev/nvme0n1p5   20G   18G  1,5G  93% / <--- this line
tmpfs           7,7G  279M  7,5G   4% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           7,7G     0  7,7G   0% /sys/fs/cgroup
/dev/loop4       92M   92M     0 100% /snap/core/8592
/dev/loop2      3,8M  3,8M     0 100% /snap/gnome-system-monitor/127
/dev/loop3      3,8M  3,8M     0 100% /snap/gnome-system-monitor/123
/dev/loop1       15M   15M     0 100% /snap/gnome-characters/375
/dev/loop6      728M  728M     0 100% /snap/intellij-idea-ultimate/204
/dev/loop5       45M   45M     0 100% /snap/gtk-common-themes/1440
/dev/loop7      157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop8       55M   55M     0 100% /snap/core18/1668
/dev/loop9      5,9M  5,9M     0 100% /snap/htop/1168
/dev/loop10     4,3M  4,3M     0 100% /snap/gnome-calculator/544
/dev/loop12     1,0M  1,0M     0 100% /snap/gnome-logs/81
/dev/loop11     1,0M  1,0M     0 100% /snap/gnome-logs/73
/dev/loop13     4,3M  4,3M     0 100% /snap/tree/18
/dev/loop14      55M   55M     0 100% /snap/core18/1650
/dev/loop15      90M   90M     0 100% /snap/core/8268
/dev/loop16     326M  326M     0 100% /snap/phpstorm/144
/dev/loop18     161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/loop17      45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop19      15M   15M     0 100% /snap/gnome-characters/399
/dev/nvme0n1p2   96M   32M   65M  33% /boot/efi
/dev/nvme0n1p7   69G   41G   26G  62% /home
tmpfs           1,6G   40K  1,6G   1% /run/user/1000

```

---

### Post by Holger_Gehrke on 2020-02-16
flatpak is another system for installing applications similar to snap. If you were to remove /var/lib/flatpak any apps you installed that way would be gone and you'd probably break the flatpak system. I'd use 'flatpak list' and 'sudo flatpak uninstall ...' to get a list of installed programs and remove the ones I don't want/need any more. If you don't want any of them you could try 'sudo apt purge flatpak' and see whether flatpak will remove installed apps when it's removed itself like snap does. If it doesn't you can remove /var/lib/flatpak after removing flatpak ('sudo rm -rf /var/lib/flatpak'). 

Holger

---

### Post by flex567 on 2020-02-16
I purged flatpak and after that I had to remove the folder manually.

Now I have more free space:
```

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7,7G     0  7,7G   0% /dev
tmpfs           1,6G  2,1M  1,6G   1% /run
/dev/nvme0n1p5   20G   15G  4,1G  79% /
tmpfs           7,7G   61M  7,7G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           7,7G     0  7,7G   0% /sys/fs/cgroup
/dev/loop4       92M   92M     0 100% /snap/core/8592
/dev/loop2      3,8M  3,8M     0 100% /snap/gnome-system-monitor/127
/dev/loop3      3,8M  3,8M     0 100% /snap/gnome-system-monitor/123
/dev/loop1       15M   15M     0 100% /snap/gnome-characters/375
/dev/loop6      728M  728M     0 100% /snap/intellij-idea-ultimate/204
/dev/loop5       45M   45M     0 100% /snap/gtk-common-themes/1440
/dev/loop7      157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop8       55M   55M     0 100% /snap/core18/1668
/dev/loop9      5,9M  5,9M     0 100% /snap/htop/1168
/dev/loop10     4,3M  4,3M     0 100% /snap/gnome-calculator/544
/dev/loop12     1,0M  1,0M     0 100% /snap/gnome-logs/81
/dev/loop11     1,0M  1,0M     0 100% /snap/gnome-logs/73
/dev/loop13     4,3M  4,3M     0 100% /snap/tree/18
/dev/loop14      55M   55M     0 100% /snap/core18/1650
/dev/loop15      90M   90M     0 100% /snap/core/8268
/dev/loop16     326M  326M     0 100% /snap/phpstorm/144
/dev/loop18     161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/loop17      45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop19      15M   15M     0 100% /snap/gnome-characters/399
/dev/nvme0n1p2   96M   32M   65M  33% /boot/efi
/dev/nvme0n1p7   69G   41G   26G  62% /home
tmpfs           1,6G   48K  1,6G   1% /run/user/1000

```

---

### Post by flex567 on 2020-02-16
What I notice with snaps is that after I do 

```

snap remove --revision 130 phpstorm
snap remove --revision 188 intellij-idea-ultimate

```

After some times these 2 appear again and I see them when I do --list . And I have to remove them again.
This applies for the same version of the apps.

So this doesn't seem like a permanent solutions??

---

### Post by HermanAB on 2020-02-16
First, make a backup of your data.

---

### Post by flex567 on 2020-02-17
What is this comment referring to? To my last question?

---

### Post by HermanAB on 2020-02-17
If you intend to make changes to the structure of disk, you run a big risk of corruption, which can waste a lot of time to fix.  Better make a decent backup first.

---

