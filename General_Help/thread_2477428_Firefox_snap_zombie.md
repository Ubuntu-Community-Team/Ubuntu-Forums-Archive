---
title: "Firefox snap zombie"
date: 2022-07-24
forum: General Help
---

### Post by dcroxton on 2022-07-24
I use an extension for Firefox that doesn't work with snaps, so I had to remove the version that came with the latest Ubuntu and install from a deb.  This works fine, but every so often my Firefox tells me I need to restart because it has upgraded.  And whenever this happens, I end up back in the snap version that I don't want.  I have to remove it again and re-add the deb repository.  Does anyone else have this problem, and what is the solution?

---

### Post by Dennis N on 2022-07-24
Close Firefox before doing updates that include Firefox.

---

### Post by ajgreeny on 2022-07-25
I don't use snaps at all and my Firefox is run directly from the downloaded .tar.gz archive from Mozilla.

I am the only user on my machine so I don't even bother to move the archive to /opt which is the normal and correct way to deal with this. I simply create a symbolic link in /usr/bin to the executable Firefox file in that extracted archive.

There are several threads giving more detail about this but searching and pasting on an Android machine is just too much palaver at the moment. When on a real computer I will find some links for you and give you the detail that may help more.

Of course, you  may have already figured this out by then but I'll keep checking.

---

### Post by oygle on 2022-07-27
I have had several attempts to remove the firefox/snap debarcle. I followed the guide at [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) , and even removed every last trace of snap. It is bloatware and I do not want any updates that happen automatically. Just why Canonical did this I do not know. In the past, snap has caused problems with other packages and that is why I steer clear of it.

It seems after the delete/purge of all snaps, I need to restart, as there is something left over. Every time I go to update **apt** pulls in a snap version of firefox. Not impressed at all.

---

