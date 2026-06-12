---
title: "pulverize snap"
date: 2022-10-14
forum: General Help
---

### Post by VMC on 2022-10-14
How do I find what process keeps rebuilding "/snap" and "/var/snap" folders. They are the last remaining snap holdouts.
If I try removing them while running any ubuntu, it states "Read-only file system". I change the grub linix line to rw, and still get read only file system.
Is systemd involved? Where do I find how it gets rebuilt.

If I boot up using another Linux distro, I can remove those folders completely, but they somehow get rebuilt once I boot the Ubuntu distro.

---

### Post by #&amp;thj^% on 2022-10-14
follow this user>> user1656671: [https://askubuntu.com/questions/1035915/how-to-remove-snap-from-ubuntu](https://askubuntu.com/questions/1035915/how-to-remove-snap-from-ubuntu)
Zanna was the last editor for the post
It will also take care of:
```
/snap
/var/snap
/var/lib/snapd
```
But stop all running snaps.

---

### Post by VMC on 2022-10-14
I think I did all that in the beginning. I read your link but the following just wont work:
```
rm -rf ~/snap
sudo rm -rf /snap sudo rm -rf /var/snap
sudo rm -rf /var/lib/snapd
```Not sure why I can't get rid of the root snaps

edit: their is no running snaps. I remove those in the beginning.
edit2:I just did this with the following error. It doesn't state what the error is ```
$ sudo apt autoremove --purge snapd
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  snapd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 302999 files and directories currently installed.)
Purging configuration files for snapd (2.57.4+22.10ubuntu1) ...
Stopping snap-firefox-1883.mount
Stopping unit snap-firefox-1883.mount
Waiting until unit snap-firefox-1883.mount is stopped [attempt 1]
snap-firefox-1883.mount is stopped.
Removing snap firefox and revision 1883
rm: cannot remove '/var/snap/firefox/common/host-hunspell': **Device or resource bus**y
dpkg: error processing package snapd (--purge):
 installed snapd package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 snapd
E: Sub-process /usr/bin/dpk**g** returned an error code (1)
```how to find the resource busy???

---

### Post by #&amp;thj^% on 2022-10-14
Please don't be offended by any of my suggestions, I know your skills. :)
show this:
```
snap list
```
and:
```
systemctl status snapd
```
EDIT: make sure your not running a snap version of firefox as well.

---

### Post by VMC on 2022-10-14
> **1fallen said:**
> Please don't be offended by any of my suggestions, I know your skills. :)
show this:
```
snap list
```
and:
```
systemctl status snapd
```
EDIT: make sure your not running a snap version of firefox as well.

```
$ snap list
Command 'snap' not found, but can be installed with:
sudo apt install snapd
$ systemctl status snapd
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)

```

No, I'm using the firefox procedure found here:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)

---

### Post by #&amp;thj^% on 2022-10-14
> &#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
That needs to be unmasked first, then run down the list for removal just to be safe.
Mine:
```
 systemctl status snapd
Unit snapd.service could not be found.

```
When done check in:
```
df -a
df: /run/user/1000/doc: Operation not permitted
Filesystem     1K-blocks    Used Available Use% Mounted on
sysfs                  0       0         0    - /sys
proc                   0       0         0    - /proc
udev             1973524       0   1973524   0% /dev
devpts                 0       0         0    - /dev/pts
tmpfs             401768    1240    400528   1% /run
/dev/vda3       30267332 7819776  20884728  28% /
securityfs             0       0         0    - /sys/kernel/security
tmpfs            2008824       0   2008824   0% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
cgroup2                0       0         0    - /sys/fs/cgroup
pstore                 0       0         0    - /sys/fs/pstore
bpf                    0       0         0    - /sys/fs/bpf
systemd-1              0       0         0    - /proc/sys/fs/binfmt_misc
hugetlbfs              0       0         0    - /dev/hugepages
mqueue                 0       0         0    - /dev/mqueue
debugfs                0       0         0    - /sys/kernel/debug
tracefs                0       0         0    - /sys/kernel/tracing
fusectl                0       0         0    - /sys/fs/fuse/connections
configfs               0       0         0    - /sys/kernel/config
none                   0       0         0    - /run/credentials/systemd-sysusers.service
/dev/vda2         524252    5364    518888   2% /boot/efi
tmpfs             401764      48    401716   1% /run/user/1000

