---
title: "Looking for creative ways to reduce disk space occupied by system folders"
date: 2020-07-09
forum: General Help
---

### Post by lads on 2020-07-09
Hi all. I am in the process of upgrading all my systems to 20.04. Some days ago I noticed that in one system the 22 GB allocated to / where nearly full. I then performed the usual tasks:

1. Removed old kernels (only one was around).
2. Purged the package cache with apt.
3. Removed all orphaned packages found with gtkorphan.
4. Uninstalled about a dozen applications used less frequently.
5. Removed older versions of Snap applications.
6. Cleared systemd journal logs.

All this freed about 2 GB, which is still insufficient to upgrade to 20.04. A fresh Ubuntu installation should not take more the 5 GB, and while I have various programmes installed, I am at a loss to explain how it can take up so much space.

The problem is that there is no obvious culprit. Listing the packages larger than 100 MB, I can see TexLive is taking some space, but far from justifying 20 GB:

```
dpkg-query -W -f='${Installed-Size;8}  ${Package}\n' | sort -n
[...]
  105934  texlive-fonts-extra-doc
  106874  docker-ce
  115945  libboost1.65-dev
  125423  inkscape
  132095  libreoffice-core
  165607  linux-modules-extra-4.15.0-91-generic
  165744  linux-modules-extra-4.15.0-108-generic
  165765  linux-modules-extra-4.15.0-109-generic
  178737  docker-ce-cli
  206344  firefox
  214194  chromium-browser
  232263  libgl1-mesa-dri
  232770  skypeforlinux
  324978  linux-firmware
  909313  texlive-fonts-extra
```

Also ranking system folders nothing obvious comes up:

```
$ sudo du -h --max-depth=0 bd bin boot cdrom data dev etc lib lib32 lib64 lost+found opt proc root sbin snap srv sys tmp usr var | sort -n -r
206M	boot
188K	tmp
66M	root
20M	etc
16K	lost+found
13M	sbin
13M	bin
12K	dev
11G	usr
8,0K	data
5,8M	lib32
4,0K	srv
4,0K	lib64
4,0K	cdrom
4,0K	bd
4,0G	snap
3,3G	var
3,1G	opt
1,1G	lib
0	sys
0	proc

$ sudo du -h --max-depth=1 /usr | sort -n -r
809M	/usr/bin
684K	/usr/games
404M	/usr/src
240M	/usr/include
91M	/usr/libexec
20M	/usr/sbin
11G	/usr
8,0M	/usr/lib32
4,2G	/usr/lib
4,1G	/usr/share
1,1G	/usr/local
```

I would welcome creative ideas to further reduce space that do not involve randomly uninstalling software.

Thank you.

---

### Post by dragonfly41 on 2020-07-09
[Stacer]("https://github.com/oguzhaninan/Stacer") provides a nice dashboard to optimise resources.
You appear to have a lot (4GB) of snap installations. Start there.
The Stacer dashboard has an Uninstaller dashboard.
Look at snap packages installed.

---

### Post by SeijiSensei on 2020-07-09
You might have some old log files in /var/log you can remove.

---

### Post by Impavidus on 2020-07-09
You've got 11GB in /usr, which is reasonable if you've installed a bunch of applications. 1GB of that is in /usr/local, which must be manually installed software. 3GB in /var is a bit much, but not excessive. Maybe you can clean up some more old logs. 3GB is in /opt, which I guess are applications you didn't get from the official repos. It's quite a lot; I guess there's a big application there with a lot of data. [s]4GB is in /snap, so some room for cleanup there.[/s] Snap packages are big and new versions get installed automatically, all by design, so that quickly adds up. I haven't got any snaps on my system. They don't get installed out of the box on Xubuntu and I like to keep it like that. Together that accounts for most of your 22GB.

Edit: snaps are on a different filesystem, so they don't count to your 22GB.

---

### Post by TheFu on 2020-07-09
swap file?

To find unused snaps use,
```
$ snap list --all|grep disabled
lxd     4.3       15913  latest/stable  canonical*  disabled
scrcpy  v1.14     230    latest/stable  sisco311    disabled
snapd   2.45      7777   latest/stable  canonical*  snapd,disabled
```
The disabled versions have new versions installed.  Sadly, there isn't 1 command to clean those up and we have to use the "ver" in the *snap remove --revision* command.

i've been meaning to write a little script for that.

---

