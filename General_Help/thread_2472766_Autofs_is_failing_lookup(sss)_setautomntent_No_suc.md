---
title: "Autofs is failing: lookup(sss): setautomntent: No such file or directory"
date: 2022-03-11
forum: General Help
---

### Post by noahdb on 2022-03-11
Hi, 

I used to be able to automount the following directories just fine. 

I can mount these nfs directories to non-ubuntu hosts. 
A recent upgrade looks like it broke autofs. 

Mounting <ip>:/mnt/DroboFS/Shares/Music  as an NFS mount to /media/Music works in the fstab just fine.  So NFS can work.
Any clues what I can do to revitalize the mounts? 

Cheers

--- command output --- 



Autofs is failing: lookup(sss): setautomntent: No such file or directory 

```
<hostname># sudo service autofs status 
&#9679; autofs.service - Automounts filesystems on demand 
     Loaded: loaded (/lib/systemd/system/autofs.service; enabled;  vendor preset: enabled) 
     Active: active (running) since Fri 2022-03-11 19:32:50 UTC; 8min ago 
       Docs: man:autofs(8) 
    Process: 1370 ExecStart=/usr/sbin/automount $OPTIONS --pid-file  /var/run/autofs.pid (code=exited, status=0/SUCCESS) 
    Process: 7433 ExecReload=/bin/kill -HUP $MAINPID (code=exited,  status=0/SUCCESS) 
   Main PID: 1382 (automount) 
      Tasks: 4 (limit: 76629) 
     Memory: 4.9M 
     CGroup: /system.slice/autofs.service 
             &#9492;&#9472;1382 /usr/sbin/automount --pid-file /var/run/autofs.pid 

Mar 11 19:38:19 <hostname> automount[1382]: setautomntent: lookup(sss):  setautomntent: No such file or directory 
Mar 11 19:38:19 <hostname> automount[1382]: setautomntent: lookup(sss):  setautomntent: No such file or directory 
Mar 11 19:40:44 <hostname> systemd[1]: Reloading Automounts filesystems  on demand. 
Mar 11 19:40:44 <hostname> systemd[1]: Reloaded Automounts filesystems  on demand. 
Mar 11 19:40:44 <hostname> automount[1382]: setautomntent: lookup(sss):  setautomntent: No such file or directory 
Mar 11 19:40:44 <hostname> automount[1382]: setautomntent: lookup(sss):  setautomntent: No such file or directory 
Mar 11 19:41:08 <hostname> systemd[1]: Reloading Automounts filesystems  on demand. 
Mar 11 19:41:08 <hostname> systemd[1]: Reloaded Automounts filesystems  on demand. 
Mar 11 19:41:08 <hostname> automount[1382]: setautomntent: lookup(sss):  setautomntent: No such file or directory 
Mar 11 19:41:08 <hostname> automount[1382]: setautomntent: lookup(sss):  setautomntent: No such file or directory 

```

```
<hostname># cat /etc/lsb-release 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=20.04 
DISTRIB_CODENAME=focal 
DISTRIB_DESCRIPTION="Ubuntu 20.04.4 LTS" 
<hostname># uname -a 
Linux <hostname> 5.4.0-104-generic #118-Ubuntu SMP Wed Mar 2 19:02:41  UTC 2022 x86_64 x86_64 x86_64 GNU/Linux 
```

```
# df -kh 
Filesystem                         Size  Used Avail Use% Mounted on 
udev                                32G     0   32G   0% /dev 
tmpfs                              6.3G  2.1M  6.3G   1% /run 
/dev/mapper/ubuntu--vg-ubuntu--lv  196G  122G   64G  66% / 
tmpfs                               32G  3.9M   32G   1% /dev/shm 
tmpfs                              5.0M     0  5.0M   0% /run/lock 
tmpfs                               32G     0   32G   0% /sys/fs/cgroup 
/dev/nvme0n1p2                     976M  208M  702M  23% /boot 
/dev/nvme0n1p1                     511M  5.3M  506M   2% /boot/efi 
/dev/loop1                          56M   56M     0 100% /snap/core18/2284 
/dev/loop0                          56M   56M     0 100% /snap/core18/2253 
/dev/loop3                          68M   68M     0 100% /snap/lxd/21835 
/dev/loop2                          62M   62M     0 100% /snap/core20/1361 
/dev/loop4                          68M   68M     0 100% /snap/lxd/22526 
/dev/loop5                          44M   44M     0 100% /snap/snapd/14978 
/dev/loop6                          62M   62M     0 100% /snap/core20/1376 
tmpfs                              6.3G   12K  6.3G   1% /run/user/1000 
tmpfs                              6.3G     0  6.3G   0% /run/user/996 
overlay                            196G  122G   64G  66%  /var/lib/docker/overlay2/37213cb6e6da12b9a735561596d74727c61183fa5a0aa6dda3ed85865c463759/merged 
overlay                            196G  122G   64G  66%  /var/lib/docker/overlay2/7ff72734f073cb264bb9a6e97f783a670fe18764888088333aa2bf0d1b46bcdb/merged 
```