```

---

### Post by oldfred on 2022-10-14
I did the purge as soon as I installed Kubuntu 22.04 and this is what I have and I do not have those folders:

```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemctl status snapd [/COLOR]
Unit snapd.service could not be found. 
[COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]


[/FONT]
```

---

### Post by VMC on 2022-10-14
OK, I did this:
```
$ systemctl status snapd 
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)
$ systemctl unmask snapd 
Removed "/etc/systemd/system/snapd.service".
$ systemctl status snapd 
Unit snapd.service could not be found.
```

edit: I tried purged afterward, but same results.

---

### Post by #&amp;thj^% on 2022-10-14
Reboot and check again.

---

### Post by VMC on 2022-10-14
> **1fallen said:**
> Reboot and check again.

I did same results.

What I have now done is re-install and I will start from scratch. Using your link above. BUT I would still like to know what caused the "/snap & /var/snap" rebuild folders.
Your sure you don't have those folders?

---

### Post by #&amp;thj^% on 2022-10-14
> **VMC said:**
> 
Your sure you don't have those folders?
LOL...I promise:
```
df -a
Filesystem     1K-blocks    Used Available Use% Mounted on
sysfs                  0       0         0    - /sys
proc                   0       0         0    - /proc
udev             1973528       0   1973528   0% /dev
devpts                 0       0         0    - /dev/pts
tmpfs             401768    1212    400556   1% /run
/dev/vda3       30267332 7614944  21089560  27% /
securityfs             0       0         0    - /sys/kernel/security
tmpfs            2008828       0   2008828   0% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
cgroup2                0       0         0    - /sys/fs/cgroup
pstore                 0       0         0    - /sys/fs/pstore
bpf                    0       0         0    - /sys/fs/bpf
systemd-1              0       0         0    - /proc/sys/fs/binfmt_misc
hugetlbfs              0       0         0    - /dev/hugepages
mqueue                 0       0         0    - /dev/mqueue
debugfs                0       0         0    - /sys/kernel/debug
tracefs                0       0         0    - /sys/kernel/tracing
fusectl                0       0         0    - /sys/fs/fuse/connections
configfs               0       0         0    - /sys/kernel/config
none                   0       0         0    - /run/credentials/systemd-sysusers.service
/dev/vda2         524252    5364    518888   2% /boot/efi
tmpfs             401764      48    401716   1% /run/user/1000
me@me-Standard-PC-Q35-ICH9-2009:~$ df -hT
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  393M  1.2M  392M   1% /run
/dev/vda3      ext4    29G  7.3G   21G  27% /
tmpfs          tmpfs  2.0G     0  2.0G   0% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
/dev/vda2      vfat   512M  5.3M  507M   2% /boot/efi
tmpfs          tmpfs  393M   48K  393M   1% /run/user/1000
me@me-Standard-PC-Q35-ICH9-2009:~$ 


```
> **VMC said:**
> BUT I would still like to know what caused the "/snap & /var/snap" rebuild folders.

This is the first I've seen this following that link, my guess you followed some other instructions, before posting this thread.
I'm now curious how the clean install, and you following that link turns out though. ;)

---

### Post by VMC on 2022-10-14
It worked! I followed this link per Zanna or User comment:
[https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-10-and-20-04-lts/](https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-10-and-20-04-lts/)
I followed it to the letter. I had snap bare in my snap listing, but as mentioned, the order
apparently is important.

Thanks @1fallen for your help!

---