### Post by deadflowr on 2020-07-09
> i've been meaning to write a little script for that.
Here:
```
!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
```
from here:
[https://superuser.com/a/1330590]("https://superuser.com/a/1330590")
Must run as root (sudo)

For the record snaps take no actual physical disk space in /snap.
The disk space use for snaps is in /var/lib/snapd/snaps.
The space shown in /snap is just the mountpoint for the squashfs in the /var location.
Which is how you (or I in my own case) can see 50Gb of spaced used on a 40Gb partition.
More here: [https://askubuntu.com/a/1000200]("https://askubuntu.com/a/1000200")

---

### Post by TheFu on 2020-07-09
Thanks.  i prefer to have scripts that depend on sudo generate the commands, not actually perform them.
```
#!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
       echo   sudo snap remove "$snapname" --revision="$revision"
    done

```
generated this:
```
sudo snap remove lxd --revision=15913
sudo snap remove scrcpy --revision=230
sudo snap remove snapd --revision=7777
```

---

### Post by sudodus on 2020-07-09
Thanks for this script :-)

---

### Post by kneutron on 2020-07-09
> [COLOR=#000000]All this freed about 2 GB, which is still insufficient to upgrade to 20.04

--You have a couple of options.  One is to add another disk, whether USB3 or internal SATA and create a 10GB ext4 or XFS filesytem on a partition on that disk. ' **gparted** ' can help you with this.  Don't use the entire drive space in case you want to create more partitions on it.

o Then mount it somewhere and move everything as root (I would recommend using Midnight Commander '**mc**') in **/var/cache** to that partition. 

o Then mount that partition as /var/cache, or symlink a pointer to your existing mountpoint: ' **ln -sfn /mnt/yourseconddrive /var/cache** ' -- that will give you enough space to download .deb packages into /var/cache.  

o Don't forget to modify /etc/fstab to have it mount after every reboot, and you may have to delete the existing /var/cache dir first after moving files out of it if 'ln' gives you an error.  Also note you will need to leave this drive attached in order to boot and work correctly in the future, unless you move /var/cache back to where it used to be.

--You can use similar procedure to move other directories to separate partitions, such as /home. This will free up quite a bit of space on your root filesystem.

--You could resize partitions on your existing disk, but you would definitely need to back things up to another disk anyhow before modifying things in place.

[/COLOR][COLOR=#000000]--You could consider redoing everything with LVM, but I would avoid that as for some it becomes difficult to manage, slows things down and I consider it in general more painful than helpful.

--Another option would be to do a fresh install of 20.04 to a USB3 drive, which would give you portability and a chance to redo your partition scheme with larger sizes, or do an experimental install to ZFS boot/root (requires UEFI.)  And you could copy your files off the old install.  If you go this route I would recommend using a USB3 portable SSD such as the Samsung T5 (rather than a thumbdrive.)[/COLOR]

---

### Post by GhX6GZMB on 2020-07-09
Why do you have 3.1G in /opt? These days it's normally empty. Special programs? And the 3.3G in /var makes me suspect you have enormous logfiles lying around.

---

### Post by TheFu on 2020-07-09
> **ml9104 said:**
> Why do you have 3.1G in /opt? These days it's normally empty. Special programs? And the 3.3G in /var makes me suspect you have enormous logfiles lying around.

Checking a laptop here:
```
$ sudo du -sh /var/* |sort -h
...
18M     /var/backups
[B]981M    /var/cache
2.5G    /var/log
6.2G    /var/lib[/B]

``` 

Which leads to ...
```
$ sudo du -sh /var/l*/* |sort -h
...
17M     /var/lib/mlocate
18M     /var/lib/aptitude
101M    /var/lib/dpkg
183M    /var/lib/apt
[B]1.4G    /var/lib/snapd
2.5G    /var/log/journal
4.5G    /var/lib/lxd[/B]

```

Ah - snaps and lxd.  Those make perfect sense.  The journal are systemd binary logs, which I’ve set to retain for 3 boots.  i should look at that.
Because i use LVM, creating a 10G LV and mounting it on /var/lib/ would be trivial. Shouldn't need any downtime. 
```
$ sudo vgs
  VG             #PV #LV #SN Attr   VSize   VFree  
  ubuntu-mate-vg   1   4   0 wz--n- 464.54g **260.08g**
```
Yep. The VG has plenty of available space. For that flexibility there is some added complexity.  Most of the time, all of this can be ignored, but when you need it, it is nice to have the option.

Back to the /var/log/journal/*.  There are 55 files each about 90mb in there, each created for every boot.  Looks like my effort to retain 3 boots of logs failed.
Added these to the journald.conf file:
```
SystemMaxUse=500M
SystemMaxFiles=10
```

After those changes **sudo systemctl restart systemd-journald.service**
```
385M    /var/log/journal
```
Nice. That's the theory. 

**sudo apt clean** and 
```
24M     /var/cache
```
is reasonable again.
Hopefully showing my fix will help others.

---

### Post by HermanAB on 2020-07-10
Check /var/log.  There is probably tons of cruft there.

---

### Post by HermanAB on 2020-07-10
BTW, you could simply delete all log files.  The system will create new ones after a little while.  It used to be controlled with logrotate.conf, but Dog knows what systemd is doing with the logs.

---

### Post by lads on 2020-07-17
Thank you all for the replies. Eventually I managed to upgrade the system to 20.04. In this particular case the most efficient strategy was to remove snap programmes. Each programme released hundreds of MB, soon enough the system meet the requirements for the upgrade.

/var/logs is taking up 120 MB, no point in working on that. I install Java software to /opt, that is why it shows up. But since these are mostly staple programmes, e.g Eclipse, JabRef, Archi, there isn't much point in removing them.

There are plenty of other interesting strategies in this thread that can work in other circumstances.

Cheers.

---

