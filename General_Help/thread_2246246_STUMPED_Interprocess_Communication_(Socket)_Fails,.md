---
title: "STUMPED: Interprocess Communication (Socket) Fails, Freezing Applications"
date: 2014-09-29
forum: General Help
---

### Post by heehau2 on 2014-09-29
OK, this one left me completely baffled.

I have been running Kubuntu on this Samsung Ultrabook (NP900X3D) for years now. Everything worked fine until a week ago or so, when the battery decided to "puff up." I had to get a replacement, and after I installed it (though not clear if there is a causal relation), all applications that use IPC on sockets simply freeze. That's a bewildering number of apps, including the "Start Menu." Some simply wait forever, while others time out the wait and move on happily thereafter. Examples of applications affected are:
[LIST]
[*]Pidgin 
[*]LibreOffice 
[*]Okular 
[/LIST]
Each of them dies in the same way. Here the tails of the straces for each of them:

[B]PIDGIN:
[/B]```
socket(PF_LOCAL, SOCK_STREAM, 0)        = 12
uname({sys="Linux", node="xyz", ...}) = 0
connect(12, {sa_family=AF_LOCAL, sun_path=@"/tmp/.ICE-unix/3673"}, 22) = 0
fcntl(12, F_SETFD, FD_CLOEXEC)          = 0
write(12, "\0\1\0\0\0\0\0\0", 8)        = 8
read(12,
```

[B]OKULAR:
[/B]```
socket(PF_LOCAL, SOCK_STREAM, 0)        = 8
uname({sys="Linux", node="xyz", ...}) = 0
connect(8, {sa_family=AF_LOCAL, sun_path=@"/tmp/.ICE-unix/3673"}, 22) = 0
fcntl(8, F_SETFD, FD_CLOEXEC)           = 0
write(8, "\0\1\0\0\0\0\0\0", 8)         = 8
read(8,
```

**LIBREOFFICE:**
```
socket(PF_LOCAL, SOCK_STREAM, 0)        = 3
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
connect(3, {sa_family=AF_LOCAL, sun_path="/tmp/OSL_PIPE_1000_SingleOfficeIPC_a3beb5cdaffdb65984763ef15579174"}, 110) = 0
read(3,
```

Those read()s never complete, and each application waits forever. As mentioned before, things were working just fine until a few days ago. Does anyone have any idea what's going on? Thanks, folks!

[B]lsb_release -a: 
[/B]```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty
```

[B]ifconfig:
[/B]```
eth0      Link encap:Ethernet  HWaddr 50:b7:c3:77:65:3c
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:45460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6016616 (6.0 MB)  TX bytes:6016616 (6.0 MB)

wlan0     Link encap:Ethernet  HWaddr c4:85:08:f1:05:7c
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c685:8ff:fef1:57c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:276689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:165258749 (165.2 MB)  TX bytes:37807022 (37.8 MB)
```

**mount:**
```
/dev/mapper/kubuntu-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/marco/.Private on /home/marco type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=###,ecryptfs_fnek_sig=###)
encfs on /home/marco/Documents/Secure type fuse.encfs (rw,nosuid,nodev,default_permissions,user=marco)
```

---

### Post by heehau2 on 2014-10-02
Well, in case this happens to anyone else...

Turns out something blocked the ksmserver process. It was trying to process something, but wasn't able to. I assume it was some kind of deadlock condition, with trying to start an application from the KDE environment being to blame.

I fixed it (after long hours of figuring out it was ksmserver that was to blame) by going to a tty (Alt-Ctrl-F1) and starting an X application from there. Since the tty is not aware of the display, you have to hand it to it manually:

DISPLAY=:0 kcalc

Note that you won't be able to see kcalc start, because it's on the graphical side. If you strace connect calls, you'll see kcalc go past the /tmp/.ICE-unix stage:

> > strace -e connect kcalc
connect(6, {sa_family=AF_LOCAL, sun_path=@"/tmp/.X11-unix/X0"}, 20) = 0
connect(7, {sa_family=AF_LOCAL, sun_path=@"/tmp/dbus-go5zFa52OC"}, 23) = 0
connect(8, {sa_family=AF_LOCAL, sun_path=@"/tmp/.ICE-unix/3628"}, 22) = 0
connect(9, {sa_family=AF_LOCAL, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
connect(9, {sa_family=AF_LOCAL, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)

---

