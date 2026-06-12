---
title: "Can I remove everything to do with SNAP ?"
date: 2022-07-27
forum: General Help
---

### Post by oygle on 2022-07-27
Having just spent a lot of time over the last few days trying to fix the snap/firefox mess, I would like to remove _everything_ to do with snap. Why did Canonical depart from apt for firefox ??

I don't use snap, is is not installed, I won't need/want it in the future. Can these paths be removed ? ..

/var/lib/snapd
/var/snap
/snap
/usr/bin/snap

and then add this code

```

cat <<EOF | sudo tee /etc/apt/preferences.d/nosnap.pref
# To prevent repository packages from triggering the installation of Snap,
# this file forbids snapd from being installed by APT.
# For more information: https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html

Package: snapd
Pin: release a=*
Pin-Priority: -10

EOF
```

(Reference:  [https://askubuntu.com/questions/1345385/how-can-i-stop-apt-from-installing-snap-packages](https://askubuntu.com/questions/1345385/how-can-i-stop-apt-from-installing-snap-packages) )

---

### Post by oldfred on 2022-07-27
You may want to see what snaps you have, so if you want the .deb version you know what to install.
 snap list

this removes everything snap
sudo apt autoremove --purge snapd
Or from snap list, you can remove them one at a time, in case you want to keep some. Example:
sudo apt purge gnome-software-plugin-snap

If you want Firefox you can install the ppa. And have to update some settings so ppa is primary.
Remove snap Firefox & use ppa this is what I have done. It does update both Firefox & Thunderbird.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)

General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) &

---

### Post by #&amp;thj^% on 2022-07-28
> **oygle said:**
> 

I don't use snap, is is not installed, I won't need/want it in the future. Can these paths be removed ? ..

/var/lib/snapd
/var/snap
/snap
/usr/bin/snap


Been waiting for someone to ask, I have removed all of:
```
/var/lib/snapd
/var/snap
/snap
/usr/bin/snap
```
This was over a month ago and again yesterday, after replying to you on firefox.
I have no side affects from this method but>>>your mileage may vary.
As oldfred suggests,use: snap list

This will show you a list of all the snap packages installed on your system.
Now for the removal, **and in this order.***
One line at a time:
```
sudo snap remove snap-store
sudo snap remove gtk-common-theme
sudo snap remove gnome-3-34-1804
```
Now Unmount snap-core:
```
sudo umount /snap/core/<core-id>
```
the <core-id> can be seen with "df"
If you are using Ubuntu 20.04 just run the following command.
```
sudo umount /var/snap
```
Now we remove snapd:
```
sudo apt purge snapd
```
Now we can get rid of the folders associated with snap.
```
sudo rm -rf ~/snap /snap /var/snap /var/lib/snapd
```
Verify with:
```
snap -version
```
Remember use this at your own risk!

---

### Post by &amp;KyT$0P# on 2022-07-28
> **oygle said:**
> I don't use snap, is is not installed, I won't need/want it in the future. Can these paths be removed ? ..

/var/lib/snapd
/var/snap
/snap
/usr/bin/snap

Are you sure snapd is completely uninstalled?  Purging snapd is the first thing I do in any new *buntu install, and I've never seen any of the paths you listed stay leftover.

> and then add this code

That should be fine once you've completely removed snapd.

---

### Post by #&amp;thj^% on 2022-07-28
> **halogen2 said:**
>  and I've never seen any of the paths you listed stay leftover.

.

Try This:
```
df -a
```

---

### Post by VMC on 2022-07-28
In addition to Oldfred's ppa solution, I use the advance Firefox install, found here:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)

---

