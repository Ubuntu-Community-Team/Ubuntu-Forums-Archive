---
title: "How install docker in ubuntu on other partition"
date: 2019-09-20
forum: General Help
---

### Post by petrogromovo on 2019-09-20
Hello, 
I have installed Kubuntu 18 on sdb5 and I need to install docker. 
As it takes a lot of free space(I found that /var/lib/docker/ takes 11.1 GiB) I want to add more disk space with using sdb7, which is not used now.
I formatted sdb7 into ext4 and do next :


I have in /etc/fstab :
```
/dev/sdb7 /mnt/_work_sdb7

```


In /etc/docker/daemon.json I have :
Code:
```
{
  "data-root": "/mnt/_work_sdb7/docker" ,
  "storage-driver": "overlay2"
}

```
I try to set symbolic link to this dir and install docker:
```
serge@serge-at-hoe:/var/lib$ sudo ln -s /mnt/_work_sdb7/docker  /var/lib/docker                                                                                                                                                              
serge@serge-at-hoe:/var/lib$ sudo rsync -av docker /mnt/_work_sdb7                                                                                                                                                              
sending incremental file list

sent 75 bytes  received 19 bytes  188.00 bytes/sec
total size is 22  speedup is 0.23
serge@serge-at-hoe:/var/lib$ sudo apt-get install docker-ce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
docker-ce is already the newest version (5:19.03.2~3-0~ubuntu-bionic).
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up docker-ce (5:19.03.2~3-0~ubuntu-bionic) ...
Job for docker.service failed because the control process exited with error code.
See "systemctl status docker.service" and "journalctl -xe" for details.
invoke-rc.d: initscript docker, action "start" failed.
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Fri 2019-09-20 17:16:54 EEST; 6ms ago
     Docs: https://docs.docker.com
  Process: 13535 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 13535 (code=exited, status=1/FAILURE)
dpkg: error processing package docker-ce (--configure):
 installed docker-ce package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 docker-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I do not see new created link to  work_sdb7 , can it be issue ?
```
serge@serge-at-hoe:/var/lib$ ls -la / | grep "\->"
lrwxrwxrwx   1 root root    14 &#1089;&#1077;&#1088; 20 21:45 _diskD_Work -> /mnt/Work_sda6
lrwxrwxrwx   1 root root    15 &#1089;&#1077;&#1088; 20 21:46 _diskE_Media -> /mnt/Media_sda8
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 20:23 initrd.img -> boot/initrd.img-4.15.0-20-generic
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 20:20 initrd.img.old -> boot/initrd.img-4.15.0-20-generic
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 21:45 _InstallLinux -> /mnt/Work_sda6/Install/__forLinux
lrwxrwxrwx   1 root root    22 &#1089;&#1077;&#1088; 20 20:56 _Prior_Kubuntu_18 -> /mnt/_Prior_Kubuntu_18
lrwxrwxrwx   1 root root    21 &#1089;&#1077;&#1088; 20 21:01 _Video -> /mnt/Media_sda8/VIDEO
lrwxrwxrwx   1 root root    30 &#1089;&#1077;&#1088; 20 20:23 vmlinuz -> boot/vmlinuz-4.15.0-20-generic
lrwxrwxrwx   1 root root    16 &#1089;&#1077;&#1088; 20 20:41 _work -> /mnt/_work_sdb8/
lrwxrwxrwx   1 root root    23 &#1089;&#1077;&#1088; 20 21:45 _wwwroot -> /mnt/_work_sdb8/wwwroot


serge@serge-at-hoe:/var/lib$ systemctl status docker.service
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2019-09-20 17:17:00 EEST; 9min ago
     Docs: https://docs.docker.com
  Process: 13670 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 13670 (code=exited, status=1/FAILURE)

