---
title: "SMB/CIFS start fail at boot"
date: 2014-05-01
forum: General Help
---

### Post by asgard2 on 2014-05-01
Hi,

at my bootlog are two entries:

```
 * Starting SMB/CIFS File and Active Directory Server[164G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[164G[[31mfail[39;49m]
```

Xbuntu 14.04 64bit with 3.13.0-24-generic

installed:
```
ii  libnss-winbind:amd64                                        2:4.1.6+dfsg-1ubuntu2                 amd64        Samba nameservice integration plugins
ii  libwbclient0:amd64                                          2:4.1.6+dfsg-1ubuntu2                 amd64        Samba winbind client library
ii  python-samba                                                2:4.1.6+dfsg-1ubuntu2                 amd64        Python bindings for Samba
ii  python-smbc                                                 1.0.14.1-0ubuntu2                     amd64        Python bindings for Samba clients (libsmbclient)
ii  samba                                                       2:4.1.6+dfsg-1ubuntu2                 amd64        SMB/CIFS file, print, and login server for Unix
ii  samba-common                                                2:4.1.6+dfsg-1ubuntu2                 all          common files used by both the Samba server and client
ii  samba-common-bin                                            2:4.1.6+dfsg-1ubuntu2                 amd64        Samba common files used by both the server and the client
ii  samba-dsdb-modules                                          2:4.1.6+dfsg-1ubuntu2                 amd64        Samba Directory Services Database
ii  samba-libs:amd64                                            2:4.1.6+dfsg-1ubuntu2                 amd64        Samba core libraries
ii  samba-vfs-modules                                           2:4.1.6+dfsg-1ubuntu2                 amd64        Samba Virtual FileSystem plugins

```

after boot, there are two running processes:
```
$ ps -e | grep smb
  652 ?        00:00:00 smbd
 1075 ?        00:00:00 smbd
```


```
$ sudo initctl list
avahi-daemon start/running, process 824
mountnfs-bootclean.sh start/running
rsyslog start/running, process 708
tty4 start/running, process 922
udev start/running, process 393
upstart-udev-bridge start/running, process 386
whoopsie start/running, process 1123
avahi-cups-reload stop/waiting
mountall-net stop/waiting
nmbd start/running, process 2445
passwd stop/waiting
rc stop/waiting
startpar-bridge stop/waiting
ureadahead-other stop/waiting
winbind start/running, process 2441
apport start/running
irqbalance start/running, process 1045
smbd start/running, process 652
systemd-logind start/running, process 765
tty5 start/running, process 926
console-setup stop/waiting
gpu-manager stop/waiting
hwclock-save stop/waiting
plymouth-log stop/waiting
mountall.sh start/running
failsafe stop/waiting
modemmanager stop/waiting
rfkill-store stop/waiting
dbus start/running, process 557
resolvconf start/running
mounted-var stop/waiting
plymouth-shutdown stop/waiting
plymouth stop/waiting
udev-fallback-graphics stop/waiting
usb-modeswitch-upstart stop/waiting
checkroot.sh start/running
control-alt-delete stop/waiting
hwclock stop/waiting
mounted-proc stop/waiting
cups-browsed start/running, process 1053
alsa-store stop/waiting
setvtrgb stop/waiting
shutdown stop/waiting
cron start/running, process 979
lightdm start/running, process 1084
mountkernfs.sh start/running
alsa-restore stop/waiting
mountall stop/waiting
mounted-debugfs stop/waiting
binfmt-support start/running
console stop/waiting
mounted-run stop/waiting
acpid start/running, process 1073
bluetooth start/running, process 593
checkfs.sh start/running
checkroot-bootclean.sh start/running
mountnfs.sh start/running
ufw start/running
kmod stop/waiting
plymouth-stop stop/waiting
rcS stop/waiting
reload-smbd stop/waiting
wait-for-state stop/waiting
bootmisc.sh start/running
flush-early-job-log stop/waiting
friendly-recovery stop/waiting
rc-sysinit stop/waiting
samba-ad-dc stop/waiting
cups start/running, process 2745
upstart-socket-bridge start/running, process 704
pulseaudio stop/waiting
cryptdisks start/running
mountdevsubfs.sh start/running
tty2 start/running, process 932
upstart-file-bridge start/running, process 591
anacron stop/waiting
udevtrigger stop/waiting
mtab.sh start/running
tty3 start/running, process 933
container-detect stop/waiting
mounted-dev stop/waiting
udev-finish stop/waiting
alsa-state stop/waiting
cryptdisks-udev stop/waiting
hostname stop/waiting
mountall-reboot stop/waiting
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface (wlan0) start/running
tty1 start/running, process 1441
mountall-shell stop/waiting
mounted-tmp stop/waiting
plymouth-ready stop/waiting
plymouth-splash stop/waiting
plymouth-upstart-bridge stop/waiting
udevmonitor stop/waiting
mountall-bootclean.sh start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/wlan0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (networking) start/running
networking start/running
tty6 start/running, process 936
dmesg stop/waiting
procps stop/waiting
rfkill-restore stop/waiting
console-font stop/waiting
network-interface-container stop/waiting
ureadahead stop/waiting
```