```
# cat /etc/auto.master 
# 
# Sample auto.master file 
# This is a 'master' automounter map and it has the following format: 
# mount-point [map-type[,format]:]map [options] 
# For details of the format look at auto.master(5). 
# 
#/misc    /etc/auto.misc 
/-    auto.homenas 
# 
# NOTE: mounts done from a hosts map will be mounted with the 
#    "nosuid" and "nodev" options unless the "suid" and "dev" 
#    options are explicitly given. 
# 
#/net    -hosts 
# 
# Include */etc/auto.master.d/**.autofs 
# To add an extra map using this mechanism you will need to add 
# two configuration items - one /etc/auto.master.d/extra.autofs file 
# (using the same line format as the auto.master file) 
# and a separate mount map (e.g. /etc/auto.extra or an auto.extra NIS map) 
# that is referred to by the extra.autofs file. 
# 
+dir:/etc/auto.master.d 
# 
# If you have fedfs set up and the related binaries, either 
# built as part of autofs or installed from another package, 
# uncomment this line to use the fedfs program map to access 
# your fedfs mounts. 
#/nfs4  /usr/sbin/fedfs-map-nfs4 nobind 
# 
# Include central master map if it can be found using 
# nsswitch sources. 
# 
# Note that if there are entries for /net or /misc (as 
# above) in the included master map any keys that are the 
# same will not be seen as the first read key seen takes 
# precedence. 
# 
+auto.master 
```

```
<hostname># cat auto.homenas 
# <mountpoint>    <options>    <remote_ip>:<location> 

/media/Audio     -fstype=nfs   <ip>:/mnt/DroboFS/Shares/Audio 
/media/Music     -fstype=nfs   <ip>:/mnt/DroboFS/Shares/Music 
/media/Pictures  -fstype=nfs   <ip>:/mnt/DroboFS/Shares/Pictures 
/media/Videos    -fstype=nfs   <ip>:/mnt/DroboFS/Shares/Videos 
/media/Streams   -fstype=nfs   <ip>:/mnt/DroboFS/Shares/Streams 
```


--- snip ---

---

### Post by TheFu on 2022-03-11
My NFS mounts are working still, but I patch only once a week, so if the problem is from this week, then I'll see it tomorrow morning.

Nothing is clearly jumping out at me as incorrect in the autofs settings. I don't have a drobo. Could that be the issue?
Anyways, it is getting late here, so if I see any issues in the morning with autofs, I'll have this post as a reminder.

Google found something in 
```
$ grep automount /etc/nsswitch.conf
```
that points at a setting there.
You probably want:
```
automount:  files
```
[COLOR="#FF0000"]not[/COLOR] **files sss** in that line.

---

### Post by TheFu on 2022-03-12
I patched and rebooted all my systems this morning.  autofs is still working. No issues.
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
romulus:/Data/r2                nfs4  1.3T  1.2T  7.2G 100% /S
istar:/d/D1                     nfs4  3.5T  3.5T   45G  99% /d/D1
```
Appears like something specific locally.

My system with the mounts above is:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu [COLOR="#008000"]20.04.4[/COLOR] LTS
Release:        20.04
Codename:       focal

$ uname -a
Linux regulus [COLOR="#008000"]5.4.0-104-generic[/COLOR] #118-Ubuntu SMP Wed Mar 2 19:02:41 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

It was a fresh install back in 2020, not an upgrade.  Actually, I moved data/settings from a 32-bit 16.04 into a 64-bit 20.04 install as part of the process.

---