&#1074;&#1077;&#1088; 20 17:17:00 serge-at-hoe systemd[1]: docker.service: Service hold-off time over, scheduling restart.
&#1074;&#1077;&#1088; 20 17:17:00 serge-at-hoe systemd[1]: docker.service: Scheduled restart job, restart counter is at 3.
&#1074;&#1077;&#1088; 20 17:17:00 serge-at-hoe systemd[1]: Stopped Docker Application Container Engine.
&#1074;&#1077;&#1088; 20 17:17:00 serge-at-hoe systemd[1]: docker.service: Start request repeated too quickly.
&#1074;&#1077;&#1088; 20 17:17:00 serge-at-hoe systemd[1]: docker.service: Failed with result 'exit-code'.
&#1074;&#1077;&#1088; 20 17:17:00 serge-at-hoe systemd[1]: Failed to start Docker Application Container Engine.
serge@serge-at-hoe:/var/lib$ journalctl -xe
&#1074;&#1077;&#1088; 20 17:20:01 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=196.196.244.38 DST=213.109.234.130 LEN=52 TOS=0x00 PREC=0x00 TTL=118 ID=538 DF PROTO=TCP SPT=56135 DPT=6881 WINDOW=8192 RES
&#1074;&#1077;&#1088; 20 17:20:39 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=192.99.175.190 DST=213.109.234.130 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=8777 DF PROTO=TCP SPT=42137 DPT=8000 WINDOW=5840 RES
&#1074;&#1077;&#1088; 20 17:20:41 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=164.68.120.73 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=250 ID=58759 PROTO=TCP SPT=57739 DPT=11223 WINDOW=1024 RES=
&#1074;&#1077;&#1088; 20 17:21:02 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=188.32.243.196 DST=213.109.234.130 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=1466 DF PROTO=TCP SPT=58845 DPT=6881 WINDOW=8192 RE
&#1074;&#1077;&#1088; 20 17:21:25 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=01:00:5e:00:00:01:c8:e7:f0:6e:fc:29:08:00 SRC=100.103.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=24332 PROTO=2 
&#1074;&#1077;&#1088; 20 17:21:42 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=109.203.223.77 DST=213.109.234.130 LEN=60 TOS=0x00 PREC=0x00 TTL=56 ID=26858 DF PROTO=TCP SPT=40047 DPT=6881 WINDOW=7300 RE
&#1074;&#1077;&#1088; 20 17:22:02 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=150.109.167.75 DST=213.109.234.130 LEN=40 TOS=0x08 PREC=0x00 TTL=242 ID=54321 PROTO=TCP SPT=45663 DPT=1040 WINDOW=65535 RES
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe dhclient[1739]: DHCPREQUEST of 213.109.234.130 on enp4s0 to 100.103.0.1 port 67 (xid=0x32ba9984)
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe dhclient[1739]: DHCPACK of 213.109.234.130 from 100.103.0.1
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe NetworkManager[1110]: <info>  [1568989341.0718] dhcp4 (enp4s0):   address 213.109.234.130
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe NetworkManager[1110]: <info>  [1568989341.0718] dhcp4 (enp4s0):   plen 23 (255.255.254.0)
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe NetworkManager[1110]: <info>  [1568989341.0719] dhcp4 (enp4s0):   gateway 213.109.234.1
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe NetworkManager[1110]: <info>  [1568989341.0719] dhcp4 (enp4s0):   lease time 3600
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe NetworkManager[1110]: <info>  [1568989341.0719] dhcp4 (enp4s0):   nameserver '93.175.192.21'
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe NetworkManager[1110]: <info>  [1568989341.0719] dhcp4 (enp4s0):   nameserver '93.175.192.22'
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe NetworkManager[1110]: <info>  [1568989341.0719] dhcp4 (enp4s0): state changed bound -> bound
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe dbus-daemon[1011]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=1110 comm="/usr/sbin/NetworkM
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe systemd[1]: Starting Network Manager Script Dispatcher Service...
-- Subject: Unit NetworkManager-dispatcher.service has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit NetworkManager-dispatcher.service has begun starting up.
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe dbus-daemon[1011]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe nm-dispatcher[13854]: req:1 'dhcp4-change' [enp4s0]: new request (1 scripts)
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe systemd[1]: Started Network Manager Script Dispatcher Service.
-- Subject: Unit NetworkManager-dispatcher.service has finished start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit NetworkManager-dispatcher.service has finished starting up.
-- 
-- The start-up result is RESULT.
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe nm-dispatcher[13854]: req:1 'dhcp4-change' [enp4s0]: start running ordered scripts...
&#1074;&#1077;&#1088; 20 17:22:21 serge-at-hoe dhclient[1739]: bound to 213.109.234.130 -- renewal in 1417 seconds.
&#1074;&#1077;&#1088; 20 17:22:22 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=185.245.87.169 DST=213.109.234.130 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=20695 DF PROTO=TCP SPT=44263 DPT=6881 WINDOW=14600 R
&#1074;&#1077;&#1088; 20 17:22:41 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=185.224.9.185 DST=213.109.234.130 LEN=132 TOS=0x00 PREC=0x00 TTL=122 ID=11252 PROTO=UDP SPT=8999 DPT=6881 LEN=112 
&#1074;&#1077;&#1088; 20 17:23:10 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=164.68.120.73 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=250 ID=61398 PROTO=TCP SPT=57739 DPT=19125 WINDOW=1024 RES=
&#1074;&#1077;&#1088; 20 17:23:20 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=185.176.27.162 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=251 ID=16105 PROTO=TCP SPT=49642 DPT=15351 WINDOW=1024 RES
&#1074;&#1077;&#1088; 20 17:24:04 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=185.222.211.54 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=251 ID=45743 PROTO=TCP SPT=53468 DPT=18138 WINDOW=1024 RES
&#1074;&#1077;&#1088; 20 17:24:05 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=117.5.215.29 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=61725 PROTO=TCP SPT=56531 DPT=23 WINDOW=52417 RES=0x00
&#1074;&#1077;&#1088; 20 17:24:22 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=86.139.126.212 DST=213.109.234.130 LEN=52 TOS=0x00 PREC=0x00 TTL=117 ID=21794 DF PROTO=TCP SPT=14874 DPT=6881 WINDOW=64240 
&#1074;&#1077;&#1088; 20 17:24:23 serge-at-hoe wpa_supplicant[1105]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.BSS dbus_property=RSN getter failed
&#1074;&#1077;&#1088; 20 17:24:23 serge-at-hoe wpa_supplicant[1105]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (org.freedesktop.DBus.Error.Failed) failed to parse RSN IE
&#1074;&#1077;&#1088; 20 17:24:23 serge-at-hoe wpa_supplicant[1105]: dbus: Failed to construct signal
&#1074;&#1077;&#1088; 20 17:24:23 serge-at-hoe wpa_supplicant[1105]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.BSS dbus_property=RSN getter failed
&#1074;&#1077;&#1088; 20 17:24:42 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=213.87.129.152 DST=213.109.234.130 LEN=52 TOS=0x18 PREC=0x60 TTL=111 ID=10890 DF PROTO=TCP SPT=15682 DPT=6881 WINDOW=64240 
&#1074;&#1077;&#1088; 20 17:25:14 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=164.68.120.73 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=250 ID=29404 PROTO=TCP SPT=57739 DPT=9578 WINDOW=1024 RES=0
&#1074;&#1077;&#1088; 20 17:25:20 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=80.82.65.74 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=250 ID=25578 PROTO=TCP SPT=44443 DPT=52776 WINDOW=1024 RES=0x
&#1074;&#1077;&#1088; 20 17:26:04 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=80.82.65.74 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=250 ID=43716 PROTO=TCP SPT=44443 DPT=60457 WINDOW=1024 RES=0x
&#1074;&#1077;&#1088; 20 17:26:10 serge-at-hoe systemd-resolved[882]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
&#1074;&#1077;&#1088; 20 17:26:10 serge-at-hoe systemd-resolved[882]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
&#1074;&#1077;&#1088; 20 17:26:12 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=213.109.1.187 DST=213.109.234.130 LEN=40 TOS=0x10 PREC=0x60 TTL=247 ID=46272 DF PROTO=TCP SPT=1841 DPT=23 WINDOW=14600 RES=
&#1074;&#1077;&#1088; 20 17:26:21 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=164.68.120.73 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=250 ID=15011 PROTO=TCP SPT=57739 DPT=3559 WINDOW=1024 RES=0
&#1074;&#1077;&#1088; 20 17:26:41 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=92.43.188.69 DST=213.109.234.130 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=4141 DF PROTO=TCP SPT=5516 DPT=6881 WINDOW=8192 RES=


```
Is it symbolic link error or what ?

Thanks!

---