### Post by #&amp;thj^% on 2022-07-27
[QUOTE=oygle;14105915Every time I go to update **apt** pulls in a snap version of firefox. Not impressed at all.[/QUOTE]

Yep you'll have to add an outside PPA to change that. ([https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa))
Or go with a flatpak install.

---

### Post by oygle on 2022-07-27
> **1fallen said:**
> Yep you'll have to add an outside PPA to change that. ([https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa))
Or go with a flatpak install.

Thanks. I'm sure I added that PPA from the instructions at [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) , and removed/purged any trace of snap. The thing I didn't do was restart I think as there were some traces still left over. I see in a **mount** command there is snap all over the place.

---

### Post by #&amp;thj^% on 2022-07-27
Just adding this, to be sure is all:
```
echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox
```
and to make sure future firefox upgrades to be installed automatically (Optional):
```
echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
```
I also see those mounts, but I'm not forced to update/upgrade firefox:
```
flatpak list
Name       Application ID             Version          Branch     Installation
Google Ch\u2026 com.google.Chrome          103.0.5060.134-1 stable     system
Google Ch\u2026 com.google.ChromeDev       105.0.5191.2-1   stable     system
Flameshot  org.flameshot.Flameshot    12.1.0           stable     system
Freedeskt\u2026 org.freedesktop.Platform   21.08.14         21.08      system
Mesa       \u2026sktop.Platform.GL.default 21.3.8           21.08      system
openh264   \u2026desktop.Platform.openh264 2.1.0            2.0        system
Yaru-mage\u2026 \u2026k3theme.Yaru-magenta-dark                  3.22       system
Adwaita t\u2026 org.kde.KStyle.Adwaita                      5.15-21.08 system
KDE Appli\u2026 org.kde.Platform                            5.15-21.08 system
QGnomePla\u2026 \u2026tformTheme.QGnomePlatform                  5.15-21.08 system
QtSNI      \u2026g.kde.PlatformTheme.QtSNI                  5.15-21.08 system
QGnomePla\u2026 \u2026QGnomePlatform-decoration                  5.15-21.08 system
Firefox    org.mozilla.firefox        103.0            stable     system

```
apt policy:
```
apt policy firefox
firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```
I have not added the PPA, I prefer flatpaks
As far as mounts we are stuck with these leftovers:
```
df -a
Filesystem     1K-blocks     Used Available Use% Mounted on
sysfs                  0        0         0    - /sys
proc                   0        0         0    - /proc
udev             1965200        0   1965200   0% /dev
devpts                 0        0         0    - /dev/pts
tmpfs             399980     1528    398452   1% /run
/dev/vda2       25108740 12607312  11200644  53% /
securityfs             0        0         0    - /sys/kernel/security
tmpfs            1999880        4   1999876   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
cgroup2                0        0         0    - /sys/fs/cgroup
pstore                 0        0         0    - /sys/fs/pstore
efivarfs               0        0         0    - /sys/firmware/efi/efivars
bpf                    0        0         0    - /sys/fs/bpf
systemd-1              -        -         -    - /proc/sys/fs/binfmt_misc
debugfs                0        0         0    - /sys/kernel/debug
hugetlbfs              0        0         0    - /dev/hugepages
mqueue                 0        0         0    - /dev/mqueue
tracefs                0        0         0    - /sys/kernel/tracing
fusectl                0        0         0    - /sys/fs/fuse/connections
configfs               0        0         0    - /sys/kernel/config
none                   0        0         0    - /run/credentials/systemd-sysusers.service
/dev/loop0         63488    63488         0 100% /snap/core20/1405
/dev/loop10        46976    46976         0 100% /snap/snap-store/575
/dev/loop2        165504   165504         0 100% /snap/firefox/1551
/dev/loop13          128      128         0 100% /snap/bare/5
/dev/loop12          384      384         0 100% /snap/snapd-desktop-integration/10
/dev/loop1         83328    83328         0 100% /snap/gtk-common-themes/1534
/dev/loop5        410496   410496         0 100% /snap/gnome-3-38-2004/112
/dev/loop7         93952    93952         0 100% /snap/gtk-common-themes/1535
/dev/loop4           384      384         0 100% /snap/snapd-desktop-integration/14
/dev/loop3         44800    44800         0 100% /snap/snapd/15177
/dev/loop9         48128    48128         0 100% /snap/snapd/16292
/dev/loop8        254848   254848         0 100% /snap/gnome-3-38-2004/99
/dev/loop6        159488   159488         0 100% /snap/firefox/1232
/dev/loop11        63488    63488         0 100% /snap/core20/1581
/dev/vda1         523244     5364    517880   2% /boot/efi
binfmt_misc            0        0         0    - /proc/sys/fs/binfmt_misc
tmpfs             399976      132    399844   1% /run/user/1000
gvfsd-fuse             0        0         0    - /run/user/1000/gvfs
portal                 0        0         0    - /run/user/1000/doc

```
I can also get rid of all the snap mounts IE:
```
 df -a
df: /run/user/1000/doc: Operation not permitted
Filesystem     1K-blocks     Used Available Use% Mounted on
sysfs                  0        0         0    - /sys
proc                   0        0         0    - /proc
udev             1965200        0   1965200   0% /dev
devpts                 0        0         0    - /dev/pts
tmpfs             399980     1476    398504   1% /run
/dev/vda2       25108740 11456960  12350996  49% /
securityfs             0        0         0    - /sys/kernel/security
tmpfs            1999880        0   1999880   0% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
cgroup2                0        0         0    - /sys/fs/cgroup
pstore                 0        0         0    - /sys/fs/pstore
efivarfs               0        0         0    - /sys/firmware/efi/efivars
bpf                    0        0         0    - /sys/fs/bpf
systemd-1              -        -         -    - /proc/sys/fs/binfmt_misc
mqueue                 0        0         0    - /dev/mqueue
debugfs                0        0         0    - /sys/kernel/debug
tracefs                0        0         0    - /sys/kernel/tracing
hugetlbfs              0        0         0    - /dev/hugepages
fusectl                0        0         0    - /sys/fs/fuse/connections
configfs               0        0         0    - /sys/kernel/config
none                   0        0         0    - /run/credentials/systemd-sysusers.service
/dev/vda1         523244     5364    517880   2% /boot/efi
binfmt_misc            0        0         0    - /proc/sys/fs/binfmt_misc
tmpfs             399976       96    399880   1% /run/user/1000
gvfsd-fuse             0        0         0    - /run/user/1000/gvfs
#############
and
me@me-Standard-PC-Q35-ICH9-2009:~$ mount | grep snaps
me@me-Standard-PC-Q35-ICH9-2009:~$ 

```
If interested let me know, and accept the risk involved if any.

---

### Post by oygle on 2022-07-27
Thanks for your help. I followed all the instructions as per [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)  , and checked the contents of the files. Removed/purged/deleted **ALL** of snap, ..completely. Then powered down, then boot up ..

```
sudo apt install firefox
```

> Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
firefox is already the newest version (1:1snap1-0ubuntu2).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

Yet firefox was nowhere to be found. It wasn't installed.

Fortunately I had a backup of Firefox as a tar file, ran that and was able to use Firefox. The 'about' says 103.0 (64-bit)

The apt policy gives false information ...

> apt policy firefox
firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 1:1snap1-0ubuntu2
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     103.0+build1-0ubuntu0.22.04.1~mt1 500
        500 [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu) jammy/main amd64 Packages

I don't have snap installed at all. What a mess this is, and I see a lot of other users are having problems. My solution for now - [https://www.torproject.org/dist/torbrowser/11.5.1/tor-browser-linux64-11.5.1_en-US.tar.xz](https://www.torproject.org/dist/torbrowser/11.5.1/tor-browser-linux64-11.5.1_en-US.tar.xz)

---

### Post by ajgreeny on 2022-07-28
The alternative method that I am now using, ie running it directly from the downloaded .tar.gz archive, does not risk apt pulling in a snap version of firefox as using a PPA apparently can.

The .tar.gz version can be either allowed to update automatically, when it will simply tell you to restart firefox to begin using the new version, or you can tell it just to notify you of a new version available and offer to download it, after which it will again tell you to restart firefox.  I use the latter of those two methods.  So far it has been completely faultless in operation.

---

### Post by oygle on 2022-07-29
> **ajgreeny said:**
> The alternative method that I am now using, ie running it directly from the downloaded .tar.gz archive, does not risk apt pulling in a snap version of firefox as using a PPA apparently can.

If I look at the PPA at [https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa) , there is firefox and firefox-esr . Notice the "[COLOR="#3399ff"]_Newer version_[/COLOR]" link is "snapped". Possibly that is why everytime I follow the instructions for the PPA, sooner or later the (snapped) version of firefox gets installed ?  So I will try

```
sudo apt install firefox-esr
```

> **ajgreeny said:**
> The .tar.gz version can be either allowed to update automatically, when it will simply tell you to restart firefox to begin using the new version, or you can tell it just to notify you of a new version available and offer to download it, after which it will again tell you to restart firefox.  I use the latter of those two methods.  So far it has been completely faultless in operation.

Yes, the "notify" gives me a warm fuzzy feeling. Thanks

---

### Post by deadflowr on 2022-07-29
> The apt policy gives false information ...
The Firefox apt package on 22.04 is transitional, meaning it will remain on until it's removed.
Removing snaps and anything snap related will do nothing to remove the apt package.

It also works in reverse.
Meaning once you install the apt version, you can remove the apt package and it will have no affect on the snap package that it installed.

---

### Post by oygle on 2022-07-29
Yes, both snap and apt are only just package managers. By "false" I simply meant the displaying of firefox being installed when it was not. I think that was compounded by apt in that there was a firefox/transitional package showing as "installed". Synaptic stated it can be safely removed, and now

```
apt policy firefox
```

> firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
     103.0+build1-0ubuntu0.22.04.1~mt1 500
        500 [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu) jammy/main amd64 Packages

I'm only running firefox from a tarred download for now. Interesting in the system activity firefox-bin has 130 threads and there are 15 processes called "Isolated Web Co". Many of those are running 20 threads. A quick look via [https://www.google.com/search?client=firefox-b-d&q=isolated+web+co](https://www.google.com/search?client=firefox-b-d&q=isolated+web+co) , and it could be just a mozilla bug, a virus, zombies, etc ??  Yet a top shows cpu to be less than 1 % and memory is about 50% used, so nothing to be concerned about.

---

### Post by oldfred on 2022-07-29
The Firefox ppa is working fine for me.

If you do not change priority, I think then the Ubuntu snap version then is installed.

---

### Post by oygle on 2022-07-31
> **oldfred said:**
> The Firefox ppa is working fine for me.

If you do not change priority, I think then the Ubuntu snap version then is installed.

Based on the current settings (below), do I have to change the priority to install the PPA ?

```
apt policy firefox
```

> firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
     103.0+build1-0ubuntu0.22.04.1~mt1 500
        500 [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu) jammy/main amd64 Packages
        
```
cat  /etc/apt/preferences.d/mozilla-firefox
```

> Package: *
        Pin: release o=LP-PPA-mozillateam
        Pin-Priority: 1001

---

### Post by oldfred on 2022-07-31
This is my policy so 1001 not 500 as snap is:
```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ apt policy firefox [/COLOR]
firefox: 
  Installed: 103.0+build1-0ubuntu0.22.04.1~mt1 
  Candidate: 103.0+build1-0ubuntu0.22.04.1~mt1 
  Version table: 
     1:1snap1-0ubuntu2 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
 *** 103.0+build1-0ubuntu0.22.04.1~mt1 1001 
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Pa
ckages 
        100 /var/lib/dpkg/status


[/FONT]
```

sudo snap remove firefox
 sudo add-apt-repository ppa:mozillateam/ppa
echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox

echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
sudo apt install firefox

Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by oygle on 2022-08-01
Thanks, I used the one at [https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd) , and it is installed now from the PPA.

---