### Post by #&amp;thj^% on 2022-07-29
Here is what I have on fresh Kubuntu install:
```
System:
  Host: oem-Standard-PC-Q35-ICH9-2009 Kernel: 5.15.0-25-generic x86_64
    bits: 64 Desktop: KDE Plasma 5.24.4 Distro: Ubuntu 22.04 (Jammy Jellyfish)

```
Mounts will show on a default install as:
```
oem@oem-Standard-PC-Q35-ICH9-2009:~$ df -a
Filesystem                 1K-blocks    Used Available Use% Mounted on
sysfs                              0       0         0    - /sys
proc                               0       0         0    - /proc
udev                         1941784       0   1941784   0% /dev
devpts                             0       0         0    - /dev/pts
tmpfs                         399984    1324    398660   1% /run
/dev/mapper/vgkubuntu-root  24118364 8353944  14513912  37% /
securityfs                         0       0         0    - /sys/kernel/security
tmpfs                        1999904       0   1999904   0% /dev/shm
tmpfs                           5120       4      5116   1% /run/lock
cgroup2                            0       0         0    - /sys/fs/cgroup
pstore                             0       0         0    - /sys/fs/pstore
efivarfs                           0       0         0    - /sys/firmware/efi/efivars
bpf                                0       0         0    - /sys/fs/bpf
systemd-1                          -       -         -    - /proc/sys/fs/binfmt_misc
hugetlbfs                          0       0         0    - /dev/hugepages
mqueue                             0       0         0    - /dev/mqueue
debugfs                            0       0         0    - /sys/kernel/debug
tracefs                            0       0         0    - /sys/kernel/tracing
fusectl                            0       0         0    - /sys/fs/fuse/connections
configfs                           0       0         0    - /sys/kernel/config
none                               0       0         0    - /run/credentials/systemd-sysusers.service
/dev/loop1                       128     128         0 100% /snap/bare/5
/dev/loop0                     63488   63488         0 100% /snap/core20/1405
/dev/loop2                    159488  159488         0 100% /snap/firefox/1232
/dev/loop4                     83328   83328         0 100% /snap/gtk-common-themes/1534
/dev/loop3                    254848  254848         0 100% /snap/gnome-3-38-2004/99
/dev/loop5                     44800   44800         0 100% /snap/snapd/15177
/dev/vda1                     523244    5364    517880   2% /boot/efi
tmpfs                         399984    1324    398660   1% /run/snapd/ns
nsfs                               0       0         0    - /run/snapd/ns/firefox.mnt
tmpfs                         399980      56    399924   1% /run/user/29999
binfmt_misc                        0       0         0    - /proc/sys/fs/binfmt_misc

```
Now to rid myself of the whole snap crap.
first look at:
```
 snap list
Name               Version          Rev    Tracking         Publisher   Notes
bare               1.0              5      latest/stable    canonical&#10003;  base
core20             20220318         1405   latest/stable    canonical&#10003;  base
firefox            99.0.1-1         1232   latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-38-2004    0+git.1f9014a    99     latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes  0.1-79-ga83e90c  1534   latest/stable/&#8230;  canonical&#10003;  -
snapd              2.54.4           15177  latest/stable    canonical&#10003;  snapd

```
Went as discribed in my post #3
Results:
```
$ df -a
Filesystem                 1K-blocks    Used Available Use% Mounted on
sysfs                              0       0         0    - /sys
proc                               0       0         0    - /proc
udev                         1941144       0   1941144   0% /dev
devpts                             0       0         0    - /dev/pts
tmpfs                         399980    1228    398752   1% /run
/dev/mapper/vgkubuntu-root  24118364 6949140  15918716  31% /
securityfs                         0       0         0    - /sys/kernel/security
tmpfs                        1999880       0   1999880   0% /dev/shm
tmpfs                           5120       4      5116   1% /run/lock
cgroup2                            0       0         0    - /sys/fs/cgroup
pstore                             0       0         0    - /sys/fs/pstore
efivarfs                           0       0         0    - /sys/firmware/efi/efivars
bpf                                0       0         0    - /sys/fs/bpf
systemd-1                          0       0         0    - /proc/sys/fs/binfmt_misc
hugetlbfs                          0       0         0    - /dev/hugepages
debugfs                            0       0         0    - /sys/kernel/debug
mqueue                             0       0         0    - /dev/mqueue
tracefs                            0       0         0    - /sys/kernel/tracing
fusectl                            0       0         0    - /sys/fs/fuse/connections
configfs                           0       0         0    - /sys/kernel/config
none                               0       0         0    - /run/credentials/systemd-sysusers.service
/dev/vda1                     523244    5364    517880   2% /boot/efi
tmpfs                         399976      48    399928   1% /run/user/29999

```
Heads up anyone using Discovey, that will be warned-removed along with snap:
That's a flase flag IE:
```
 apt policy plasma-discover
plasma-discover:
  Installed: 5.24.4-0ubuntu1
  Candidate: 5.24.4-0ubuntu1
  Version table:
 *** 5.24.4-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

```

 snap -version
bash: /usr/bin/snap: No such file or directory
```
EDIT:
```
oem@oem-Standard-PC-Q35-ICH9-2009:~$ cd /var/lib/snapd
bash: cd: /var/lib/snapd: No such file or directory
oem@oem-Standard-PC-Q35-ICH9-2009:~$ cd /var/snap
bash: cd: /var/snap: No such file or directory
oem@oem-Standard-PC-Q35-ICH9-2009:~$ cd /snap
bash: cd: /snap: No such file or directory
oem@oem-Standard-PC-Q35-ICH9-2009:~$ cd /usr/bin/snap
bash: cd: /usr/bin/snap: No such file or directory
oem@oem-Standard-PC-Q35-ICH9-2009:~$ 

```

---

### Post by oygle on 2022-07-29
Thanks everyone for your replies, links, etc, much appreciated.  :)

I'm now "snapfree" ....

```
snap list
```

> bash: /usr/bin/snap: No such file or directory

Most of the paths containing 'snap' are removed, and for safety sake, renamed /usr/lib/snap to /usr/lib/snap_backup

I don't see how Kubuntu can install/update snap without my intervention now, despite the fact a **locate** shows a few paths and many files there; all in /root though. I'm not concerned. Either a **mount** or a **df -a** show no references to snap.

This is how apt sees firefox now .

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

Even the PPA seems poised, ready to do a snap install, see [https://ubuntuforums.org/showthread.php?t=2477428&p=14106064#post14106064](https://ubuntuforums.org/showthread.php?t=2477428&p=14106064#post14106064)

At present I'm running firefox from an untarred download. It does do updates. It's not "installed" as such, just run the executable. Seems there are now two options for me.

1. Install firefox as per [https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)
2. **sudo apt install firefox-esr**

Thanks for your help.  :)

---