How can I fix this, I assume that the second smb start is wrong?


Regards

---

### Post by HermanAB on 2014-05-01
Well, you need to start Samba AFTER the network is steady and you need both smbd and nmbd running for it to actually work.

---

### Post by asgard2 on 2014-05-15
How can I do that?
I could [disable]("http://askubuntu.com/questions/19320/how-to-enable-or-disable-services") the service and add them manually, but this ways seems not clean to me.

---

### Post by capscrew on 2014-05-15
> **asgard2 said:**
> How can I do that?
I could [disable]("http://askubuntu.com/questions/19320/how-to-enable-or-disable-services") the service and add them manually, but this ways seems not clean to me.Samba should have 2 smbd daemons and 1 nmbd daemons running.  You can use this to show all the Samba daemons running after boot up```
ps -ef |grep **[COLOR="#FF0000"]mbd[/COLOR]**
```

I get this when Samba is working properly ```

  814 ?        00:00:00 smbd
  836 ?        00:00:00 smbd
  968 ?        00:00:00 nmbd

```

---

### Post by HiImTye on 2014-05-15
> **asgard2 said:**
> after boot, there are two running processes:
```
$ ps -e | grep smb
  652 ?        00:00:00 smbd
 1075 ?        00:00:00 smbd
```


```
$ sudo initctl list
...
nmbd start/running, process 2445
...
smbd start/running, process 652
...
```

How can I fix this, I assume that the second smb start is wrong?

I'm not sure what the issue is from your post. both daemons appear to be running. have you tried to access your files?

---

### Post by asgard2 on 2014-05-17
Yes, I can access other samba shares from my system, the issue is the error at boot and I want to fix that. 

```
$ ps -ef |grep mbd
root       680     1  0 10:35 ?        00:00:00 smbd -F
root      1089   680  0 10:35 ?        00:00:00 smbd -F
root      2135     1  0 10:36 ?        00:00:00 nmbd -D
```

```
$ ps -e | grep 680
  680 ?        00:00:00 smbd
```

However something goes wrong during booting.

---

### Post by Merrattic on 2014-05-17
I get the same "fail" on a clean install of 14.04 server. All daemons running as they should, though....

---

### Post by michal-urban on 2014-06-09
Same here ... I changed the sleep commands in /etc/init/failsafe.conf so it wont boot so bloody long but it still sucks ... 

Any solution, anybody?

---

### Post by pmackinney on 2014-07-09
Samba 4 has more daemons than just nmbd and smbd now. I'm also getting that startup error using "server role = standalone server". My shares are working just fine. Clearly Ubuntu needs to do some work on package configuration.

    # initctl list | grep mb
    nmbd start/running, process 1203
    smbd start/running, process 604
    reload-smbd stop/waiting
    samba-ad-dc stop/waiting

---

