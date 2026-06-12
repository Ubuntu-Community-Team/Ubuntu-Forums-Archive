---
title: "Ubuntu crashes (hangs) after being left for a while."
date: 2008-02-12
forum: General Help
---

### Post by marshall.robert on 2008-02-12
Hello.

What I have here is a fresh-ish (~4days) install on a Dell Vostro 1500.

Laptop Hardware:
2.0GHz Intel Core 2 Duo
2GB RAM
nVidia 8600GT
Intel ICH8 82801H Chipset
Intel HDA Audio
Intel PRO/Wireless 3945ABG
160GB HDD

So a pretty capable machine.

There is a slight problem with my Gutsy install. It keeps crashing when left for a few hours.

Known Symptoms:
Wireless dies, light still on, killswitch doesnt work.
No programs can open, though the already running ones are fine.
I tried to bring up the network with "ifconfig eth1 up" on the console screen (tty1), just sat there.
I cannot reboot normally or by pressing ctrl+alt+del in a tty, I have to hold the power button.

Its a bit of a shame when you pop out for a bit and you come back and have to reboot...

Any ideas or thoughts or even solutions are all very welcome. :D

Thanks

Rob

PS. Sorry if this thread should go elsewhere, I wasn't sure where to put it.

---

### Post by jimmy the saint on 2008-02-12
I just posted for the exact same issue a couple minutes ago.  I have had this problem with two seperate laptops under both fiesty and gutsy.  It is extremely annoying, especially since I have to do a hard reboot in order to get things going again!!  I sure hope someone in the know replies with some help here because we are in the same boat!!  If I get help, I will repost a solution here.  My post is a few down from yours, so if you get help, let me know!!

---

### Post by marshall.robert on 2008-02-12
You must have started writing the same time as me, cos i didnt see it before, but i saw it just after i posted, heh.

link: [http://ubuntuforums.org/showthread.php?t=694940](http://ubuntuforums.org/showthread.php?t=694940)

---

### Post by apetresc on 2008-02-12
Is there anything telling in /var/log/syslog or /var/log/kern.log or /var/log/Xorg.log right after a hang?

---

### Post by marshall.robert on 2008-02-12
i could probably tell you if i knew what to look for, but i probably wont be able to open it, given the characteristics of the crash

---

### Post by apetresc on 2008-02-12
> **marshall.robert said:**
> i could probably tell you if i knew what to look for, but i probably wont be able to open it, given the characteristics of the crash

Nono, I mean, after the crash :) Ubuntu doesn't rotate them every reboot, since they're most often used for diagnosing crashes.

---

### Post by marshall.robert on 2008-02-12
Oh, my bad, lol, ill open them, tell me what to look for and ill post with what i have. :D

---

### Post by jimmy the saint on 2008-02-12
I have selected the part of my log file relating to the last time my session locked up.  I do not know how to post it in those scroll boxes though, and it is looong because I have no idea which part would be "telling."  If someone could let me know how to do that, I will post it here.

---

### Post by apetresc on 2008-02-12
> **jimmy the saint said:**
> I have selected the part of my log file relating to the last time my session locked up.  I do not know how to post it in those scroll boxes though, and it is looong because I have no idea which part would be "telling."  If someone could let me know how to do that, I will post it here.

Put them in between [ code ] [ /code ] tags (without the spaces between the [ and the words).

> Oh, my bad, lol, ill open them, tell me what to look for and ill post with what i have. 
I'm not sure exactly what I'm looking for. I'm hoping I'll "know it when I see it" :). Just post the end (use tail).

---

### Post by marshall.robert on 2008-02-12
Not sure exactly when it happened, but im pretty sure it was after 12 today:

syslog:
```
Feb 12 12:02:40 rob-laptop -- MARK --
Feb 12 12:06:46 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.128 from 00:0c:29:56:7d:0f via vmnet8
Feb 12 12:06:46 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.128 to 00:0c:29:56:7d:0f via vmnet8
Feb 12 12:09:04 rob-laptop anacron[7809]: Anacron 2.3 started on 2008-02-12
Feb 12 12:09:04 rob-laptop anacron[7809]: Normal exit (0 jobs run)
Feb 12 12:14:45 rob-laptop ntfs-3g[4291]: Unmounting /dev/sda1 (Vista) 
Feb 12 12:14:47 rob-laptop ntfs-3g[4294]: Unmounting /dev/sda3 (XP) 
Feb 12 12:16:52 rob-laptop NetworkManager: <debug> [1202818612.531445] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_5C2C85C52C859B22'). 
Feb 12 12:16:52 rob-laptop NetworkManager: <debug> [1202818612.532257] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3C9889AF988967EA'). 
Feb 12 12:16:53 rob-laptop NetworkManager: <debug> [1202818613.106641] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3C9889AF988967EA'). 
Feb 12 12:16:53 rob-laptop NetworkManager: <debug> [1202818613.157798] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_5C2C85C52C859B22'). 
Feb 12 12:17:01 rob-laptop /USR/SBIN/CRON[8245]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 12:17:15 rob-laptop ntfs-3g[8284]: Version 1.913 
Feb 12 12:17:15 rob-laptop ntfs-3g[8284]: Mounted /dev/sda1 (Read-Write, label "Vista", NTFS 3.1) 
Feb 12 12:17:15 rob-laptop ntfs-3g[8284]: Cmdline options: rw,umask=007,gid=46 
Feb 12 12:17:15 rob-laptop ntfs-3g[8284]: Mount options: noatime,rw,silent,allow_other,nonempty,default_permissions,fsname=/dev/sda1,blkdev,blksize=4096 
Feb 12 12:19:27 rob-laptop vmnet-dhcpd: DHCPDISCOVER from 00:0c:29:56:7d:0f via vmnet8
Feb 12 12:19:28 rob-laptop vmnet-dhcpd: DHCPOFFER on 172.16.159.128 to 00:0c:29:56:7d:0f via vmnet8
Feb 12 12:19:28 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.128 from 00:0c:29:56:7d:0f via vmnet8
Feb 12 12:19:28 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.128 to 00:0c:29:56:7d:0f via vmnet8
Feb 12 12:22:00 rob-laptop avahi-daemon[5472]: Invalid legacy unicast query packet.
Feb 12 12:22:00 rob-laptop avahi-daemon[5472]: Recieved repsonse with invalid source port 32921 on interface 'eth1.0'
Feb 12 12:22:00 rob-laptop avahi-daemon[5472]: Invalid legacy unicast query packet.
Feb 12 12:22:01 rob-laptop last message repeated 2 times
Feb 12 12:22:01 rob-laptop avahi-daemon[5472]: Recieved repsonse with invalid source port 32921 on interface 'eth1.0'
Feb 12 12:22:15 rob-laptop last message repeated 4 times
Feb 12 12:22:55 rob-laptop avahi-daemon[5472]: Recieved repsonse with invalid source port 32921 on interface 'eth1.0'
Feb 12 12:25:29 rob-laptop avahi-daemon[5472]: Recieved repsonse with invalid source port 32922 on interface 'eth1.0'
Feb 12 12:42:40 rob-laptop -- MARK --
Feb 12 13:02:40 rob-laptop -- MARK --
Feb 12 13:17:01 rob-laptop /USR/SBIN/CRON[8456]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 13:42:40 rob-laptop -- MARK --
Feb 12 14:02:40 rob-laptop -- MARK --
Feb 12 14:17:01 rob-laptop /USR/SBIN/CRON[8669]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 14:42:40 rob-laptop -- MARK --
Feb 12 14:52:36 rob-laptop vmnet-dhcpd: DHCPDISCOVER from 00:0c:29:56:7d:0f via vmnet8
Feb 12 14:52:37 rob-laptop vmnet-dhcpd: DHCPOFFER on 172.16.159.128 to 00:0c:29:56:7d:0f via vmnet8
Feb 12 14:52:37 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.128 from 00:0c:29:56:7d:0f via vmnet8
Feb 12 14:52:40 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.128 to 00:0c:29:56:7d:0f via vmnet8
Feb 12 14:54:44 rob-laptop avahi-daemon[5472]: Invalid legacy unicast query packet.
Feb 12 14:54:44 rob-laptop avahi-daemon[5472]: Recieved repsonse with invalid source port 32924 on interface 'eth1.0'
Feb 12 14:54:44 rob-laptop avahi-daemon[5472]: Invalid legacy unicast query packet.
Feb 12 14:54:45 rob-laptop last message repeated 2 times
Feb 12 14:54:45 rob-laptop avahi-daemon[5472]: Recieved repsonse with invalid source port 32924 on interface 'eth1.0'
Feb 12 14:55:19 rob-laptop last message repeated 4 times
Feb 12 14:56:30 rob-laptop last message repeated 2 times
Feb 12 15:16:02 rob-laptop ntfs-3g[8854]: Version 1.913 
Feb 12 15:16:02 rob-laptop ntfs-3g[8854]: Mounted /dev/sda3 (Read-Write, label "XP", NTFS 3.1) 
Feb 12 15:16:02 rob-laptop ntfs-3g[8854]: Cmdline options: rw,umask=007,gid=46 
Feb 12 15:16:02 rob-laptop ntfs-3g[8854]: Mount options: noatime,rw,silent,allow_other,nonempty,default_permissions,fsname=/dev/sda3,blkdev,blksize=4096 
Feb 12 15:17:01 rob-laptop /USR/SBIN/CRON[8858]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 15:23:02 rob-laptop NetworkManager: <debug> [1202829782.412961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135'). 
Feb 12 15:23:02 rob-laptop NetworkManager: <debug> [1202829782.419944] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0'). 
Feb 12 15:23:02 rob-laptop NetworkManager: <debug> [1202829782.521564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_usbraw'). 
Feb 12 15:23:07 rob-laptop NetworkManager: <debug> [1202829787.696849] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host'). 
Feb 12 15:23:07 rob-laptop NetworkManager: <debug> [1202829787.709283] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0'). 
Feb 12 15:23:07 rob-laptop NetworkManager: <debug> [1202829787.718717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 15:23:08 rob-laptop NetworkManager: <debug> [1202829788.115082] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_2500BEA_External_575843393037333436303135_0_0'). 
Feb 12 15:23:08 rob-laptop NetworkManager: <debug> [1202829788.247799] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B0F8AD42F8AD0824'). 
Feb 12 15:23:08 rob-laptop NetworkManager: <debug> [1202829788.359226] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_1401196d_3423_4b6d_8b35_46530321519d'). 
Feb 12 15:23:08 rob-laptop NetworkManager: <debug> [1202829788.491329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a12b464c_8795_4f26_a8ab_5e13b7aaf665'). 
Feb 12 15:23:10 rob-laptop ntfs-3g[8997]: Version 1.913 
Feb 12 15:23:10 rob-laptop ntfs-3g[8997]: Mounted /dev/sdb1 (Read-Write, label "PORNARCHIVE", NTFS 3.1) 
Feb 12 15:23:10 rob-laptop ntfs-3g[8997]: Cmdline options: rw,nosuid,nodev,locale=en_GB.UTF-8 
Feb 12 15:23:10 rob-laptop ntfs-3g[8997]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdb1,blkdev,blksize=512 
Feb 12 15:23:10 rob-laptop hald: mounted /dev/sdb1 on behalf of uid 1000
Feb 12 15:23:10 rob-laptop hald: mounted /dev/sdb2 on behalf of uid 1000
Feb 12 15:37:08 rob-laptop vmnet-dhcpd: DHCPDISCOVER from 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:37:09 rob-laptop vmnet-dhcpd: DHCPOFFER on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:37:09 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.130 from 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:37:09 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:37:09 rob-laptop vmnet-dhcpd: DHCPDISCOVER from 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:37:09 rob-laptop vmnet-dhcpd: DHCPOFFER on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:37:09 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.130 from 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:37:09 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:40:57 rob-laptop vmnet-dhcpd: DHCPINFORM from 172.16.159.130
Feb 12 15:41:02 rob-laptop vmnet-dhcpd: DHCPINFORM from 172.16.159.130
Feb 12 15:50:03 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.130 from 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:50:03 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:52:21 rob-laptop vmnet-dhcpd: DHCPINFORM from 172.16.159.130
Feb 12 15:52:25 rob-laptop vmnet-dhcpd: DHCPINFORM from 172.16.159.130
Feb 12 15:54:00 rob-laptop NetworkManager: <info>  eth1: link timed out. 
Feb 12 15:54:00 rob-laptop NetworkManager: <info>  SWITCH: found better connection 'eth1/marshall' than current connection 'eth1/marshall'.  same_ssid=1, have_link=0 
Feb 12 15:54:00 rob-laptop NetworkManager: <info>  Will activate connection 'eth1/marshall'. 
Feb 12 15:54:00 rob-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Feb 12 15:54:00 rob-laptop NetworkManager: <info>  Deactivating device eth1. 
Feb 12 15:54:00 rob-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6347
Feb 12 15:54:00 rob-laptop dhclient: killed old client process, removed PID file
Feb 12 15:54:00 rob-laptop dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 12 15:54:00 rob-laptop avahi-daemon[5472]: Withdrawing address record for 192.168.1.2 on eth1.
Feb 12 15:54:00 rob-laptop avahi-daemon[5472]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 15:54:00 rob-laptop avahi-daemon[5472]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 15:54:01 rob-laptop avahi-daemon[5472]: Withdrawing address record for fe80::21c:bfff:fe09:d5c7 on eth1.
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  Activation (eth1) started... 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'marshall' is encrypted, and a key exists.  No new key needed. 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Feb 12 15:54:01 rob-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 15:54:02 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Feb 12 15:54:02 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Feb 12 15:54:02 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Feb 12 15:54:02 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Feb 12 15:54:02 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Feb 12 15:54:02 rob-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant5^I' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was '0' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6d61727368616c6c' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 15:54:03 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 15:54:11 rob-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Feb 12 15:54:39 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 15:54:42 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 15:54:47 rob-laptop avahi-daemon[5472]: Registering new address record for fe80::21c:bfff:fe09:d5c7 on eth1.*.
Feb 12 15:54:59 rob-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'marshall'. 
Feb 12 15:54:59 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb 12 15:54:59 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Feb 12 15:55:00 rob-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Feb 12 15:55:00 rob-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Feb 12 15:55:00 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Feb 12 15:55:00 rob-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Feb 12 15:55:01 rob-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Feb 12 15:55:03 rob-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Feb 12 15:55:03 rob-laptop dhclient: DHCPOFFER from 192.168.1.1
Feb 12 15:55:03 rob-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Feb 12 15:55:03 rob-laptop dhclient: DHCPACK from 192.168.1.1
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Registering new address record for 192.168.1.2 on eth1.IPv4.
Feb 12 15:55:03 rob-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Feb 12 15:55:03 rob-laptop dhclient: bound to 192.168.1.2 -- renewal in 36019 seconds.
Feb 12 15:55:03 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Feb 12 15:55:03 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Feb 12 15:55:03 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Feb 12 15:55:03 rob-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>    address 192.168.1.2 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>    netmask 255.255.255.0 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>    broadcast 192.168.1.255 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>    gateway 192.168.1.1 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>    nameserver 192.168.1.1 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>    domain name 'home' 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Feb 12 15:55:03 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Withdrawing address record for 192.168.1.2 on eth1.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Withdrawing address record for fe80::21c:bfff:fe09:d5c7 on eth1.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 15:55:03 rob-laptop avahi-daemon[5472]: Registering new address record for 192.168.1.2 on eth1.IPv4.
Feb 12 15:55:04 rob-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Feb 12 15:55:04 rob-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Feb 12 15:55:04 rob-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Feb 12 15:55:04 rob-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Feb 12 15:55:04 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 12 15:55:04 rob-laptop ntpdate[9662]: step time server 91.189.94.4 offset -1.222790 sec
Feb 12 15:55:05 rob-laptop avahi-daemon[5472]: Registering new address record for fe80::21c:bfff:fe09:d5c7 on eth1.*.
Feb 12 15:55:15 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.130 from 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:55:17 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 15:55:54 rob-laptop anacron[9702]: Anacron 2.3 started on 2008-02-12
Feb 12 15:55:54 rob-laptop anacron[9702]: Normal exit (0 jobs run)
Feb 12 16:17:01 rob-laptop /USR/SBIN/CRON[9722]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 16:26:07 rob-laptop NetworkManager: <info>  eth1: link timed out. 
Feb 12 16:26:07 rob-laptop NetworkManager: <info>  SWITCH: found better connection 'eth1/marshall' than current connection 'eth1/marshall'.  same_ssid=1, have_link=0 
Feb 12 16:26:07 rob-laptop NetworkManager: <info>  Will activate connection 'eth1/marshall'. 
Feb 12 16:26:07 rob-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Feb 12 16:26:07 rob-laptop NetworkManager: <info>  Deactivating device eth1. 
Feb 12 16:26:07 rob-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 9597
Feb 12 16:26:07 rob-laptop dhclient: killed old client process, removed PID file
Feb 12 16:26:07 rob-laptop dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 12 16:26:07 rob-laptop avahi-daemon[5472]: Withdrawing address record for 192.168.1.2 on eth1.
Feb 12 16:26:07 rob-laptop avahi-daemon[5472]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 16:26:07 rob-laptop avahi-daemon[5472]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 16:26:08 rob-laptop avahi-daemon[5472]: Withdrawing address record for fe80::21c:bfff:fe09:d5c7 on eth1.
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  Activation (eth1) started... 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'marshall' is encrypted, and a key exists.  No new key needed. 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Feb 12 16:26:08 rob-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant7^I' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was '0' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6d61727368616c6c' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 16:26:09 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 16:26:47 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 16:27:19 rob-laptop last message repeated 16 times
Feb 12 16:28:07 rob-laptop last message repeated 24 times
Feb 12 16:28:09 rob-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long (>120s), failing activation. 
Feb 12 16:28:09 rob-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Feb 12 16:28:09 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 16:28:09 rob-laptop NetworkManager: <info>  Activation (eth1) failed for access point (marshall) 
Feb 12 16:28:09 rob-laptop NetworkManager: <info>  Activation (eth1) failed. 
Feb 12 16:28:09 rob-laptop NetworkManager: <info>  Deactivating device eth1. 
Feb 12 16:28:09 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Resource temporarily unavailable 
Feb 12 16:28:09 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Resource temporarily unavailable 
Feb 12 16:28:09 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: Resource temporarily unavailable 
Feb 12 16:28:09 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_mode(): error setting card eth1 to Infrastructure mode: Resource temporarily unavailable 
Feb 12 16:42:41 rob-laptop -- MARK --
Feb 12 17:02:41 rob-laptop -- MARK --
Feb 12 17:17:01 rob-laptop /USR/SBIN/CRON[9794]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 17:42:41 rob-laptop -- MARK --
Feb 12 18:02:41 rob-laptop -- MARK --
Feb 12 18:04:28 rob-laptop init: tty4 main process (4585) killed by TERM signal
Feb 12 18:04:28 rob-laptop init: tty5 main process (4586) killed by TERM signal
Feb 12 18:04:28 rob-laptop init: tty1 main process (4592) killed by TERM signal
Feb 12 18:04:28 rob-laptop init: tty2 main process (4588) killed by TERM signal
Feb 12 18:04:28 rob-laptop init: tty3 main process (4590) killed by TERM signal
Feb 12 18:04:28 rob-laptop init: tty6 main process (4593) killed by TERM signal
Feb 12 18:09:23 rob-laptop init: control-alt-delete respawning too fast, stopped
Feb 12 18:09:24 rob-laptop last message repeated 12 times
Feb 12 18:09:26 rob-laptop init: rc6 main process (9848) killed by TERM signal
Feb 12 18:14:56 rob-laptop syslogd 1.4.1#21ubuntu3: restart.
Feb 12 18:14:56 rob-laptop NetworkManager: <info>  starting... 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.547101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.904370] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.904773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a00'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.905071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a01'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.905357] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10de_407'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.905647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2834'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.906011] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.906338] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.906650] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2835'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.906939] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.907229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.907517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283a'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.907825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.908211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.908671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.909240] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283f'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.909905] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2841'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.910294] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_4222'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.910973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2845'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.911942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2830'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.912329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.912691] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.913052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2831'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.913413] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.913772] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.914132] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2832'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.914502] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.914861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.915233] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2836'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.915592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.915910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.916202] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.961576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.961982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.962287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.962612] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.962954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.963256] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.963542] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2815'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.963876] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.964302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.965549] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host_scsi_device_lun0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.965945] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2828'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.966342] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2828_scsi_host'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.966718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2828_scsi_host_scsi_device_lun0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.967049] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283e'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.967375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_coretemp_0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.967726] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_coretemp_1'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.968098] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.968469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.968842] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.969152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.969459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_Synaptics_pass_through'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.969786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.970516] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.970822] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.971124] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.971428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.971756] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.972445] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.972748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.973094] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Feb 12 18:14:56 rob-laptop NetworkManager: <debug> [1202840096.973404] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.010477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.010860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.011169] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.011517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.011846] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.012259] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.012601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.012969] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.013302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.014816] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.015128] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.015471] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.015792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1c_23_9c_a1_50'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  Deactivating device eth0. 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.082973] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1c_bf_09_d5_c7'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw3945'. 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Feb 12 18:14:57 rob-laptop NetworkManager: <info>  Deactivating device eth1. 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.146141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.146550] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2828_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.146872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.147186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_control__1'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.147520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.147848] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_mixer__1'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.148180] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_capture_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.148493] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_playback_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.148804] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.149121] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.149450] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.149759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.150080] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.150394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.150711] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.151040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_usbraw'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.151351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_usbraw'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.151682] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.151999] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.152335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.152627] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_usbraw'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.152940] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.153274] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST9160821AS_5MA68RM7'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.153605] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_5C2C85C52C859B22'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.153952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_0fbec2c8_0304_44dc_9f18_65154211256e'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.260244] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3C9889AF988967EA'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.416799] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.470211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.470719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.471152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Feb 12 18:14:57 rob-laptop NetworkManager: <debug> [1202840097.471600] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_L632H'). 
Feb 12 18:14:58 rob-laptop xinetd[5387]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Feb 12 18:14:58 rob-laptop xinetd[5387]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Feb 12 18:14:58 rob-laptop xinetd[5387]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Feb 12 18:14:58 rob-laptop xinetd[5387]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Feb 12 18:14:58 rob-laptop xinetd[5387]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Feb 12 18:14:58 rob-laptop xinetd[5387]: Reading included configuration file: /etc/xinetd.d/vmware-authd [file=/etc/xinetd.d/vmware-authd] [line=28]
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing chargen
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing chargen
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing daytime
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing daytime
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing discard
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing discard
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing echo
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing echo
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing time
Feb 12 18:14:58 rob-laptop xinetd[5387]: removing time
Feb 12 18:14:58 rob-laptop xinetd[5387]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Feb 12 18:14:58 rob-laptop xinetd[5387]: Started working: 1 available service
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: Successfully dropped root privileges.
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: avahi-daemon 0.6.20 starting up.
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: Successfully called chroot().
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: Successfully dropped remaining capabilities.
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: No service file found in /etc/avahi/services.
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: Network interface enumeration completed.
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: Registering HINFO record with values 'I686'/'LINUX'.
Feb 12 18:14:58 rob-laptop avahi-daemon[5493]: Server startup complete. Host name is rob-laptop.local. Local service cookie is 368292532.
Feb 12 18:14:58 rob-laptop dhcdbd: Started up.
Feb 12 18:14:58 rob-laptop hcid[5528]: Bluetooth HCI daemon
Feb 12 18:14:58 rob-laptop hcid[5528]: Starting SDP server
Feb 12 18:14:58 rob-laptop hcid[5528]: Created local server at unix:abstract=/var/run/dbus-CPLskEhLyE,guid=f71aa5e77fdb9b5a6f3b920047b1e222
Feb 12 18:14:58 rob-laptop input[5540]: Bluetooth Input daemon
Feb 12 18:14:58 rob-laptop input[5540]: Registered input manager path:/org/bluez/input
Feb 12 18:14:58 rob-laptop audio[5541]: Bluetooth Audio daemon
Feb 12 18:14:58 rob-laptop audio[5541]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Feb 12 18:14:58 rob-laptop audio[5541]: Unix socket created: 5
Feb 12 18:14:58 rob-laptop audio[5541]: add_service_record: got record id 0x10000
Feb 12 18:14:58 rob-laptop audio[5541]: add_service_record: got record id 0x10001
Feb 12 18:14:58 rob-laptop audio[5541]: Registered manager path:/org/bluez/audio
Feb 12 18:15:03 rob-laptop /usr/sbin/cron[5641]: (CRON) INFO (pidfile fd = 3)
Feb 12 18:15:03 rob-laptop /usr/sbin/cron[5642]: (CRON) STARTUP (fork ok)
Feb 12 18:15:03 rob-laptop /usr/sbin/cron[5642]: (CRON) INFO (Running @reboot jobs)
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.247.1.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: New relevant interface vmnet1.IPv4 for mDNS.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Registering new address record for 192.168.247.1 on vmnet1.IPv4.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.159.1.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: New relevant interface vmnet8.IPv4 for mDNS.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Registering new address record for 172.16.159.1 on vmnet8.IPv4.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Withdrawing address record for 172.16.159.1 on vmnet8.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 172.16.159.1.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Interface vmnet8.IPv4 no longer relevant for mDNS.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.159.1.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: New relevant interface vmnet8.IPv4 for mDNS.
Feb 12 18:15:05 rob-laptop avahi-daemon[5493]: Registering new address record for 172.16.159.1 on vmnet8.IPv4.
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: All rights reserved.
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: 
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: 
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: All rights reserved.
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: 
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: 
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Configured subnet: 172.16.159.0
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.159.254
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Recving on     VNet/vmnet8/172.16.159.0
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Sending on     VNet/vmnet8/172.16.159.0
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Configured subnet: 192.168.247.0
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.247.254
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.247.0
Feb 12 18:15:05 rob-laptop vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.247.0
Feb 12 18:15:17 rob-laptop hcid[5528]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Feb 12 18:15:17 rob-laptop hcid[5528]: Default authorization agent (:1.17, /org/bluez/auth) registered
Feb 12 18:15:26 rob-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Feb 12 18:15:27 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Will activate connection 'eth1/marshall'. 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) started... 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'marshall' is encrypted, but NO valid key exists.  New key needed. 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'marshall'. 
Feb 12 18:15:27 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 18:15:32 rob-laptop avahi-daemon[5493]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Feb 12 18:15:32 rob-laptop avahi-daemon[5493]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Feb 12 18:16:33 rob-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'marshall' received. 
Feb 12 18:16:33 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 18:16:33 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 18:16:33 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 18:16:33 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 18:16:33 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 18:16:33 rob-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'marshall' is encrypted, and a key exists.  No new key needed. 
Feb 12 18:16:34 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Feb 12 18:16:34 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Feb 12 18:16:34 rob-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was '0' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6d61727368616c6c' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 18:16:35 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 18:16:39 rob-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'marshall'. 
Feb 12 18:16:39 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb 12 18:16:39 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Feb 12 18:16:40 rob-laptop avahi-daemon[5493]: Registering new address record for fe80::21c:bfff:fe09:d5c7 on eth1.*.
Feb 12 18:16:40 rob-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Feb 12 18:16:40 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Feb 12 18:16:40 rob-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Feb 12 18:16:41 rob-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Feb 12 18:16:43 rob-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Feb 12 18:16:43 rob-laptop dhclient: DHCPOFFER from 192.168.1.1
Feb 12 18:16:43 rob-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Feb 12 18:16:43 rob-laptop dhclient: DHCPACK from 192.168.1.1
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Registering new address record for 192.168.1.2 on eth1.IPv4.
Feb 12 18:16:43 rob-laptop dhclient: bound to 192.168.1.2 -- renewal in 42605 seconds.
Feb 12 18:16:43 rob-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Feb 12 18:16:43 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Feb 12 18:16:43 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Feb 12 18:16:43 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Feb 12 18:16:43 rob-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>    address 192.168.1.2 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>    netmask 255.255.255.0 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>    broadcast 192.168.1.255 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>    gateway 192.168.1.1 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>    nameserver 192.168.1.1 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>    domain name 'home' 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Feb 12 18:16:43 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Withdrawing address record for 192.168.1.2 on eth1.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Withdrawing address record for fe80::21c:bfff:fe09:d5c7 on eth1.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 18:16:43 rob-laptop avahi-daemon[5493]: Registering new address record for 192.168.1.2 on eth1.IPv4.
Feb 12 18:16:44 rob-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Feb 12 18:16:44 rob-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Feb 12 18:16:44 rob-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Feb 12 18:16:44 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 12 18:16:44 rob-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Feb 12 18:16:44 rob-laptop ntpdate[6289]: adjust time server 91.189.94.4 offset 0.361561 sec
Feb 12 18:16:45 rob-laptop avahi-daemon[5493]: Registering new address record for fe80::21c:bfff:fe09:d5c7 on eth1.*.
Feb 12 18:17:01 rob-laptop /USR/SBIN/CRON[6304]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 18:34:56 rob-laptop -- MARK --
Feb 12 18:35:26 rob-laptop NetworkManager: <debug> [1202841326.769443] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135'). 
Feb 12 18:35:26 rob-laptop NetworkManager: <debug> [1202841326.951801] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0'). 
Feb 12 18:35:26 rob-laptop NetworkManager: <debug> [1202841326.990067] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_usbraw'). 
Feb 12 18:35:32 rob-laptop NetworkManager: <debug> [1202841332.153843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host'). 
Feb 12 18:35:32 rob-laptop NetworkManager: <debug> [1202841332.162978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0'). 
Feb 12 18:35:32 rob-laptop NetworkManager: <debug> [1202841332.170713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 18:35:32 rob-laptop NetworkManager: <debug> [1202841332.260748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_2500BEA_External_575843393037333436303135_0_0'). 
Feb 12 18:35:32 rob-laptop NetworkManager: <debug> [1202841332.632835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B0F8AD42F8AD0824'). 
Feb 12 18:35:32 rob-laptop NetworkManager: <debug> [1202841332.763371] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a12b464c_8795_4f26_a8ab_5e13b7aaf665'). 
Feb 12 18:35:32 rob-laptop NetworkManager: <debug> [1202841332.861962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_1401196d_3423_4b6d_8b35_46530321519d'). 
Feb 12 18:35:35 rob-laptop ntfs-3g[6837]: Version 1.913 
Feb 12 18:35:35 rob-laptop ntfs-3g[6837]: Mounted /dev/sdb1 (Read-Write, label "PORNARCHIVE", NTFS 3.1) 
Feb 12 18:35:35 rob-laptop ntfs-3g[6837]: Cmdline options: rw,nosuid,nodev,locale=en_GB.UTF-8 
Feb 12 18:35:35 rob-laptop ntfs-3g[6837]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdb1,blkdev,blksize=512 
Feb 12 18:35:35 rob-laptop hald: mounted /dev/sdb1 on behalf of uid 1000
Feb 12 18:35:35 rob-laptop hald: mounted /dev/sdb2 on behalf of uid 1000
Feb 12 18:54:56 rob-laptop -- MARK --
Feb 12 19:00:00 rob-laptop vmnet-dhcpd: DHCPDISCOVER from 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:00:01 rob-laptop vmnet-dhcpd: DHCPOFFER on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:00:01 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.130 from 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:00:01 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:05:48 rob-laptop NetworkManager: <info>  eth1: link timed out. 
Feb 12 19:05:48 rob-laptop NetworkManager: <info>  SWITCH: found better connection 'eth1/marshall' than current connection 'eth1/marshall'.  same_ssid=1, have_link=0 
Feb 12 19:05:48 rob-laptop NetworkManager: <info>  Will activate connection 'eth1/marshall'. 
Feb 12 19:05:48 rob-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Feb 12 19:05:48 rob-laptop NetworkManager: <info>  Deactivating device eth1. 
Feb 12 19:05:48 rob-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6228
Feb 12 19:05:48 rob-laptop dhclient: killed old client process, removed PID file
Feb 12 19:05:48 rob-laptop dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 12 19:05:48 rob-laptop avahi-daemon[5493]: Withdrawing address record for 192.168.1.2 on eth1.
Feb 12 19:05:48 rob-laptop avahi-daemon[5493]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 19:05:48 rob-laptop avahi-daemon[5493]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  Activation (eth1) started... 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'marshall' is encrypted, and a key exists.  No new key needed. 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Feb 12 19:05:49 rob-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 19:05:49 rob-laptop avahi-daemon[5493]: Withdrawing address record for fe80::21c:bfff:fe09:d5c7 on eth1.
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant5^I' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was '0' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6d61727368616c6c' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 19:05:50 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 19:06:29 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 19:06:31 rob-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 19:06:35 rob-laptop avahi-daemon[5493]: Registering new address record for fe80::21c:bfff:fe09:d5c7 on eth1.*.
Feb 12 19:06:40 rob-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'marshall'. 
Feb 12 19:06:40 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb 12 19:06:40 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Feb 12 19:06:41 rob-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Feb 12 19:06:41 rob-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Feb 12 19:06:41 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Feb 12 19:06:41 rob-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Feb 12 19:06:42 rob-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Feb 12 19:06:46 rob-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Feb 12 19:06:46 rob-laptop dhclient: DHCPOFFER from 192.168.1.1
Feb 12 19:06:46 rob-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Feb 12 19:06:46 rob-laptop dhclient: DHCPACK from 192.168.1.1
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Registering new address record for 192.168.1.2 on eth1.IPv4.
Feb 12 19:06:46 rob-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Feb 12 19:06:46 rob-laptop dhclient: bound to 192.168.1.2 -- renewal in 35157 seconds.
Feb 12 19:06:46 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Feb 12 19:06:46 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Feb 12 19:06:46 rob-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Feb 12 19:06:46 rob-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>    address 192.168.1.2 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>    netmask 255.255.255.0 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>    broadcast 192.168.1.255 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>    gateway 192.168.1.1 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>    nameserver 192.168.1.1 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>    domain name 'home' 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Feb 12 19:06:46 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Withdrawing address record for 192.168.1.2 on eth1.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Withdrawing address record for fe80::21c:bfff:fe09:d5c7 on eth1.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.2.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 19:06:46 rob-laptop avahi-daemon[5493]: Registering new address record for 192.168.1.2 on eth1.IPv4.
Feb 12 19:06:47 rob-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Feb 12 19:06:47 rob-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Feb 12 19:06:47 rob-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Feb 12 19:06:47 rob-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Feb 12 19:06:47 rob-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 12 19:06:47 rob-laptop ntpdate[7423]: adjust time server 91.189.94.4 offset -0.281267 sec
Feb 12 19:06:48 rob-laptop avahi-daemon[5493]: Registering new address record for fe80::21c:bfff:fe09:d5c7 on eth1.*.
Feb 12 19:13:55 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.130 from 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:13:55 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:17:01 rob-laptop /USR/SBIN/CRON[7475]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 19:34:56 rob-laptop -- MARK --
Feb 12 19:44:54 rob-laptop vmnet-dhcpd: DHCPREQUEST for 172.16.159.130 from 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:44:54 rob-laptop vmnet-dhcpd: DHCPACK on 172.16.159.130 to 00:0c:29:77:3a:fe via vmnet8
Feb 12 19:54:56 rob-laptop -- MARK --
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.332285] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.335416] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a12b464c_8795_4f26_a8ab_5e13b7aaf665'). 
Feb 12 20:02:02 rob-laptop hald[5106]: forcibly attempting to lazy unmount /dev/sdb2 as enclosing drive was disconnected
Feb 12 20:02:02 rob-laptop hald: unmounted /dev/sdb2 from '/media/disk' on behalf of uid 0
Feb 12 20:02:02 rob-laptop hald[5106]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.458284] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_1401196d_3423_4b6d_8b35_46530321519d'). 
Feb 12 20:02:02 rob-laptop ntfs-3g[6837]: Unmounting /dev/sdb1 (PORNARCHIVE) 
Feb 12 20:02:02 rob-laptop hald: unmounted /dev/sdb1 from '/media/PORNARCHIVE' on behalf of uid 0
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.523047] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B0F8AD42F8AD0824'). 
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.543935] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0'). 
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.544940] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_usbraw'). 
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.545489] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_2500BEA_External_575843393037333436303135_0_0'). 
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.546889] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0'). 
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.546943] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135'). 
Feb 12 20:02:02 rob-laptop NetworkManager: <debug> [1202846522.551938] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host'). 
Feb 12 20:06:27 rob-laptop NetworkManager: <debug> [1202846787.579763] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135'). 
Feb 12 20:06:27 rob-laptop NetworkManager: <debug> [1202846787.668525] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0'). 
Feb 12 20:06:27 rob-laptop NetworkManager: <debug> [1202846787.699093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_usbraw'). 
Feb 12 20:06:32 rob-laptop NetworkManager: <debug> [1202846792.784322] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host'). 
Feb 12 20:06:32 rob-laptop NetworkManager: <debug> [1202846792.786937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0'). 
Feb 12 20:06:32 rob-laptop NetworkManager: <debug> [1202846792.787950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 20:06:33 rob-laptop NetworkManager: <debug> [1202846793.217657] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_2500BEA_External_575843393037333436303135_0_0'). 
Feb 12 20:06:33 rob-laptop NetworkManager: <debug> [1202846793.300744] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a12b464c_8795_4f26_a8ab_5e13b7aaf665'). 
Feb 12 20:06:33 rob-laptop NetworkManager: <debug> [1202846793.391931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_1401196d_3423_4b6d_8b35_46530321519d'). 
Feb 12 20:06:33 rob-laptop hald: mounted /dev/sdb2 on behalf of uid 1000
Feb 12 20:06:33 rob-laptop NetworkManager: <debug> [1202846793.642004] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B0F8AD42F8AD0824'). 
Feb 12 20:06:36 rob-laptop ntfs-3g[8103]: Version 1.913 
Feb 12 20:06:36 rob-laptop ntfs-3g[8103]: Mounted /dev/sdb1 (Read-Write, label "PORNARCHIVE", NTFS 3.1) 
Feb 12 20:06:36 rob-laptop ntfs-3g[8103]: Cmdline options: rw,nosuid,nodev,locale=en_GB.UTF-8 
Feb 12 20:06:36 rob-laptop ntfs-3g[8103]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdb1,blkdev,blksize=512 
Feb 12 20:06:36 rob-laptop hald: mounted /dev/sdb1 on behalf of uid 1000
Feb 12 20:10:24 rob-laptop ntfs-3g[8103]: Unmounting /dev/sdb1 (PORNARCHIVE) 
Feb 12 20:10:24 rob-laptop hald: unmounted /dev/sdb1 from '/media/PORNARCHIVE' on behalf of uid 1000
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.649594] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.655382] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a12b464c_8795_4f26_a8ab_5e13b7aaf665'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.658951] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host_scsi_device_lun0'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.659067] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0_scsi_host'). 
Feb 12 20:10:31 rob-laptop hald[5106]: forcibly attempting to lazy unmount /dev/sdb2 as enclosing drive was disconnected
Feb 12 20:10:31 rob-laptop hald: unmounted /dev/sdb2 from '/media/disk' on behalf of uid 0
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.722913] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_1401196d_3423_4b6d_8b35_46530321519d'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.730145] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B0F8AD42F8AD0824'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.733493] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_if0'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.736323] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135_usbraw'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.738847] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1058_702_575843393037333436303135'). 
Feb 12 20:10:31 rob-laptop NetworkManager: <debug> [1202847031.741781] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_2500BEA_External_575843393037333436303135_0_0'). 
Feb 12 20:17:01 rob-laptop /USR/SBIN/CRON[8332]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 20:34:56 rob-laptop -- MARK --
Feb 12 20:54:56 rob-laptop -- MARK --
```

kern:
```
has nothing after "Feb 12 00:08:15 rob-laptop kernel: Kernel log daemon terminating."
```

xorg:
```
has no date so here is all of it:
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux rob-laptop 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 12 18:15:00 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a00 card 1028,0228 rev 0c class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2a01 card 0000,0000 rev 0c class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,0228 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,0228 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,0228 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,0228 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,0228 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,0228 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,0228 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,0228 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 1028,0228 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 1028,0228 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2828 card 1028,0228 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,0228 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0407 card 1028,0228 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,170c card 1028,0228 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0832 card 1028,0228 rev 05 class 0c,00,10 hdr 80
(II) PCI: 03:01:1: chip 1180,0822 card 1028,0228 rev 22 class 08,05,01 hdr 80
(II) PCI: 03:01:2: chip 1180,0843 card 1028,0228 rev 12 class 08,80,00 hdr 80
(II) PCI: 03:01:3: chip 1180,0592 card 1028,0228 rev 12 class 08,80,00 hdr 80
(II) PCI: 03:01:4: chip 1180,0852 card 1028,0228 rev 12 class 08,80,00 hdr 80
(II) PCI: 0c:00:0: chip 8086,4222 card 8086,1021 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfeafffff (0x4b00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xf9f00000 - 0xf9ffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 13: bridge is at (0:28:3), (0,13,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 13 non-prefetchable memory range:
	[0] -1	0	0xf9c00000 - 0xf9efffff (0x300000) MX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9b00000 - 0xf9bfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0407) rev 161, Mem @ 0xfd000000/24, 0xe0000000/28, 0xfa000000/25, I/O @ 0xdf00/7, BIOS @ 0xfea00000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xf9fff000 - 0xf9ffffff (0x1000) MX[B]
	[1] -1	0	0xf9bfd700 - 0xf9bfd7ff (0x100) MX[B]
	[2] -1	0	0xf9bfd600 - 0xf9bfd6ff (0x100) MX[B]
	[3] -1	0	0xf9bfd500 - 0xf9bfd5ff (0x100) MX[B]
	[4] -1	0	0xf9bfd400 - 0xf9bfd4ff (0x100) MX[B]
	[5] -1	0	0xf9bfd800 - 0xf9bfdfff (0x800) MX[B]
	[6] -1	0	0xf9bfe000 - 0xf9bfffff (0x2000) MX[B]
	[7] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[8] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[10] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[11] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[16] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[17] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[18] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[19] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[20] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[21] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[22] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[28] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[29] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[30] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[31] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[32] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9fff000 - 0xf9ffffff (0x1000) MX[B]
	[1] -1	0	0xf9bfd700 - 0xf9bfd7ff (0x100) MX[B]
	[2] -1	0	0xf9bfd600 - 0xf9bfd6ff (0x100) MX[B]
	[3] -1	0	0xf9bfd500 - 0xf9bfd5ff (0x100) MX[B]
	[4] -1	0	0xf9bfd400 - 0xf9bfd4ff (0x100) MX[B]
	[5] -1	0	0xf9bfd800 - 0xf9bfdfff (0x800) MX[B]
	[6] -1	0	0xf9bfe000 - 0xf9bfffff (0x2000) MX[B]
	[7] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[8] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[9] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[10] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[11] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[16] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[17] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[18] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[19] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[20] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[21] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[22] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[28] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[29] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[30] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[31] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[32] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff000 - 0xf9ffffff (0x1000) MX[B]
	[5] -1	0	0xf9bfd700 - 0xf9bfd7ff (0x100) MX[B]
	[6] -1	0	0xf9bfd600 - 0xf9bfd6ff (0x100) MX[B]
	[7] -1	0	0xf9bfd500 - 0xf9bfd5ff (0x100) MX[B]
	[8] -1	0	0xf9bfd400 - 0xf9bfd4ff (0x100) MX[B]
	[9] -1	0	0xf9bfd800 - 0xf9bfdfff (0x800) MX[B]
	[10] -1	0	0xf9bfe000 - 0xf9bfffff (0x2000) MX[B]
	[11] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[12] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[13] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[14] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[15] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[22] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[23] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[24] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[25] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[26] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[27] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[28] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[34] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[35] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[36] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[37] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[38] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff000 - 0xf9ffffff (0x1000) MX[B]
	[5] -1	0	0xf9bfd700 - 0xf9bfd7ff (0x100) MX[B]
	[6] -1	0	0xf9bfd600 - 0xf9bfd6ff (0x100) MX[B]
	[7] -1	0	0xf9bfd500 - 0xf9bfd5ff (0x100) MX[B]
	[8] -1	0	0xf9bfd400 - 0xf9bfd4ff (0x100) MX[B]
	[9] -1	0	0xf9bfd800 - 0xf9bfdfff (0x800) MX[B]
	[10] -1	0	0xf9bfe000 - 0xf9bfffff (0x2000) MX[B]
	[11] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[12] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[13] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[14] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[15] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[22] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[23] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[24] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[25] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[26] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[27] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[28] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[34] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[35] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[36] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[37] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[38] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf9fff000 - 0xf9ffffff (0x1000) MX[B]
	[5] -1	0	0xf9bfd700 - 0xf9bfd7ff (0x100) MX[B]
	[6] -1	0	0xf9bfd600 - 0xf9bfd6ff (0x100) MX[B]
	[7] -1	0	0xf9bfd500 - 0xf9bfd5ff (0x100) MX[B]
	[8] -1	0	0xf9bfd400 - 0xf9bfd4ff (0x100) MX[B]
	[9] -1	0	0xf9bfd800 - 0xf9bfdfff (0x800) MX[B]
	[10] -1	0	0xf9bfe000 - 0xf9bfffff (0x2000) MX[B]
	[11] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[12] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[13] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[14] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[15] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[25] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[26] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[27] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[28] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[29] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[30] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[31] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[32] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[33] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[34] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[37] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[38] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[39] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[40] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[41] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1280x800_60 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.50.00.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600M GT at PCI:1:0:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf9fff000 - 0xf9ffffff (0x1000) MX[B]
	[8] -1	0	0xf9bfd700 - 0xf9bfd7ff (0x100) MX[B]
	[9] -1	0	0xf9bfd600 - 0xf9bfd6ff (0x100) MX[B]
	[10] -1	0	0xf9bfd500 - 0xf9bfd5ff (0x100) MX[B]
	[11] -1	0	0xf9bfd400 - 0xf9bfd4ff (0x100) MX[B]
	[12] -1	0	0xf9bfd800 - 0xf9bfdfff (0x800) MX[B]
	[13] -1	0	0xf9bfe000 - 0xf9bfffff (0x2000) MX[B]
	[14] -1	0	0xfebfbf00 - 0xfebfbfff (0x100) MX[B]
	[15] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
	[16] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[17] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
	[18] -1	0	0xfea00000 - 0xfea1ffff (0x20000) MX[B](B)
	[19] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[20] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[21] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] 0	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[29] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[30] -1	0	0x00006ee0 - 0x00006eef (0x10) IX[B]
	[31] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[B]
	[32] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[B]
	[33] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[B]
	[34] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[B]
	[35] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[B]
	[36] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[37] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[38] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[B]
	[41] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[B]
	[42] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[B]
	[43] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[B]
	[44] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[B]
	[45] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "1280x800_60+0+0"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
Synaptics DeviceOff called
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x800_60+0+0"
(--) NVIDIA(0): No video decoder detected
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by jimmy the saint on 2008-02-12
And here is mine:

```
Feb 12 11:52:55 ThinkU syslogd 1.4.1#21ubuntu3: restart.
Feb 12 11:52:55 ThinkU anacron[5625]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Feb 12 11:52:55 ThinkU postfix/sendmail[6514]: fatal: open /etc/postfix/main.cf: No such file or directory
Feb 12 11:52:55 ThinkU anacron[5625]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 75
Feb 12 11:56:14 ThinkU anacron[5625]: Job `cron.weekly' started
Feb 12 11:56:14 ThinkU anacron[6522]: Updated timestamp for job `cron.weekly' to 2008-02-12
Feb 12 11:56:15 ThinkU syslogd 1.4.1#21ubuntu3: restart.
Feb 12 11:56:15 ThinkU anacron[5625]: Job `cron.weekly' terminated
Feb 12 11:56:15 ThinkU anacron[5625]: Normal exit (2 jobs run)
Feb 12 12:11:53 ThinkU kernel: [ 1567.068000] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Feb 12 12:11:55 ThinkU kernel: [ 1568.668000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Feb 12 12:11:55 ThinkU kernel: [ 1569.168000] ipw3945: Error sending cmd #08 to daemon: time out after 500ms.
Feb 12 12:11:56 ThinkU kernel: [ 1569.668000] ipw3945: Error sending ADD_STA: time out after 500ms.
Feb 12 12:11:56 ThinkU kernel: [ 1570.168000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Feb 12 12:12:00 ThinkU kernel: [ 1573.732000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Feb 12 12:12:16 ThinkU NetworkManager: <info>  eth1: link timed out. 
Feb 12 12:12:16 ThinkU NetworkManager: <info>  SWITCH: found better connection 'eth1/Valhalla' than current connection 'eth1/Valhalla'.  same_ssid=1, have_link=0 
Feb 12 12:12:16 ThinkU NetworkManager: <info>  Will activate connection 'eth1/Valhalla'. 
Feb 12 12:12:16 ThinkU NetworkManager: <info>  Device eth1 activation scheduled... 
Feb 12 12:12:16 ThinkU NetworkManager: <info>  Deactivating device eth1. 
Feb 12 12:12:16 ThinkU dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6094
Feb 12 12:12:16 ThinkU dhclient: killed old client process, removed PID file
Feb 12 12:12:16 ThinkU dhclient: DHCPRELEASE on eth1 to 185.211.4.1 port 67
Feb 12 12:12:16 ThinkU avahi-daemon[5506]: Withdrawing address record for 185.211.4.102 on eth1.
Feb 12 12:12:16 ThinkU avahi-daemon[5506]: Leaving mDNS multicast group on interface eth1.IPv4 with address 185.211.4.102.
Feb 12 12:12:16 ThinkU avahi-daemon[5506]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 12:12:17 ThinkU NetworkManager: <info>  Activation (eth1) started... 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  Activation (eth1/wireless): access point 'Valhalla' is encrypted, and a key exists.  No new key needed. 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Feb 12 12:12:17 ThinkU NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Feb 12 12:12:17 ThinkU avahi-daemon[5506]: Withdrawing address record for fe80::21c:bfff:fe0f:cfb7 on eth1.
Feb 12 12:12:18 ThinkU NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Feb 12 12:12:18 ThinkU NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant5^I' 
Feb 12 12:12:19 ThinkU kernel: [ 1592.636000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was '0' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 56616c68616c6c61' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:12:19 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 12:12:55 ThinkU NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 12:12:55 ThinkU kernel: [ 1629.168000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Feb 12 12:12:56 ThinkU kernel: [ 1629.668000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Feb 12 12:12:57 ThinkU NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 12:13:29 ThinkU last message repeated 16 times
Feb 12 12:14:17 ThinkU last message repeated 24 times
Feb 12 12:14:19 ThinkU NetworkManager: <info>  Activation (eth1/wireless): association took too long (>120s), failing activation. 
Feb 12 12:14:19 ThinkU NetworkManager: <info>  Activation (eth1) failure scheduled... 
Feb 12 12:14:19 ThinkU NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Feb 12 12:14:19 ThinkU NetworkManager: <info>  Activation (eth1) failed for access point (Valhalla) 
Feb 12 12:14:19 ThinkU NetworkManager: <info>  Activation (eth1) failed. 
Feb 12 12:14:19 ThinkU NetworkManager: <info>  Deactivating device eth1. 
Feb 12 12:14:19 ThinkU NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device eth1: Resource temporarily unavailable 
Feb 12 12:14:19 ThinkU NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Resource temporarily unavailable 
Feb 12 12:14:19 ThinkU NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on eth1: Resource temporarily unavailable 
Feb 12 12:14:19 ThinkU NetworkManager: <WARN>  nm_device_802_11_wireless_set_mode(): error setting card eth1 to Infrastructure mode: Resource temporarily unavailable 
Feb 12 12:17:01 ThinkU /USR/SBIN/CRON[6859]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 12 12:17:31 ThinkU NetworkManager: <debug> [1202847451.217720] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Valhalla' 
Feb 12 12:17:31 ThinkU NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Valhalla 
Feb 12 12:17:31 ThinkU NetworkManager: <info>  Deactivating device eth1. 
Feb 12 12:18:59 ThinkU init: tty4 main process (4589) killed by TERM signal
Feb 12 12:18:59 ThinkU init: tty5 main process (4590) killed by TERM signal
Feb 12 12:18:59 ThinkU init: tty2 main process (4592) killed by TERM signal
Feb 12 12:18:59 ThinkU init: tty3 main process (4594) killed by TERM signal
Feb 12 12:18:59 ThinkU init: tty1 main process (4596) killed by TERM signal
Feb 12 12:18:59 ThinkU init: tty6 main process (4597) killed by TERM signal
Feb 12 12:18:59 ThinkU avahi-daemon[5506]: Got SIGTERM, quitting.
Feb 12 12:19:03 ThinkU exiting on signal 15
Feb 12 12:20:11 ThinkU syslogd 1.4.1#21ubuntu3: restart.
Feb 12 12:20:11 ThinkU kernel: Inspecting /boot/System.map-2.6.22-14-generic
Feb 12 12:20:11 ThinkU kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Feb 12 12:20:11 ThinkU kernel: Symbols match kernel version 2.6.22.
Feb 12 12:20:11 ThinkU kernel: No module symbols loaded - kernel modules not enabled. 
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003eeb0000 (usable)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 000000003eeb0000 - 000000003eecc000 (ACPI data)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 000000003eecc000 - 000000003ef00000 (ACPI NVS)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 000000003ef00000 - 000000003f000000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] 110MB HIGHMEM available.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] 896MB LOWMEM available.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] found SMP MP-table at 000f6900
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Entering add_active_range(0, 0, 257712) 0 entries of 256 used
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Zone PFN ranges:
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   DMA             0 ->     4096
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   Normal       4096 ->   229376
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   HighMem    229376 ->   257712
Feb 12 12:20:11 ThinkU kernel: [    0.000000] early_node_map[1] active PFN ranges
Feb 12 12:20:11 ThinkU kernel: [    0.000000]     0:        0 ->   257712
Feb 12 12:20:11 ThinkU kernel: [    0.000000] On node 0 totalpages: 257712
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   DMA zone: 0 pages reserved
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   HighMem zone: 221 pages used for memmap
Feb 12 12:20:11 ThinkU kernel: [    0.000000]   HighMem zone: 28115 pages, LIFO batch:7
Feb 12 12:20:11 ThinkU kernel: [    0.000000] DMI present.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F68D0 checksum 0
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: XSDT 3EEBB79F, 0094 (r1 LENOVO TP-7L        1260  LTP        0)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: FACP 3EEBB900, 00F4 (r3 LENOVO TP-7L        1260 LNVO        1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: DSDT 3EEBBD0C, FEC2 (r1 LENOVO TP-7L        1260 MSFT  3000000)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: FACS 3EEE4000, 0040
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: SSDT 3EEBBAB4, 0258 (r1 LENOVO TP-7L        1260 MSFT  3000000)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: ECDT 3EECBBCE, 0052 (r1 LENOVO TP-7L        1260 LNVO        1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: TCPA 3EECBC20, 0032 (r2 LENOVO TP-7L        1260 LNVO        1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: APIC 3EECBC52, 0068 (r1 LENOVO TP-7L        1260 LNVO        1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: MCFG 3EECBCBA, 003C (r1 LENOVO TP-7L        1260 LNVO        1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: HPET 3EECBCF6, 0038 (r1 LENOVO TP-7L        1260 LNVO        1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: SLIC 3EECBDF0, 0176 (r1 LENOVO TP-7L        1260  LTP        0)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: BOOT 3EECBF66, 0028 (r1 LENOVO TP-7L        1260  LTP        1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: ASF! 3EECBF8E, 0072 (r16 LENOVO TP-7L        1260 PTL         1)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: SSDT 3EEE26D9, 025F (r1 LENOVO TP-7L        1260 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: SSDT 3EEE2938, 00A6 (r1 LENOVO TP-7L        1260 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: SSDT 3EEE29DE, 04F7 (r1 LENOVO TP-7L        1260 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: SSDT 3EEE2ED5, 01D8 (r1 LENOVO TP-7L        1260 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Processor #0 6:15 APIC version 20
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Processor #1 6:15 APIC version 20
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Feb 12 12:20:11 ThinkU kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb 12 12:20:11 ThinkU kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f000000:b1000000)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Built 1 zonelists.  Total pages: 255699
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Kernel command line: root=UUID=dd047503-a20a-4884-9b75-df63f9a8db23 ro quiet splash
Feb 12 12:20:11 ThinkU kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Initializing CPU#0
Feb 12 12:20:11 ThinkU kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb 12 12:20:11 ThinkU kernel: [    0.000000] Detected 1995.186 MHz processor.
Feb 12 12:20:11 ThinkU kernel: [   17.849396] Console: colour VGA+ 80x25
Feb 12 12:20:11 ThinkU kernel: [   17.849758] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 12 12:20:11 ThinkU kernel: [   17.850060] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 12 12:20:11 ThinkU kernel: [   17.871012] Memory: 1010360k/1030848k available (2015k kernel code, 19848k reserved, 916k data, 364k init, 113344k highmem)
Feb 12 12:20:11 ThinkU kernel: [   17.871019] virtual kernel memory layout:
Feb 12 12:20:11 ThinkU kernel: [   17.871020]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Feb 12 12:20:11 ThinkU kernel: [   17.871021]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Feb 12 12:20:11 ThinkU kernel: [   17.871022]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Feb 12 12:20:11 ThinkU kernel: [   17.871023]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Feb 12 12:20:11 ThinkU kernel: [   17.871024]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Feb 12 12:20:11 ThinkU kernel: [   17.871024]       .data : 0xc02f7e66 - 0xc03dce84   ( 916 kB)
Feb 12 12:20:11 ThinkU kernel: [   17.871025]       .text : 0xc0100000 - 0xc02f7e66   (2015 kB)
Feb 12 12:20:11 ThinkU kernel: [   17.871027] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb 12 12:20:11 ThinkU kernel: [   17.871054] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Feb 12 12:20:11 ThinkU kernel: [   17.871181] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb 12 12:20:11 ThinkU kernel: [   17.871185] hpet0: 3 64-bit timers, 14318180 Hz
Feb 12 12:20:11 ThinkU kernel: [   17.952164] Calibrating delay using timer specific routine.. 3995.99 BogoMIPS (lpj=7991990)
Feb 12 12:20:11 ThinkU kernel: [   17.952180] Security Framework v1.0.0 initialized
Feb 12 12:20:11 ThinkU kernel: [   17.952184] SELinux:  Disabled at boot.
Feb 12 12:20:11 ThinkU kernel: [   17.952193] Mount-cache hash table entries: 512
Feb 12 12:20:11 ThinkU kernel: [   17.952280] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Feb 12 12:20:11 ThinkU kernel: [   17.952286] monitor/mwait feature present.
Feb 12 12:20:11 ThinkU kernel: [   17.952288] using mwait in idle threads.
Feb 12 12:20:11 ThinkU kernel: [   17.952291] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 12 12:20:11 ThinkU kernel: [   17.952293] CPU: L2 cache: 4096K
Feb 12 12:20:11 ThinkU kernel: [   17.952295] CPU: Physical Processor ID: 0
Feb 12 12:20:11 ThinkU kernel: [   17.952296] CPU: Processor Core ID: 0
Feb 12 12:20:11 ThinkU kernel: [   17.952298] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Feb 12 12:20:11 ThinkU kernel: [   17.952304] Compat vDSO mapped to ffffe000.
Feb 12 12:20:11 ThinkU kernel: [   17.952313] Checking 'hlt' instruction... OK.
Feb 12 12:20:11 ThinkU kernel: [   17.968230] SMP alternatives: switching to UP code
Feb 12 12:20:11 ThinkU kernel: [   17.968536] Early unpacking initramfs... done
Feb 12 12:20:11 ThinkU kernel: [   18.219756] ACPI: Core revision 20070126
Feb 12 12:20:11 ThinkU kernel: [   18.219816] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Feb 12 12:20:11 ThinkU kernel: [   18.248816] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Feb 12 12:20:11 ThinkU kernel: [   18.248829] SMP alternatives: switching to SMP code
Feb 12 12:20:11 ThinkU kernel: [   18.248898] Booting processor 1/1 eip 3000
Feb 12 12:20:11 ThinkU kernel: [   18.259884] Initializing CPU#1
Feb 12 12:20:11 ThinkU kernel: [   18.336552] Calibrating delay using timer specific routine.. 3989.99 BogoMIPS (lpj=7979998)
Feb 12 12:20:11 ThinkU kernel: [   18.336557] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Feb 12 12:20:11 ThinkU kernel: [   18.336561] monitor/mwait feature present.
Feb 12 12:20:11 ThinkU kernel: [   18.336564] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 12 12:20:11 ThinkU kernel: [   18.336565] CPU: L2 cache: 4096K
Feb 12 12:20:11 ThinkU kernel: [   18.336567] CPU: Physical Processor ID: 0
Feb 12 12:20:11 ThinkU kernel: [   18.336569] CPU: Processor Core ID: 1
Feb 12 12:20:11 ThinkU kernel: [   18.336570] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Feb 12 12:20:11 ThinkU kernel: [   18.336675] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Feb 12 12:20:11 ThinkU kernel: [   18.336700] Total of 2 processors activated (7985.99 BogoMIPS).
Feb 12 12:20:11 ThinkU kernel: [   18.336880] ENABLING IO-APIC IRQs
Feb 12 12:20:11 ThinkU kernel: [   18.337092] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 12 12:20:11 ThinkU kernel: [   18.483948] checking TSC synchronization [CPU#0 -> CPU#1]:
Feb 12 12:20:11 ThinkU kernel: [   18.503944] Measured 1213920 cycles TSC warp between CPUs, turning off TSC clock.
Feb 12 12:20:11 ThinkU kernel: [    0.484000] Marking TSC unstable due to: check_tsc_sync_source failed.
Feb 12 12:20:11 ThinkU kernel: [    0.488000] Brought up 2 CPUs
Feb 12 12:20:11 ThinkU kernel: [    0.984000] migration_cost=4000
Feb 12 12:20:11 ThinkU kernel: [    0.984000] Booting paravirtualized kernel on bare hardware
Feb 12 12:20:11 ThinkU kernel: [    0.984000] Time: 12:19:52  Date: 01/12/108
Feb 12 12:20:11 ThinkU kernel: [    0.984000] NET: Registered protocol family 16
Feb 12 12:20:11 ThinkU kernel: [    0.984000] EISA bus registered
Feb 12 12:20:11 ThinkU kernel: [    0.984000] ACPI: bus type pci registered
Feb 12 12:20:11 ThinkU kernel: [    0.984000] PCI: PCI BIOS revision 3.00 entry at 0xfdda7, last bus=24
Feb 12 12:20:11 ThinkU kernel: [    0.984000] PCI: Using configuration type 1
Feb 12 12:20:11 ThinkU kernel: [    0.984000] Setting up standard PCI resources
Feb 12 12:20:11 ThinkU kernel: [    0.988000] ACPI: EC: Found ECDT
Feb 12 12:20:11 ThinkU kernel: [    0.992000] ACPI: System BIOS is requesting _OSI(Linux)
Feb 12 12:20:11 ThinkU kernel: [    0.992000] ACPI: Please test with "acpi_osi=!Linux"
Feb 12 12:20:11 ThinkU kernel: [    0.992000] Please send dmidecode to linux-acpi@vger.kernel.org
Feb 12 12:20:11 ThinkU kernel: [    1.000000] ACPI: Interpreter enabled
Feb 12 12:20:11 ThinkU kernel: [    1.000000] ACPI: (supports S0 S3 S4 S5)
Feb 12 12:20:11 ThinkU kernel: [    1.000000] ACPI: Using IOAPIC for interrupt routing
Feb 12 12:20:11 ThinkU kernel: [    1.008000] ACPI: EC: GPE=0x12, ports=0x66, 0x62
Feb 12 12:20:11 ThinkU kernel: [    1.008000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 12 12:20:11 ThinkU kernel: [    1.008000] PCI: Probing PCI hardware (bus 00)
Feb 12 12:20:11 ThinkU kernel: [    1.012000] PCI: Transparent bridge - 0000:00:1e.0
Feb 12 12:20:11 ThinkU kernel: [    1.012000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.012000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.012000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.012000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.012000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.016000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.016000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.016000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Feb 12 12:20:11 ThinkU kernel: [    1.016000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: Power Resource [PUBS] (on)
Feb 12 12:20:11 ThinkU kernel: [    1.020000] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 12 12:20:11 ThinkU kernel: [    1.020000] pnp: PnP ACPI init
Feb 12 12:20:11 ThinkU kernel: [    1.020000] ACPI: bus type pnp registered
Feb 12 12:20:11 ThinkU kernel: [    1.024000] pnp: PnP ACPI: found 10 devices
Feb 12 12:20:11 ThinkU kernel: [    1.024000] ACPI: ACPI bus type pnp unregistered
Feb 12 12:20:11 ThinkU kernel: [    1.024000] PnPBIOS: Disabled by ACPI PNP
Feb 12 12:20:11 ThinkU kernel: [    1.024000] PCI: Using ACPI for IRQ routing
Feb 12 12:20:11 ThinkU kernel: [    1.024000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Feb 12 12:20:11 ThinkU kernel: [    1.184000] NET: Registered protocol family 8
Feb 12 12:20:11 ThinkU kernel: [    1.184000] NET: Registered protocol family 20
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.184000] pnp: 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
Feb 12 12:20:11 ThinkU kernel: [    1.188000] Time: hpet clocksource has been installed.
Feb 12 12:20:11 ThinkU kernel: [    1.188000] Switched to high resolution mode on CPU 0
Feb 12 12:20:11 ThinkU kernel: [    1.188000] Switched to high resolution mode on CPU 1
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bridge: 0000:00:01.0
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 2000-2fff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: d4000000-d6ffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: e0000000-efffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bridge: 0000:00:1c.0
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 3000-3fff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: fc000000-fdffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: f8000000-f80fffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bridge: 0000:00:1c.1
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 4000-4fff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: dc100000-df2fffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: dfd00000-dfdfffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bridge: 0000:00:1c.2
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 5000-5fff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: d8000000-d9ffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: dfa00000-dfafffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bridge: 0000:00:1c.3
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 6000-6fff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: d0000000-d1ffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: df700000-df7fffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bridge: 0000:00:1c.4
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 7000-7fff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: cc000000-cdffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: df400000-df4fffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bus 22, cardbus bridge: 0000:15:00.0
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 00008000-000080ff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 00008400-000084ff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: f4000000-f7ffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: 40000000-43ffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Bridge: 0000:00:1e.0
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   IO window: 8000-bfff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   MEM window: f8100000-fbffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000]   PREFETCH window: f4000000-f7ffffff
Feb 12 12:20:11 ThinkU kernel: [    1.212000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.212000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.212000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 18
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.212000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 19
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.212000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 20
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.212000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 20 (level, low) -> IRQ 17
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
Feb 12 12:20:11 ThinkU kernel: [    1.212000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.212000] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 12 12:20:11 ThinkU kernel: [    1.216000] PCI: Setting latency timer of device 0000:15:00.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.216000] NET: Registered protocol family 2
Feb 12 12:20:11 ThinkU kernel: [    1.256000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 12 12:20:11 ThinkU kernel: [    1.256000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Feb 12 12:20:11 ThinkU kernel: [    1.256000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 12 12:20:11 ThinkU kernel: [    1.256000] TCP: Hash tables configured (established 131072 bind 65536)
Feb 12 12:20:11 ThinkU kernel: [    1.256000] TCP reno registered
Feb 12 12:20:11 ThinkU kernel: [    1.272000] checking if image is initramfs... it is
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Freeing initrd memory: 7069k freed
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Simple Boot Flag at 0x35 set to 0x1
Feb 12 12:20:11 ThinkU kernel: [    1.816000] audit: initializing netlink socket (disabled)
Feb 12 12:20:11 ThinkU kernel: [    1.816000] audit(1202818792.688:1): initialized
Feb 12 12:20:11 ThinkU kernel: [    1.816000] highmem bounce pool size: 64 pages
Feb 12 12:20:11 ThinkU kernel: [    1.816000] VFS: Disk quotas dquot_6.5.1
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 12 12:20:11 ThinkU kernel: [    1.816000] io scheduler noop registered
Feb 12 12:20:11 ThinkU kernel: [    1.816000] io scheduler anticipatory registered
Feb 12 12:20:11 ThinkU kernel: [    1.816000] io scheduler deadline registered
Feb 12 12:20:11 ThinkU kernel: [    1.816000] io scheduler cfq registered (default)
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Boot video device is 0000:01:00.0
Feb 12 12:20:11 ThinkU kernel: [    1.816000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.816000] assign_interrupt_mode Found MSI capability
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Allocate Port Service[0000:00:01.0:pcie00]
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Allocate Port Service[0000:00:01.0:pcie02]
Feb 12 12:20:11 ThinkU kernel: [    1.816000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.816000] assign_interrupt_mode Found MSI capability
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Allocate Port Service[0000:00:1c.0:pcie00]
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Allocate Port Service[0000:00:1c.0:pcie02]
Feb 12 12:20:11 ThinkU kernel: [    1.816000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.816000] assign_interrupt_mode Found MSI capability
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Allocate Port Service[0000:00:1c.1:pcie00]
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Allocate Port Service[0000:00:1c.1:pcie02]
Feb 12 12:20:11 ThinkU kernel: [    1.816000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.816000] assign_interrupt_mode Found MSI capability
Feb 12 12:20:11 ThinkU kernel: [    1.816000] Allocate Port Service[0000:00:1c.2:pcie00]
Feb 12 12:20:11 ThinkU kernel: [    1.820000] Allocate Port Service[0000:00:1c.2:pcie02]
Feb 12 12:20:11 ThinkU kernel: [    1.820000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.820000] assign_interrupt_mode Found MSI capability
Feb 12 12:20:11 ThinkU kernel: [    1.820000] Allocate Port Service[0000:00:1c.3:pcie00]
Feb 12 12:20:11 ThinkU kernel: [    1.820000] Allocate Port Service[0000:00:1c.3:pcie02]
Feb 12 12:20:11 ThinkU kernel: [    1.820000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Feb 12 12:20:11 ThinkU kernel: [    1.820000] assign_interrupt_mode Found MSI capability
Feb 12 12:20:11 ThinkU kernel: [    1.820000] Allocate Port Service[0000:00:1c.4:pcie00]
Feb 12 12:20:11 ThinkU kernel: [    1.820000] Allocate Port Service[0000:00:1c.4:pcie02]
Feb 12 12:20:11 ThinkU kernel: [    1.820000] isapnp: Scanning for PnP cards...
Feb 12 12:20:11 ThinkU kernel: [    2.176000] isapnp: No Plug & Play device found
Feb 12 12:20:11 ThinkU kernel: [    2.196000] Real Time Clock Driver v1.12ac
Feb 12 12:20:11 ThinkU kernel: [    2.196000] hpet_resources: 0xfed00000 is busy
Feb 12 12:20:11 ThinkU kernel: [    2.196000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Feb 12 12:20:11 ThinkU kernel: [    2.196000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb 12 12:20:11 ThinkU kernel: [    2.196000] input: Macintosh mouse button emulation as /class/input/input0
Feb 12 12:20:11 ThinkU kernel: [    2.196000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Feb 12 12:20:11 ThinkU kernel: [    2.204000] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 12 12:20:11 ThinkU kernel: [    2.204000] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 12 12:20:11 ThinkU kernel: [    2.204000] mice: PS/2 mouse device common for all mice
Feb 12 12:20:11 ThinkU kernel: [    2.204000] EISA: Probing bus 0 at eisa.0
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 1
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 2
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 3
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 4
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 5
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 6
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 7
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Cannot allocate resource for EISA slot 8
Feb 12 12:20:11 ThinkU kernel: [    2.204000] EISA: Detected 0 cards.
Feb 12 12:20:11 ThinkU kernel: [    2.204000] TCP cubic registered
Feb 12 12:20:11 ThinkU kernel: [    2.204000] NET: Registered protocol family 1
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Using IPI No-Shortcut mode
Feb 12 12:20:11 ThinkU kernel: [    2.204000]   Magic number: 12:418:329
Feb 12 12:20:11 ThinkU kernel: [    2.204000]   hash matches device tty50
Feb 12 12:20:11 ThinkU kernel: [    2.204000] Freeing unused kernel memory: 364k freed
Feb 12 12:20:11 ThinkU kernel: [    2.212000] input: AT Translated Set 2 keyboard as /class/input/input1
Feb 12 12:20:11 ThinkU kernel: [    3.376000] AppArmor: AppArmor initialized<5>audit(1202818794.188:2):  type=1505 info="AppArmor initialized" pid=1253
Feb 12 12:20:11 ThinkU kernel: [    3.380000] fuse init (API version 7.8)
Feb 12 12:20:11 ThinkU kernel: [    3.384000] Failure registering capabilities with primary security module.
Feb 12 12:20:11 ThinkU kernel: [    3.408000] ACPI: SSDT 3EEE1B32, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    3.408000] ACPI: SSDT 3EEE1E7B, 085E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    3.412000] Monitor-Mwait will be used to enter C-1 state
Feb 12 12:20:11 ThinkU kernel: [    3.412000] Monitor-Mwait will be used to enter C-2 state
Feb 12 12:20:11 ThinkU kernel: [    3.412000] Monitor-Mwait will be used to enter C-3 state
Feb 12 12:20:11 ThinkU kernel: [    3.412000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb 12 12:20:11 ThinkU kernel: [    3.412000] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb 12 12:20:11 ThinkU kernel: [    3.412000] ACPI: SSDT 3EEE1A6A, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    3.412000] ACPI: SSDT 3EEE1DF6, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
Feb 12 12:20:11 ThinkU kernel: [    3.412000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Feb 12 12:20:11 ThinkU kernel: [    3.412000] ACPI: Processor [CPU1] (supports 8 throttling states)
Feb 12 12:20:11 ThinkU kernel: [    3.412000] ACPI: Thermal Zone [THM0] (56 C)
Feb 12 12:20:11 ThinkU kernel: [    3.416000] ACPI: Thermal Zone [THM1] (54 C)
Feb 12 12:20:11 ThinkU kernel: [    3.764000] usbcore: registered new interface driver usbfs
Feb 12 12:20:11 ThinkU kernel: [    3.764000] usbcore: registered new interface driver hub
Feb 12 12:20:11 ThinkU kernel: [    3.764000] usbcore: registered new device driver usb
Feb 12 12:20:11 ThinkU kernel: [    3.764000] USB Universal Host Controller Interface driver v3.0
Feb 12 12:20:11 ThinkU kernel: [    3.764000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 17
Feb 12 12:20:11 ThinkU kernel: [    3.764000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    3.764000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Feb 12 12:20:11 ThinkU kernel: [    3.764000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Feb 12 12:20:11 ThinkU kernel: [    3.764000] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001860
Feb 12 12:20:11 ThinkU kernel: [    3.764000] usb usb1: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    3.764000] hub 1-0:1.0: USB hub found
Feb 12 12:20:11 ThinkU kernel: [    3.764000] hub 1-0:1.0: 2 ports detected
Feb 12 12:20:11 ThinkU kernel: [    3.844000] SCSI subsystem initialized
Feb 12 12:20:11 ThinkU kernel: [    3.848000] libata version 2.21 loaded.
Feb 12 12:20:11 ThinkU kernel: [    3.864000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
Feb 12 12:20:11 ThinkU kernel: [    3.864000] Copyright (c) 1999-2006 Intel Corporation.
Feb 12 12:20:11 ThinkU kernel: [    3.868000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Feb 12 12:20:11 ThinkU kernel: [    3.868000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Feb 12 12:20:11 ThinkU kernel: [    3.868000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Feb 12 12:20:11 ThinkU kernel: [    3.868000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Feb 12 12:20:11 ThinkU kernel: [    3.868000] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001880
Feb 12 12:20:11 ThinkU kernel: [    3.868000] usb usb2: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    3.868000] hub 2-0:1.0: USB hub found
Feb 12 12:20:11 ThinkU kernel: [    3.868000] hub 2-0:1.0: 2 ports detected
Feb 12 12:20:11 ThinkU kernel: [    3.972000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 12 12:20:11 ThinkU kernel: [    3.972000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    3.972000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb 12 12:20:11 ThinkU kernel: [    3.972000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Feb 12 12:20:11 ThinkU kernel: [    3.972000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
Feb 12 12:20:11 ThinkU kernel: [    3.972000] usb usb3: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    3.972000] hub 3-0:1.0: USB hub found
Feb 12 12:20:11 ThinkU kernel: [    3.972000] hub 3-0:1.0: 2 ports detected
Feb 12 12:20:11 ThinkU kernel: [    4.000000] Clocksource tsc unstable (delta = -101538386 ns)
Feb 12 12:20:11 ThinkU kernel: [    4.076000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
Feb 12 12:20:11 ThinkU kernel: [    4.076000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Feb 12 12:20:11 ThinkU kernel: [    4.076000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 12 12:20:11 ThinkU kernel: [    4.076000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Feb 12 12:20:11 ThinkU kernel: [    4.076000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000018c0
Feb 12 12:20:11 ThinkU kernel: [    4.076000] usb usb4: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    4.076000] hub 4-0:1.0: USB hub found
Feb 12 12:20:11 ThinkU kernel: [    4.076000] hub 4-0:1.0: 2 ports detected
Feb 12 12:20:11 ThinkU kernel: [    4.180000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
Feb 12 12:20:11 ThinkU kernel: [    4.180000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Feb 12 12:20:11 ThinkU kernel: [    4.180000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 12 12:20:11 ThinkU kernel: [    4.180000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Feb 12 12:20:11 ThinkU kernel: [    4.180000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018e0
Feb 12 12:20:11 ThinkU kernel: [    4.180000] usb usb5: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    4.180000] hub 5-0:1.0: USB hub found
Feb 12 12:20:11 ThinkU kernel: [    4.180000] hub 5-0:1.0: 2 ports detected
Feb 12 12:20:11 ThinkU kernel: [    4.284000] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 17
Feb 12 12:20:11 ThinkU kernel: [    4.284000] PCI: Setting latency timer of device 0000:00:19.0 to 64
Feb 12 12:20:11 ThinkU kernel: [    4.312000] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:6b:d2:47:23
Feb 12 12:20:11 ThinkU kernel: [    4.328000] usb 3-2: new low speed USB device using uhci_hcd and address 2
Feb 12 12:20:11 ThinkU kernel: [    4.404000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Feb 12 12:20:11 ThinkU kernel: [    4.404000] ata_piix 0000:00:1f.1: version 2.11
Feb 12 12:20:11 ThinkU kernel: [    4.404000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
Feb 12 12:20:11 ThinkU kernel: [    4.404000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Feb 12 12:20:11 ThinkU kernel: [    4.404000] scsi0 : ata_piix
Feb 12 12:20:11 ThinkU kernel: [    4.404000] scsi1 : ata_piix
Feb 12 12:20:11 ThinkU kernel: [    4.408000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011830 irq 14
Feb 12 12:20:11 ThinkU kernel: [    4.408000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011838 irq 15
Feb 12 12:20:11 ThinkU kernel: [    4.512000] usb 3-2: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    4.520000] usbcore: registered new interface driver hiddev
Feb 12 12:20:11 ThinkU kernel: [    4.532000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
Feb 12 12:20:11 ThinkU kernel: [    4.532000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
Feb 12 12:20:11 ThinkU kernel: [    4.532000] usbcore: registered new interface driver usbhid
Feb 12 12:20:11 ThinkU kernel: [    4.532000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Feb 12 12:20:11 ThinkU kernel: [    4.732000] ata1.00: ATAPI: DVD/CDRW UJDA775, CB03, max UDMA/33
Feb 12 12:20:11 ThinkU kernel: [    4.908000] ata1.00: configured for UDMA/33
Feb 12 12:20:11 ThinkU kernel: [    4.908000] ata2: port disabled. ignoring.
Feb 12 12:20:11 ThinkU kernel: [    4.908000] scsi 0:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA775 CB03 PQ: 0 ANSI: 5
Feb 12 12:20:11 ThinkU kernel: [    4.908000] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
Feb 12 12:20:11 ThinkU kernel: [    4.908000] PCI: Setting latency timer of device 0000:15:00.1 to 64
Feb 12 12:20:11 ThinkU kernel: [    4.912000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
Feb 12 12:20:11 ThinkU kernel: [    4.912000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Feb 12 12:20:11 ThinkU kernel: [    4.912000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Feb 12 12:20:11 ThinkU kernel: [    4.912000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Feb 12 12:20:11 ThinkU kernel: [    4.912000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Feb 12 12:20:11 ThinkU kernel: [    4.912000] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfe226c00
Feb 12 12:20:11 ThinkU kernel: [    4.916000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 12 12:20:11 ThinkU kernel: [    4.916000] usb usb6: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    4.916000] hub 6-0:1.0: USB hub found
Feb 12 12:20:11 ThinkU kernel: [    4.916000] hub 6-0:1.0: 4 ports detected
Feb 12 12:20:11 ThinkU kernel: [    4.960000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Feb 12 12:20:11 ThinkU kernel: [    4.968000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Feb 12 12:20:11 ThinkU kernel: [    4.968000] Uniform CD-ROM driver Revision: 3.20
Feb 12 12:20:11 ThinkU kernel: [    4.968000] sr 0:0:0:0: Attached scsi CD-ROM sr0
Feb 12 12:20:11 ThinkU kernel: [    4.972000] sr 0:0:0:0: Attached scsi generic sg0 type 5
Feb 12 12:20:11 ThinkU kernel: [    5.024000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
Feb 12 12:20:11 ThinkU kernel: [    5.024000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Feb 12 12:20:11 ThinkU kernel: [    5.024000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb 12 12:20:11 ThinkU kernel: [    5.024000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Feb 12 12:20:11 ThinkU kernel: [    5.024000] ehci_hcd 0000:00:1d.7: debug port 1
Feb 12 12:20:11 ThinkU kernel: [    5.024000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Feb 12 12:20:11 ThinkU kernel: [    5.024000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe227000
Feb 12 12:20:11 ThinkU kernel: [    5.028000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 12 12:20:11 ThinkU kernel: [    5.028000] usb usb7: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    5.028000] hub 7-0:1.0: USB hub found
Feb 12 12:20:11 ThinkU kernel: [    5.028000] hub 7-0:1.0: 6 ports detected
Feb 12 12:20:11 ThinkU kernel: [    5.100000] usb 3-2: USB disconnect, address 2
Feb 12 12:20:11 ThinkU kernel: [    5.132000] ahci 0000:00:1f.2: version 2.2
Feb 12 12:20:11 ThinkU kernel: [    5.132000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
Feb 12 12:20:11 ThinkU kernel: [    5.132000] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match
Feb 12 12:20:11 ThinkU kernel: [    5.908000] usb 3-2: new low speed USB device using uhci_hcd and address 3
Feb 12 12:20:11 ThinkU kernel: [    6.088000] usb 3-2: configuration #1 chosen from 1 choice
Feb 12 12:20:11 ThinkU kernel: [    6.104000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
Feb 12 12:20:11 ThinkU kernel: [    6.104000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
Feb 12 12:20:11 ThinkU kernel: [    6.136000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
Feb 12 12:20:11 ThinkU kernel: [    6.136000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
Feb 12 12:20:11 ThinkU kernel: [    6.136000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Feb 12 12:20:11 ThinkU kernel: [    6.136000] scsi2 : ahci
Feb 12 12:20:11 ThinkU kernel: [    6.136000] ata3: SATA max UDMA/133 cmd 0xf8878100 ctl 0x00000000 bmdma 0x00000000 irq 16
Feb 12 12:20:11 ThinkU kernel: [    6.244000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a15ecb2]
Feb 12 12:20:11 ThinkU kernel: [    6.620000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 12 12:20:11 ThinkU kernel: [    6.620000] ata3.00: ATA-7: HITACHI HTS541680J9SA00, SB2IC7UP, max UDMA/100
Feb 12 12:20:11 ThinkU kernel: [    6.620000] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Feb 12 12:20:11 ThinkU kernel: [    6.620000] ata3.00: configured for UDMA/100
Feb 12 12:20:11 ThinkU kernel: [    6.620000] scsi 2:0:0:0: Direct-Access     ATA      HITACHI HTS54168 SB2I PQ: 0 ANSI: 5
Feb 12 12:20:11 ThinkU kernel: [    6.620000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] Write Protect is off
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] Write Protect is off
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 12 12:20:11 ThinkU kernel: [    6.624000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 12 12:20:11 ThinkU kernel: [    6.624000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Feb 12 12:20:11 ThinkU kernel: [    7.044000] sd 2:0:0:0: [sda] Attached SCSI disk
Feb 12 12:20:11 ThinkU kernel: [    7.520000] Attempting manual resume
Feb 12 12:20:11 ThinkU kernel: [    7.520000] swsusp: Resume From Partition 8:6
Feb 12 12:20:11 ThinkU kernel: [    7.520000] PM: Checking swsusp image.
Feb 12 12:20:11 ThinkU kernel: [    7.520000] PM: Resume from disk failed.
Feb 12 12:20:11 ThinkU kernel: [    7.552000] kjournald starting.  Commit interval 5 seconds
Feb 12 12:20:11 ThinkU kernel: [    7.552000] EXT3-fs: mounted filesystem with ordered data mode.
Feb 12 12:20:11 ThinkU kernel: [   15.208000] Linux agpgart interface v0.102 (c) Dave Jones
Feb 12 12:20:11 ThinkU kernel: [   15.264000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 12 12:20:11 ThinkU kernel: [   15.348000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 12 12:20:11 ThinkU kernel: [   15.528000] input: PC Speaker as /class/input/input4
Feb 12 12:20:11 ThinkU kernel: [   15.664000] ieee80211_crypt: registered algorithm 'NULL'
Feb 12 12:20:11 ThinkU kernel: [   15.668000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Feb 12 12:20:11 ThinkU kernel: [   15.668000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Feb 12 12:20:11 ThinkU kernel: [   15.736000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
Feb 12 12:20:11 ThinkU kernel: [   15.744000] sdhci: Secure Digital Host Controller Interface driver
Feb 12 12:20:11 ThinkU kernel: [   15.744000] sdhci: Copyright(c) Pierre Ossman
Feb 12 12:20:11 ThinkU kernel: [   15.868000] Yenta: ISA IRQ mask 0x04b8, PCI irq 16
Feb 12 12:20:11 ThinkU kernel: [   15.868000] Socket status: 30000006
Feb 12 12:20:11 ThinkU kernel: [   15.868000] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
Feb 12 12:20:11 ThinkU kernel: [   15.868000] cs: IO port probe 0x8000-0xbfff: clean.
Feb 12 12:20:11 ThinkU kernel: [   15.868000] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
Feb 12 12:20:11 ThinkU kernel: [   15.868000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
Feb 12 12:20:11 ThinkU kernel: [   15.868000] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
Feb 12 12:20:11 ThinkU kernel: [   15.868000] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
Feb 12 12:20:11 ThinkU kernel: [   15.868000] PCI: Setting latency timer of device 0000:15:00.2 to 64
Feb 12 12:20:11 ThinkU kernel: [   15.868000] mmc0: SDHCI at 0xf8101800 irq 22 DMA
Feb 12 12:20:11 ThinkU kernel: [   16.228000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
Feb 12 12:20:11 ThinkU kernel: [   16.228000] serio: Synaptics pass-through port at isa0060/serio1/input0
Feb 12 12:20:11 ThinkU kernel: [   16.268000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
Feb 12 12:20:11 ThinkU kernel: [   16.376000] nvidia: module license 'NVIDIA' taints kernel.
Feb 12 12:20:11 ThinkU kernel: [   16.624000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
Feb 12 12:20:11 ThinkU kernel: [   16.624000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Feb 12 12:20:11 ThinkU kernel: [   16.624000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
Feb 12 12:20:11 ThinkU kernel: [   16.624000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Feb 12 12:20:11 ThinkU kernel: [   16.624000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Feb 12 12:20:11 ThinkU kernel: [   16.832000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 12 12:20:11 ThinkU kernel: [   16.832000] PCI: Setting latency timer of device 0000:01:00.0 to 64
Feb 12 12:20:11 ThinkU kernel: [   16.832000] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.07  Thu Dec 13 18:42:56 PST 2007
Feb 12 12:20:11 ThinkU kernel: [   16.980000] cs: IO port probe 0x100-0x3af: clean.
Feb 12 12:20:11 ThinkU kernel: [   16.984000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Feb 12 12:20:11 ThinkU kernel: [   16.984000] cs: IO port probe 0x820-0x8ff: clean.
Feb 12 12:20:11 ThinkU kernel: [   16.984000] cs: IO port probe 0xc00-0xcf7: clean.
Feb 12 12:20:11 ThinkU kernel: [   16.984000] cs: IO port probe 0xa00-0xaff: clean.
Feb 12 12:20:11 ThinkU kernel: [   17.036000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
Feb 12 12:20:11 ThinkU kernel: [   17.036000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Feb 12 12:20:11 ThinkU kernel: [   17.564000] lp: driver loaded but no devices found
Feb 12 12:20:11 ThinkU kernel: [   17.656000] Adding 566960k swap on /dev/sda6.  Priority:-1 extents:1 across:566960k
Feb 12 12:20:11 ThinkU kernel: [   18.012000] EXT3 FS on sda5, internal journal
Feb 12 12:20:11 ThinkU kernel: [   18.696000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Feb 12 12:20:11 ThinkU kernel: [   19.132000] ACPI: ACPI Dock Station Driver 
Feb 12 12:20:11 ThinkU kernel: [   19.188000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
Feb 12 12:20:11 ThinkU kernel: [   19.188000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
Feb 12 12:20:11 ThinkU kernel: [   19.188000] ACPI: Error installing bay notify handler
Feb 12 12:20:11 ThinkU kernel: [   19.188000] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
Feb 12 12:20:11 ThinkU kernel: [   19.200000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Feb 12 12:20:11 ThinkU kernel: [   19.200000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Feb 12 12:20:11 ThinkU kernel: [   19.248000] input: Power Button (FF) as /class/input/input6
Feb 12 12:20:11 ThinkU kernel: [   19.248000] ACPI: Power Button (FF) [PWRF]
Feb 12 12:20:11 ThinkU kernel: [   19.264000] input: Lid Switch as /class/input/input7
Feb 12 12:20:11 ThinkU kernel: [   19.264000] ACPI: Lid Switch [LID]
Feb 12 12:20:11 ThinkU kernel: [   19.264000] input: Sleep Button (CM) as /class/input/input8
Feb 12 12:20:11 ThinkU kernel: [   19.264000] ACPI: Sleep Button (CM) [SLPB]
Feb 12 12:20:11 ThinkU kernel: [   19.320000] ACPI: Battery Slot [BAT0] (battery present)
Feb 12 12:20:11 ThinkU kernel: [   19.344000] ACPI: AC Adapter [AC] (on-line)
Feb 12 12:20:11 ThinkU NetworkManager: <info>  starting... 
Feb 12 12:20:11 ThinkU NetworkManager: <WARN>  load_services(): Error loading VPN service file '/etc/NetworkManager/VPN/nm-openvpn-service.name': program does not exist, or is not executable. 
Feb 12 12:20:11 ThinkU NetworkManager: <WARN>  load_services(): Error loading VPN service file '/etc/NetworkManager/VPN/nm-vpnc-service.name': program does not exist, or is not executable. 
Feb 12 12:20:11 ThinkU NetworkManager: <debug> [1202847611.990954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a00'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.138943] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a01'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.139488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10de_429'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.140264] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_1049'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.141461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2834'). 
Feb 12 12:20:12 ThinkU kernel: [   20.596000] ppdev: user-space parallel port driver
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.192314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.193260] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.194285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2835'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.195146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.195544] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.195951] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283a'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.196677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.197055] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.197426] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.197831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283f'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.198579] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2841'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.198947] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_4227'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.199312] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2843'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.199676] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2845'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.200039] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2847'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.200412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2830'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.200784] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.201147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.201523] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.239940] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.240352] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2831'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.240720] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.241118] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.241527] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2832'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.241990] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.242379] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.242777] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2836'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.243186] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.244727] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.245061] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.245391] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_476'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.245719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.246058] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.246425] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.246764] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.247091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.247418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2811'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.247744] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.248071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.248422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host_scsi_device_lun0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.248813] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.249175] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829_scsi_host'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.249564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829_scsi_host_scsi_device_lun0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.250016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283e'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.250399] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bay_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.250777] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_dock_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.251105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.251432] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.251759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.252086] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.252443] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_Synaptics_pass_through'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.252785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.253111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.253436] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.253761] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.254092] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.254427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.254751] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.255076] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.255400] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.255748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.256087] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.256443] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_IBM0057'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.256777] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.257119] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.257458] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.257805] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_if0_logicaldev_input'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.258147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.258471] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.258818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.259143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.259467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.259790] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.260114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1a_6b_d2_47_23'). 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  eth0: Device is fully-supported using driver 'e1000'. 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  Deactivating device eth0. 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.322505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1c_bf_0f_cf_b7'). 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw3945'. 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Feb 12 12:20:12 ThinkU NetworkManager: <info>  Deactivating device eth1. 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.385221] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.385604] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.385931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.386275] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_control__1'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.386620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.386963] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_mixer__1'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.387310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_capture_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.387652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_playback_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.387993] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.388347] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.388646] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.388950] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.389310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.389650] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.389991] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.390332] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.390681] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.391021] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00e_noserial_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.391339] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.391651] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.391991] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.392344] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.392689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_HITACHI_HTS541680J9SA00_SB2241KGDTALLE'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.436662] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_C4CCF2D3CCF2BF2C'). 
Feb 12 12:20:12 ThinkU kernel: [   21.008000] audit(1202847612.253:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5176 profile="/usr/sbin/cupsd"
Feb 12 12:20:12 ThinkU kernel: [   21.056000] apm: BIOS not found.
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.640853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_F22C4C892C4C4AB5'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.840281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_F604A4B704A47BED'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.878606] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part4_size_1024'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.882201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_dd047503_a20a_4884_9b75_df63f9a8db23'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.885929] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_02e87002_348d_48b0_8b49_9cfacc7370c2'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.927653] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.942987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.943381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.943777] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Feb 12 12:20:12 ThinkU NetworkManager: <debug> [1202847612.944453] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD/CDRW_UJDA775'). 
Feb 12 12:20:13 ThinkU kernel: [   21.856000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Feb 12 12:20:13 ThinkU kernel: [   22.088000] input: TPPS/2 IBM TrackPoint as /class/input/input9
Feb 12 12:20:13 ThinkU NetworkManager: <debug> [1202847613.847339] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_OFFICE_SPACE'). 
Feb 12 12:20:13 ThinkU NetworkManager: <debug> [1202847613.847726] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_Synaptics_pass_through_logicaldev_input'). 
Feb 12 12:20:14 ThinkU kernel: [   22.956000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
Feb 12 12:20:14 ThinkU kernel: [   22.956000] thinkpad_acpi: http://ibm-acpi.sf.net/
Feb 12 12:20:14 ThinkU kernel: [   22.956000] thinkpad_acpi: ThinkPad EC firmware 7KHT22WW-1.06
Feb 12 12:20:15 ThinkU kernel: [   24.276000] Failure registering capabilities with primary security module.
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: Successfully dropped root privileges.
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: avahi-daemon 0.6.20 starting up.
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: Successfully called chroot().
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: Successfully dropped remaining capabilities.
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: No service file found in /etc/avahi/services.
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: Network interface enumeration completed.
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: Registering HINFO record with values 'I686'/'LINUX'.
Feb 12 12:20:15 ThinkU avahi-daemon[5540]: Server startup complete. Host name is ThinkU.local. Local service cookie is 245036864.
Feb 12 12:20:15 ThinkU dhcdbd: Started up.
Feb 12 12:20:15 ThinkU hcid[5575]: Bluetooth HCI daemon
Feb 12 12:20:16 ThinkU kernel: [   24.512000] Bluetooth: Core ver 2.11
Feb 12 12:20:16 ThinkU kernel: [   24.512000] NET: Registered protocol family 31
Feb 12 12:20:16 ThinkU kernel: [   24.512000] Bluetooth: HCI device and connection manager initialized
Feb 12 12:20:16 ThinkU kernel: [   24.512000] Bluetooth: HCI socket layer initialized
Feb 12 12:20:16 ThinkU hcid[5575]: Starting SDP server
Feb 12 12:20:16 ThinkU kernel: [   24.544000] Bluetooth: L2CAP ver 2.8
Feb 12 12:20:16 ThinkU kernel: [   24.544000] Bluetooth: L2CAP socket layer initialized
Feb 12 12:20:16 ThinkU hcid[5575]: Created local server at unix:abstract=/var/run/dbus-XlUfM97Mqy,guid=dbb8d37b2412ee6f4d1c260047b1ff80
Feb 12 12:20:16 ThinkU audio[5587]: Bluetooth Audio daemon
Feb 12 12:20:16 ThinkU audio[5587]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Feb 12 12:20:16 ThinkU input[5588]: Bluetooth Input daemon
Feb 12 12:20:16 ThinkU audio[5587]: Unix socket created: 5
Feb 12 12:20:16 ThinkU input[5588]: Registered input manager path:/org/bluez/input
Feb 12 12:20:16 ThinkU kernel: [   24.644000] Bluetooth: RFCOMM socket layer initialized
Feb 12 12:20:16 ThinkU kernel: [   24.644000] Bluetooth: RFCOMM TTY layer initialized
Feb 12 12:20:16 ThinkU kernel: [   24.644000] Bluetooth: RFCOMM ver 1.8
Feb 12 12:20:16 ThinkU audio[5587]: add_service_record: got record id 0x10000
Feb 12 12:20:16 ThinkU audio[5587]: add_service_record: got record id 0x10001
Feb 12 12:20:16 ThinkU audio[5587]: Registered manager path:/org/bluez/audio
Feb 12 12:20:18 ThinkU anacron[5659]: Anacron 2.3 started on 2008-02-12
Feb 12 12:20:18 ThinkU anacron[5659]: Normal exit (0 jobs run)
Feb 12 12:20:18 ThinkU /usr/sbin/cron[5686]: (CRON) INFO (pidfile fd = 3)
Feb 12 12:20:18 ThinkU /usr/sbin/cron[5687]: (CRON) STARTUP (fork ok)
Feb 12 12:20:19 ThinkU /usr/sbin/cron[5687]: (CRON) INFO (Running @reboot jobs)
Feb 12 12:20:40 ThinkU kernel: [   48.508000] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 12 12:20:40 ThinkU kernel: [   48.624000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'OFFICE_SPACE', timestamp 1999/05/21 15:43 (1e20)
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Updating allowed wireless network lists. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Feb 12 12:20:55 ThinkU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Will activate connection 'eth1/Valhalla'. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Device eth1 activation scheduled... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) started... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1/wireless): access point 'Valhalla' is encrypted, but NO valid key exists.  New key needed. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Valhalla'. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Valhalla' received. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Feb 12 12:20:55 ThinkU NetworkManager: <info>  Activation (eth1/wireless): access point 'Valhalla' is encrypted, and a key exists.  No new key needed. 
Feb 12 12:20:56 ThinkU NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Feb 12 12:20:56 ThinkU NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Feb 12 12:20:57 ThinkU kernel: [   65.756000] NET: Registered protocol family 17
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was '0' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 56616c68616c6c61' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  SUP: response was 'OK' 
Feb 12 12:20:57 ThinkU NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Feb 12 12:21:00 ThinkU kernel: [   68.936000] ieee80211_crypt: registered algorithm 'TKIP'
Feb 12 12:21:01 ThinkU NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Valhalla'. 
Feb 12 12:21:01 ThinkU NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb 12 12:21:01 ThinkU NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Feb 12 12:21:02 ThinkU NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Feb 12 12:21:02 ThinkU NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Feb 12 12:21:02 ThinkU NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Feb 12 12:21:03 ThinkU NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Feb 12 12:21:07 ThinkU dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Feb 12 12:21:08 ThinkU dhclient: DHCPOFFER from 185.211.4.1
Feb 12 12:21:08 ThinkU dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Feb 12 12:21:08 ThinkU dhclient: DHCPACK from 185.211.4.1
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Joining mDNS multicast group on interface eth1.IPv4 with address 185.211.4.102.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Registering new address record for 185.211.4.102 on eth1.IPv4.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Withdrawing address record for 185.211.4.102 on eth1.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Leaving mDNS multicast group on interface eth1.IPv4 with address 185.211.4.102.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Joining mDNS multicast group on interface eth1.IPv4 with address 185.211.4.102.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Registering new address record for 185.211.4.102 on eth1.IPv4.
Feb 12 12:21:08 ThinkU NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Feb 12 12:21:08 ThinkU NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 12 12:21:08 ThinkU NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Feb 12 12:21:08 ThinkU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Feb 12 12:21:08 ThinkU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Feb 12 12:21:08 ThinkU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Feb 12 12:21:08 ThinkU NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Feb 12 12:21:08 ThinkU NetworkManager: <info>    address 185.211.4.102 
Feb 12 12:21:08 ThinkU NetworkManager: <info>    netmask 255.255.255.0 
Feb 12 12:21:08 ThinkU NetworkManager: <info>    broadcast 185.211.4.255 
Feb 12 12:21:08 ThinkU NetworkManager: <info>    gateway 185.211.4.1 
Feb 12 12:21:08 ThinkU NetworkManager: <info>    nameserver 192.168.0.1 
Feb 12 12:21:08 ThinkU NetworkManager: <info>    hostname 'ThinkU' 
Feb 12 12:21:08 ThinkU NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 12 12:21:08 ThinkU NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Feb 12 12:21:08 ThinkU NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Feb 12 12:21:08 ThinkU dhclient: bound to 185.211.4.102 -- renewal in 36641 seconds.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Withdrawing address record for 185.211.4.102 on eth1.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Leaving mDNS multicast group on interface eth1.IPv4 with address 185.211.4.102.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Joining mDNS multicast group on interface eth1.IPv4 with address 185.211.4.102.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: New relevant interface eth1.IPv4 for mDNS.
Feb 12 12:21:08 ThinkU avahi-daemon[5540]: Registering new address record for 185.211.4.102 on eth1.IPv4.
Feb 12 12:21:09 ThinkU NetworkManager: <info>  Clearing nscd hosts cache. 
Feb 12 12:21:09 ThinkU NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Feb 12 12:21:09 ThinkU NetworkManager: <info>  Activation (eth1) successful, device activated. 
Feb 12 12:21:09 ThinkU NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Feb 12 12:21:09 ThinkU NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 12 12:21:09 ThinkU kernel: [   77.936000] NET: Registered protocol family 10
Feb 12 12:21:09 ThinkU kernel: [   77.936000] lo: Disabled Privacy Extensions
Feb 12 12:21:09 ThinkU kernel: [   77.936000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 12 12:21:10 ThinkU ntpdate[6165]: adjust time server 91.189.94.4 offset 0.410520 sec
Feb 12 12:21:11 ThinkU avahi-daemon[5540]: Registering new address record for fe80::21c:bfff:fe0f:cfb7 on eth1.*.
Feb 12 12:21:20 ThinkU kernel: [   88.772000] eth1: no IPv6 routers present
```

I don't know what parts are relevant, but I figure if we are having the same problem, seeing both of our logs should help narrow it down!!

---

### Post by peabody on 2008-02-12
I don't know if this has been mentioned yet, but a common culprit for this kind of behavior is often an opengl screensaver.  Might be worth looking into the screensaver control panel and disabling it and see if your system becomes more stable.

---

### Post by jimmy the saint on 2008-02-12
I disabled the screensaver a long time ago because it interfered with the nes emulator I have.

---

### Post by marshall.robert on 2008-02-12
in the screen saver preferences i have "Blank Screen" selected

---

### Post by jimmy the saint on 2008-02-12
bump

---

### Post by jimmy the saint on 2008-02-12
Is there nobody out there today that can help us out with this?  This is a constant problem that has plauged me since fiesty, so it is nothing new or unique.  Others must have had this issue, but apperantly neither of us could find a solution!!

---

### Post by peabody on 2008-02-13
> **jimmy the saint said:**
> Is there nobody out there today that can help us out with this?  This is a constant problem that has plauged me since** fiesty**, so it is nothing new or unique.  Others must have had this issue, but apperantly neither of us could find a solution!!

That may contain the causal link we're looking for.  If you were to say, install dapper LTS and notice that the problem wasn't present, it may have been something that changed in the kernel.  Did you have to use ndiswrapper before feisty or anything of that nature?  Did the video driver you used change between versions?  Did you change hardware at all between versions?

I also found this link related to the laptop of the OP:
[http://ubuntuforums.org/showthread.php?p=3246344](http://ubuntuforums.org/showthread.php?p=3246344)

One of things mentioned in fan control...could be an overheating issue.

---

### Post by marshall.robert on 2008-02-13
in relation to the link, i dont see it as an overheating issue, as it runs cooler in ubuntu than in vista, and that doesnt freeze. the cpu runs at about 40c, and with the dekstop effects on all the time my gpu runs about 50c, also the fan seems to be always on a mid speed, so its not full speed (like in vista) and not no speed (like in xp when im not gaming). that said it can get a bit warm if left on the sofa, or bed...

but i can see how heat would make the wireless break ro the point the killswitch doesnt work...

also, i had a previous install of gutsy on this very same laptop (which i really really broke) and i never whitnessed this before...

---

### Post by NIT006.5 on 2008-02-13
Perhaps completely unrelated, but I did have similar issues that I eventually discovered were being caused by the Crux theme I was using. I changed themes and haven't had a single freeze since.

---

### Post by marshall.robert on 2008-02-13
im using default theme, but ill give that a try...

---

### Post by jimmy the saint on 2008-02-13
Yeah, Ive had this problem on a dell 600m with an ati card under feisty and gutsy as well as on my thinkpad with Nvidia and gutsy.  I have no idea about ndwrapper, but as far as the theme, I used crux for a while, but it interfered with openoffice and its gnome integration package.  
    Its funny because I just left this laptop alone for two hours and it is still going just fine, but other times I will leave it for five minutes and it becomes unusable.  
    Hopefully a guru will swing by and check out these log files and something will jump out at them.  Heres hoping!!

---

### Post by nadi on 2008-02-14
I am experiencing exactly the same problem. I noticed that after every crash I get the same error message in /var/log/debug, with the exact time before the crash: 

Feb 15 05:15:16 nadi-laptop NetworkManager: <debug> [1203048916.666671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 

repeated over and over again during the same second (16th here). its looks like networkmanager to me, but disabling the nm-applet did not help, the hang presisted. It happens sporadically, so I cannot pinpoint why exactly. 

test: disable Networkmanager (killall NetworkManager) , and see if the problem repeats itself or not (note that you will not have network from networkmanager, you can use other means)

It did not happend before, it seems like after the last kernel apgrade I did.

Nadi

---

### Post by nadi on 2008-02-15
I removed networkManager and installed Wicd. zero problem until now, I al already working several hours. 
And you know what? Wicd, with its small python script for the applet, actually does what it is told to!! this is new to me, since Network Manager had its own ghost, ignoring my requrests completely.... :-)
Good luck
EDIT:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) is the link to Wicd instructions. VERY simple.

---

### Post by marshall.robert on 2008-02-16
Its not the theme for me, it crashed while i was using it this time...

edit: i also seem to have lost a bit of configuration data for firefox and all of specto's...

---

### Post by jimmy the saint on 2008-02-16
Just did it again to me.  I don't know if this helps isolate just where the issue lies, but I played around a bit with the crippled session and this is what I noticed.

1.  I can open nautilus if I double click a folder, but not through the panel's  "places" 
2.  If I try to open a terminal, or gedit from the terminal I had open, the taskbar says "opening [program name]" but that soon goes away.
3.  It seems to be deeper than gnome, because the system will not shutdown properly, even though ctl-alt-bkspc exits gnome.

It is most frustrating not even being able to compile enough data to submit a valid bug report!!

---

### Post by jimmy the saint on 2008-02-16
Marshall.Robert, I just thought of something!  Do you have a networked hp printer?  I ask because that was the source of many of my issues back in my xp days.  I was just going through my user.log and noticed an entry regarding a refused connection.  Wouldn't be the first time this particular product caused unexpected issues.  Just a thought.  Grasping at straws here!

---

### Post by stella2657 on 2008-02-17
hi, i had major problems with my own system with  lockups and crashes with compiz, also the hibernate/suspend, disabled both and have been crash free for 4 months.
try disabling all the bells and whistles, and adding them back one at a time.

---

### Post by soulskater on 2008-02-17
Hi.

I would try to upgrade the driver for the graphics card, since that can be a player when it comes to system hangs, it was on mine.

I used the software called envy and picked a different driver than the one on the system, the system worked much better.

You can find envy via following link:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then run it, choose to Install driver Manually in case you have a nVidia card, since the latest driver(169.09) has a Open GL bug that makes games not working at all, but if you do not game do take the latest and test with that, if gaming try the 96.xx.xx driver.

On ATI cards I really don't know if there are any know bugs in their versions.


Hope this helps some of you.

/soulskater

---

### Post by marshall.robert on 2008-02-17
> **jimmy the saint said:**
> Marshall.Robert, I just thought of something!  Do you have a networked hp printer?  I ask because that was the source of many of my issues back in my xp days.  I was just going through my user.log and noticed an entry regarding a refused connection.  Wouldn't be the first time this particular product caused unexpected issues.  Just a thought.  Grasping at straws here!

I do have an hp printer, but not networked, and the pc its attached to is hardly ever on, and the printer is on even less. so i cant be that, plus it happened the most recent time when i wasnt even home...


as for the stuff with envy, ill give that a shot as long as i know its safe, and if the driver that it installs breaks, i can revert to the one in the repositories.

---

### Post by DavidTangye on 2008-02-17
> **jimmy the saint said:**
> And here is mine:

```
Feb 12 11:52:55 ThinkU syslogd 1.4.1#21ubuntu3: restart.
Feb 12 11:52:55 ThinkU anacron[5625]: Job `cron.daily' terminated (exit status: 1) (mailing output)
...
```I don't know what parts are relevant, but I figure if we are having the same problem, seeing both of our logs should help narrow it down!!

Do you still have the problem? If so, I would do the following:[LIST=1]
[*]Reinstall a _***standard***_ Ubuntu. Add/install nothing, configure nothing except minimal preferences in a few apps as absolutely necessary. Don't set up the 3D compiz stuff or anything else. Especially; don't go near the Appearance tool (leave the screensaver as is: off)
[*]Note the exact time, reboot, and log in. Do nothing in the session at all.
[*]Wait. Do nothing for an hour. Take a walk.[/LIST][LIST]
[*]If the machine is dead on your return, then post the logs here, clipped from the noted point of reboot, so you don't need to wade through irrelevant stuff.
[*]Consider installing, in turn, Xubuntu, Ubuntu mini with the icewm window manager, then either the Linux RescueCD distro, Puppy or Knoppix, in step 1 above. Follow the steps again exactly for each.
[*]Conversely, if the machine is OK, configure a little at a time, record what you configured, and wait a day or two after each to ensure the system is stable before changing more. In the meantime, just run simple or core user apps, eg firefox, nautilus, text editor, word processor, movie player.[/LIST]I would be very surprised if all these crash. If fact, with standard installations as per above, you might find they all work. Its all a question of slowing right down with your config changes, so that you can identify which change is leading to the crash. Your other info: > this issue has been present on two different laptops, a Dell and a Thinkpad, and under both Fiesty and Gutsy. I am tired of having to perform hard reboots on my laptops several times a dayindicates to me that you are consistently setting up a combination that does not work.

If all distros above crash when installed carefully as above, then your hardware is problematic: either with the relevant linux kernels (a failing with linux), else you have defective hardware.

---

### Post by jimmy the saint on 2008-02-18
I feel foolish.  I forgot to mention the most important part about the last crash!!  I was using the laptop when it happened.  I had not left it alone for even a minute.  I noticed when I went to open a file in gedit.

---

### Post by soulskater on 2008-02-18
Hi, you should be able to use the standard repository version, saw that the version i have as standard the  100.xx  so by using the 96.xx version you do a downgrade, but should be tried anyhow if problem persists, but as i said before try the latest one if you do not game on your computer.

/soulskater

---

### Post by DavidTangye on 2008-02-18
AS well as my previous post, in the light of what you now mention, I also recommend that you try to see if you problem in to do with foreground gui (X-related) or background stuff, eg kernel and other drivers.

Eg, start it, then switch to a text console, CtlAltF1 to F6 usually, and verify that text apps, like vi run OK for a while.

The closest I have had to what might be your problem, is with my 6 year old Toshiba laptop. I could netboot it into the Ubuntu live desktop system only by adding something like gui=safe-mode as a parameter to the kernel. I guess this is the same as selecting '**Start Ubuntu in safe graphics mode**' from the CD boot screen. If I did not do this, the PC would lock up after a short while into my session. This indicated that the issue was in the way Ubuntu was trying to drive my graphics system. I fixed the problem by booting it into Puppy linux, which worked fine, and drove the graphics fine. Then I copied over to Ubuntu the /etc/X11/xorg.conf that Puppy had generated, and after a few tests and hacks to fine tune this, I had the laptop working efficiently.

---

### Post by jimmy the saint on 2008-02-19
I will look into the graphics situation for sure.  I am pretty sure I have narrowed it down to something to do with the netowork mangager though.  It seems that the first obvious symptom is always the networking.

---

### Post by soulskater on 2008-02-19
Sure, I have trouble with my network on my work laptop to especially when trying to run my computer off line, it's  like  someone put fudge in the lines, slow, very slow.

Try these tips and come back with your findings, sure more people would like to know if and what made your computer work better.

---

### Post by jimmy the saint on 2008-02-19
So I just replaced Network Manager with WICD.  I read in a few places that it solved a whole host of issues.  I figure, as long as I'm looking for solutions, this seems like an easy place to start.  If I am crash free for the next few days, I will let you all know!  Fingers crossed everyone!

---

### Post by jimmy the saint on 2008-02-19
Success!!!  I left the laptop on all night and when I woke up, the internet connection was lost.  The difference is that this time, everything still works, and I could reestablish the connection becasue... everything still works.   I will post a link to a good guide to put WCID into gutsy later.

---

### Post by DavidTangye on 2008-02-19
Well I am surprised, but pleased for you that you are making progress. Its interesting to know that network rather than graphics is your problem. I wonder if the common problem for many issues lies in the way the kernel or library modules/drivers are relating or not to the motherboard chip(s) that provide the graphic and network services. It sounds like you are changing software that controls the drivers for the hardware. Perhaps they alter the way the drivers work. Hmm, dunno where that thought leads me though. :confused:

---

### Post by jimmy the saint on 2008-02-21
Here is a link to the guide I followed to install WCID.  I haven't had a lock up in days now, so I really think this is the solution.  I am going to do some research and try to find out why network manager would be causing this problem.  I would imagine that since Mr Robert has an hp and I have experienced the problem on a Dell and a Lenovo, there are others experiencing similar issues.

[http://wesleybailey.com/blog/2007/11/01/wireless-with-wicd/]("http://wesleybailey.com/blog/2007/11/01/wireless-with-wicd/")

---

### Post by soulskater on 2008-02-22
Glad to hear that it worked for you, have a similar problem on my work laptop, when it has no active network it is extremely slow, will check out the wicd guide and test that.

But for those where this doesn't work i recommend the graphic approach to.

/soulskater :-)

---

### Post by soulskater on 2008-02-22
Feels like a need to revise my last statement about my computer working better with the 169.09 driver, i did a complete hang a little while ago and I forcefully had to use the reset button to make it restart.

Hmm, it looked like it was working better, well I crapped in my own corner anyhow.

/soulskater

---

### Post by jimmy the saint on 2008-02-24
Well my laptop just had the issue again.  I guess WCID didnt solve the problem.  That said, it certainly reduces the frequency of these system hangs!!

---

### Post by soulskater on 2008-02-25
True true, it did on mine to when i intalled the graphics driver via envy.

/soulskater

---

### Post by matthewboh on 2008-02-25
I'm having the same problem but without nVidia, just plain old vanilla graphics.  I've had this problem since Fiesty and I've got Gutsy right now.  I'm running on an o-l-d Toshiba Tecra M1.  There's a huge discussion about a problem like this in the 64-bit forum, but I'm running the 32-bit version - it's here 

[http://ubuntuforums.org/showthread.php?t=587905&highlight=freezes](http://ubuntuforums.org/showthread.php?t=587905&highlight=freezes)

After reading several pages, it seems to be pointing to a problem with xorg.  Any ideas?  I also couldn't find a bug report for the 32-bit version in Launchpad - has anyone put one in?

---

### Post by matherians2 on 2008-02-25
I have a BestBuy special desktop computer, VPR Matrix, that I bought 5 years ago with 1GB of Ram, Pentium 4 processor.  I left it on all night and it didn't crash.  In fact I like Ubuntu better than the OS that came with my computer!  :KS

I am sorry to hear that your computer crashes.  :confused:

---

### Post by jimmy the saint on 2008-02-29
I posted a bug report on launchpad, but so far i have heard nothing.  One problem is that it is a difficult problem to describe.  As a result, there are probably a lot of people that have this problem, and describe it in completely different words, making searching for it harder.

---

### Post by sryth on 2008-02-29
Fair warning...I didn't read the entire 5 page thread.  My impression is that you are having a laptop hang up after leaving it alone for a while.   This quite possibly could be a power management issue.  Do you still have the problem if you disable power management in bios?  (Assuming your bios gives you that option.)  

Otherwise...I do believe that ubuntu hardy that is scheduled for April release has a good bit more support for power management features.

---

### Post by binary00mind on 2008-02-29
Basically I just started my voyage on Ubuntu waters, my first install was in the start of January, I have my up´s and down´s. I have made a super research before my first installation. But I guess not enough...During 6 weeks I did an easy a dozen installations, and I will keep up until I get all things figured out..The only things which works for me is years of years working in Win OS, from the point of understanding the hardware..In the case here and what is mentioned in this thread (I was/am as well, experiencing the same problem(s) )
 I found this thread by search, first in Google then here. The search words <acpi_OSI=Linux>. During all my 2-7 days max. of using Ubuntu after each install, and looking through all little things happening here and there and reading all the logs like a bible.
I Do not have any answers, however during each time when computer is ¨hanging¨ or not responding..The TEMPERATURE of computer or board(core) is going well over 60 C and then hitting the 70 degrees and up. Problem is connected with power managment, hal. BIOS, correct reading of IRQ during the boot time..In some scenarios you may get the wrong reading of temperature and thinking that all is a ok, Wrong !
After each of install Some things works while the others are NOT...So I am on my Trek, to get all toogether 
BTW, I got the temperatures readings from outside of the computer, and the device, that I have used, is german made (reading is in Celsius only), so no mistake here. (it is old, but it works)
So My guess is, to All of You is. That overheating is the reason. Especially that it happens after few hours.... But it is only a guess, from what I did learn so far.

---

### Post by ninja nicco on 2008-03-02
I an experiencing the exact same issue on my Vostro 1500. Almost every time I leave the computer for a while, like when I am copying files from my old windows-box, the network manager suddenly gives me an error message and then I can't open any programs or even reboot. Although one time I actually managed to open the shutdown-menu but when I asked it to reboot something very strange happened. My screen turned black and was split in to. I could type in letters but nothing happened when trying different commands. It is also worth mentioning that as I typed, the letters appeared at both the "split-up blackscreens".

Would be very grateful if anyone came up with a solution to this!

---

### Post by repager on 2008-03-03
I don't know if this adds anything to the discussion but I find that my desktop (unbranded) only hangs with an application open.  If left with only the OS running (7.10 with Compiz fusion) it runs and runs.
Leave it with Firefox, Thunderbird. or OOo and the whole thing hangs.
BUT both Firefox and Thunderbird are unstable during use usually just crashing, so sudden there is nothing significant in 'crash' but sometimes causing a hung system.
This is all really annoying it reminds me so much of the Evil Empire

---

### Post by ninja nicco on 2008-03-05
Hi!
I think I may have found something. Like I said earlier was I able to press the Restart interface after the network-connection was lost but this time the split screen wasn't blank it contained this error-message:

[[IMG]http://img168.imageshack.us/img168/72/rebooterrorsa5.th.jpg[/IMG]](http://img168.imageshack.us/my.php?image=rebooterrorsa5.jpg)

Hope someone can find this useful in helping out.

---

### Post by marshall.robert on 2008-03-06
Wow, this thread has had a fair bit of attention, i havnt been here in a while since i have mainly dealth with windows over the past couple of weeks, but i was using ubuntu today and it did freeze, and it was in a typical scenario for a freeze, left on the sofa, but i do make sure the fan has access to air though, i think its got something to do with the vostro 1500 bios (btw nice to see another vostro 1500 user) not enitiating the fan so it gets a bit hot (doesnt seem to fully initialize until the cpu.gpu gets very hot (60c+)), which im guessing doesnt help.

i have 2 ideas.

1. run the ubuntu install in vmware, see what happens.

2. update the dell bios (yes there is one, but i havn't installed it..)

ill try the vm session tomorrow running in the background while im at college, and check on it now and then, post back what i find. then after that ill update the dell bios and see if that makes a difference.

Edit: i can't successfully run Ubuntu in vmware as it cannot start the graphical enviroment...

---

### Post by ninja nicco on 2008-03-08
I have now find a way to avoid the issue. When I only use wired connection and disables the wireless I can go hang-free forever (at least it hasn't occurred yet), so I think  that at least my problem has something to do with the wireless card not function properly or the Network Manager, rather than overheating or some graphical difficulty.

---

### Post by jimmy the saint on 2008-03-08
I agree 100%.  I am almost positive that this issue lies in the wireless networking.  This would explain why every post I have seen regarding similar problems is related to laptops locking up, rather than desktops; laptops are more likely to use wireless.   The bug I submitted to launchpad has recieved no attention yet, so who knows if that will be addressed.  It is unfortunate that I don't know enough to isolate the issue sufficiently to submit a bug report with enough data to be very usefull.  hopefully a *nix guru stumbles upon this thread and offers a solution!  I am going to upgrade my bios again this afternoon to see if that helps, but the last few updates didn't solve the issue, so who knows.  I'll definitely keep you guys posted.

---

### Post by marshall.robert on 2008-03-09
the bios update did nothing, didnt really expect it to.

also i went out today, and in anticipation i disabled the networking via the nm-applet right click menu, and when i got back everything worked except the wireless, but the difference is that the wireless could scan but not connect, i also tried kismet and it threw some error at me...

so i think the evidence points to networking.

---

### Post by charliehubuntu on 2008-03-13
I'm glad this problem is getting some discussion. I, too, have experienced this on two versions of Ubuntu and on two computers: one a Vaio VGN-170P and one a Dell Vostro 1700, both with Intel 3945. It has been the most long-lived and frustrating problem in my linux experience.

I replaced NM with WICD and had a similar experience to one other poster - the system didn't crash (didn't stop launching programs such as terminal shells, didn't stop responding to shutdown/reboot commands, didn't stop responding to ctrl-alt-F, as it does after a crash using nm). But the wireless connection did crash, only in my case I could not re-connect using wicd. Wicd acted as if there was no wireless function at all - no listing of access points, no responcse to the "connect" command. Bottom line, more stuff works after a crash with wicd, but I still have to reboot.

Has anybody had any success in using ndiswrapper instead of the proprietary intel driver? I think I'll experiment with that.

Here is some interesting stuff from syslog:

```

Mar 13 07:05:04 gemini kernel: [35131.620000] rtc: lost 2 interrupts
Mar 13 07:05:04 gemini kernel: [35131.640000] rtc: lost 2 interrupts
Mar 13 07:05:04 gemini kernel: [35131.892000] rtc: lost 6 interrupts
Mar 13 07:05:04 gemini kernel: [35132.136000] rtc: lost 2 interrupts
Mar 13 07:05:04 gemini kernel: [35132.160000] rtc: lost 2 interrupts
Mar 13 07:05:04 gemini kernel: [35132.188000] rtc: lost 1 interrupts
Mar 13 07:05:04 gemini kernel: [35132.412000] rtc: lost 6 interrupts
Mar 13 07:05:04 gemini kernel: [35132.432000] rtc: lost 6 interrupts
Mar 13 07:05:04 gemini kernel: [35132.452000] rtc: lost 6 interrupts
Mar 13 07:05:05 gemini kernel: [35132.608000] rtc: lost 4 interrupts
Mar 13 07:05:10 gemini kernel: [35137.660000] ipw3945: Error sending cmd #07 to 
daemon: time out after 500ms.
Mar 13 07:05:10 gemini kernel: [35138.160000] ipw3945: Error sending SCAN_ABORT_
CMD: time out after 500ms.
Mar 13 07:05:11 gemini kernel: [35138.660000] ipw3945: Error sending cmd #08 to 
daemon: time out after 500ms.
Mar 13 07:05:11 gemini kernel: [35139.160000] ipw3945: Error sending ADD_STA: ti
me out after 500ms.
Mar 13 07:05:12 gemini kernel: [35139.660000] ipw3945: Error sending SCAN_ABORT_
CMD: time out after 500ms.
Mar 13 07:05:16 gemini kernel: [35143.204000] ipw3945: Error sending LEDS_CMD: t
ime out after 500ms.
Mar 13 07:05:23 gemini kernel: [35150.748000] bridge-eth1: disabling the bridge
Mar 13 07:05:23 gemini dhclient: receive_packet failed on eth1: Network is down
Mar 13 07:05:23 gemini avahi-daemon[6018]: Interface eth1.IPv4 no longer relevan
t for mDNS.

```

---

### Post by marshall.robert on 2008-03-14
Who here has the Intel 3945 wireless chip?

please post if you have and state whether you have been having problems or not.

---

### Post by jimmy the saint on 2008-03-16
Ive got a 3945.  The dell that previously had this problem had an intel card as well, but it was a different one.  

I upgraded the bios last wednesday and havent had another freeze yet.  Maybe lenovo figured out a way to fix it or maybe Ive just been lucky.  When I switched to WICD I went three days without a freeze, then BAM it froze.

---

### Post by charliehubuntu on 2008-03-16
I followed the instructions on this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy]("https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy")
and afterwards wireless didn't work at all. No interface.

So I backed out of the file modifications from that page and re-enabled the 3945 in "Restricted Drivers".

My machine has been up for several days now. Ordinarily it would crash every few hours.

---

### Post by charliehubuntu on 2008-03-18
My system is back to crashing regularly.

Any new insights, successes on this issue?

---

### Post by marshall.robert on 2008-03-20
note: last night i left it on, no crash, but while i used it this morning crashed while i was doing stuff that needed the internet (other note: it has crashed when im not using the internet so im doubtful as to that being the reason)

---

### Post by ninja nicco on 2008-03-22
Have you tried to uninstall the network manager and connect to the wireless network manually? At least I havn't had a problem this far. Been surfing the net for a week now without a crash :)

..and yes I have the Intel 3945 wireless chip.

---

### Post by marshall.robert on 2008-03-22
No, i would if it where a desktop, but being a laptop and there being a couple of wireless networks at college that i have access to i cant keep doing it manually...

ive just installed WICD and i shall see how that turns out...

---

### Post by charliehubuntu on 2008-03-22
For me, the crashing happens with NM or WICD. I haven't tried full manual.

---

### Post by marshall.robert on 2008-03-22
I'll have to wait to report if it crashes or not, but im really impressed that it doesn't use a keyring, now i dont even have to enter my password everytime i boot into Ubuntu...

so for that reason im gonna keep it regardless!

---

### Post by juky on 2008-03-23
Hi everyone;

I had a similar experience as most of you here in this thread. So here goes my issue and a way how I had fixed it.

First of all, note that I am a user of Gutsy and ATI Radeon X700 (PCIE) graphic card with "fglrx" driver.

My problem was that each and every time screen saver was started, my display turned grey, and a PC got frozen (both keypad and a mouse). Only solution was hard reset on a PC case. I noticed such behavior after I enabled visual effects in System-->Preferences-->Appearance-->Visual Effects-->"Extra" (3rd) option. 

After retrieving settings to "Normal" in System-->Preferences-->Appearance-->Visual Effects, I had never had bahavior described above again.

Possible solution would also be turning off screensaver, leaving visual effects set to "Extra".

Can anyone of you can try this possibility / check your visual settings and report an outcome here?

I do not know if this is a kernel or driver issue, if anyone can provide more info, I would appreciate it!

Cheers,
juky

---

### Post by charliehubuntu on 2008-03-23
My screen saver is turned off, and visual effects set to none, and the system still crashes regularly

---

### Post by juky on 2008-03-23
> **charliehletmein said:**
> My screen saver is turned off, and visual effects set to none, and the system still crashes regularly

Regularly, like each 15 mins after boot or?

---

### Post by charliehubuntu on 2008-03-23
Sometimes it'll run for a couple of days. Sometimes crash after a few minutes. Typically can run for an hour or two. Sometimes will crash when I'm doing something. Sometimes it'll crash when I'm away. By "crash" I mean the network connection dies, cannot re-connect, and if I don't reboot strange things will start happening like unable to launch applications followed by unable to ctrl-alt-F to terminals, and unable to shutdown using any software commands (must power down).

---

### Post by juky on 2008-03-24
> **charliehletmein said:**
> Sometimes it'll run for a couple of days. Sometimes crash after a few minutes. Typically can run for an hour or two. Sometimes will crash when I'm doing something. Sometimes it'll crash when I'm away. By "crash" I mean the network connection dies, cannot re-connect, and if I don't reboot strange things will start happening like unable to launch applications followed by unable to ctrl-alt-F to terminals, and unable to shutdown using any software commands (must power down).

Have you tried clean reinstall? If you can try it, do it, but without any additional SW, or so. Just pure OS.

Then, if the crahes continue to happen, I would suspect in HW failure.

Which version are you using, gutsy?

---

### Post by charliehubuntu on 2008-03-24
That is going to be my next step. I have some backup problems to work out before I can try it.

---

### Post by juky on 2008-03-25
Good luck and let us know how did it went.

Cheers
juky

---

### Post by marshall.robert on 2008-03-25
Just to let you know that after instaling WICD it still crashed, but i could use stuff still, and reboot and all that, but i could not even scan for a network, whereas before i could. but there is no point being able to scan without being able to connect.

EDIT: Just a thought but maybe it could be something to do with IPv6 this post [http://ubuntuforums.org/showpost.php?p=4583757&postcount=2](http://ubuntuforums.org/showpost.php?p=4583757&postcount=2) suggests that gutsy doesnt have the 'guts' to work IPv6 properly

Another Note: My desktop (which i use for messing around/testing) currently has the hardy beta install, and it just did the same thing while i was grabbing lots of updates (only 4 left too). i also use wicd on that. but its not an intel chip, but rather a broadcom 4306 chip...

---

### Post by Deb.Early on 2008-04-03
> strange things will start happening like unable to launch applications followed by unable to ctrl-alt-F to terminals, and unable to shutdown using any software commands (must power down).

I've been experiencing the same symptoms on a Thinkpad T60 with the Intel 3945ABG a few times a day for the past week. I don't recall this happening prior to that, and the only thing I've done that may coincide with the start of these things is change my network fileserver drive automount from cifs to smbfs (I've had too many problems with cifs in fstab on desktops).

My installation includes the ATI driver version 8.45 (to get suspend working) for my ATI Mobility Radeon X1300 card. Given the current controversy and hair-pulling over SLAB vs SLUB and fglrx in general, I steer clear of desktop effects and other video fanciness.

I went through all the logs I could find after the last hang and found this in /var/log/samba/log.nmbd:

```
[2008/04/03 12:21:07, 0] libsmb/nmblib.c:send_udp(791)
  Packet send failed to 192.168.23.255(138) ERRNO=Invalid argument
[2008/04/03 12:21:07, 0] libsmb/nmblib.c:send_udp(791)
  Packet send failed to 192.168.23.255(137) [COLOR="Red"]ERRNO=Network is unreachable[/COLOR] 
[2008/04/03 12:21:07, 0] nmbd/nmbd_packets.c:send_netbios_packet(163)
  send_netbios_packet: send_packet() to IP 192.168.23.255 port 137 failed
[2008/04/03 12:21:07, 0] nmbd/nmbd_namequery.c:query_name(245)
  query_name: Failed to send packet trying to query name EPSILON<1d>
[2008/04/03 12:21:07, 0] nmbd/nmbd.c:reload_interfaces(229)
  reload_interfaces: No subnets to listen to. Shutting down...
```

The time corresponds exactly with the hang, and the log resumes after that with startup messages. There are identical errors further up in the log whose times look suspiciously like they coincide with previous hangs, and which are all -- without exception -- followed by shutdown and startup messages.

I've combed the internet and these forums, and it really smells to me like a networking issue -- possibly independent of the wireless packages folks are using (WiCD, network manager, whatever). If packet-handling hiccups for whatever reason, it sure looks like something deep inside isn't handling that gracefully.

I'm pretty much a newbie to Linux, but not to OSes in general (I used to write OS simulators in IBM assembler). Is there a software layer in Ubuntu specific to wireless communication that apps like WiCD and network manager sit "on top" of? Could there be an "ack" or a "handshake" issue of some sort that's propagating all the way up to Gnome?

Sorry if I sound like an idiot here, just thinking out loud...  :redface:

---

### Post by marshall.robert on 2008-04-03
Thats good stuff.

I think we have definitely outlined that this is a network issue, and almost certainly specific to the Intel 3945 wireless chip.

One thing i noticed recently is that it tends to happen strait after a reboot from windows to Ubuntu.

But since i have switched to WICD i have been able to do a software reboot, unlike when i was using nm-applet which caused the whole system to go down with it...

---

### Post by Deb.Early on 2008-04-03
> One thing i noticed recently is that it tends to happen strait after a reboot from windows to Ubuntu

I honestly can't remember when I last booted Windows on this machine. OTOH, at my age that doesn't mean much!  ;-)

I do close the lid and suspend it every night, though, and there's a suspicious-looking bug in launchpad ([https://bugs.launchpad.net/ubuntu/+source/samba/+bug/172541](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/172541)) that may or may not be related.

> almost certainly specific to the Intel 3945 wireless chip

I'm not so sure I agree. There are piles and piles of reports of the same weird crash behavior all over the forums. A lot of those were obviously due to other issues,  but of those that looked like they could be network-related,  they can't all be using the same chip. FWIW, my old tech-support "gut" says it's in the kernel somewhere. Or HAL, maybe.

---

### Post by marshall.robert on 2008-04-11
Anyone have any revelations, more issues to raise, or anything?

---

### Post by arelis on 2008-04-11
I have the same problem. After leaving Ubuntu on for a while, i can't start programs either and the ones running still work fine. When i switch to the console and type the name of a graphical program i get "Segmentation Fault". For more details click on the link in my sig.

---

### Post by Mamsaac on 2008-04-14
Same problem with Intel 3945 wireless.

So... I'm really really really expecting this to die. It really bothers me to have a laptop that crashes every now and then.

I'm using network manager as most people in here, I will try WICD tomorrow. I still wonder how manual configuration works. If anyone knows I will appreciate it.

---

### Post by erginemr on 2008-04-14
> **Mamsaac said:**
> Same problem with Intel 3945 wireless.

So... I'm really really really expecting this to die. It really bothers me to have a laptop that crashes every now and then.

I'm using network manager as most people in here, I will try WICD tomorrow. I still wonder how manual configuration works. If anyone knows I will appreciate it.

Then, please spend some time in this thread:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

And another relevant topic is:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by Kn1vez on 2008-04-14
> **marshall.robert said:**
> Hello.

What I have here is a fresh-ish (~4days) install on a Dell Vostro 1500.

Laptop Hardware:
2.0GHz Intel Core 2 Duo
2GB RAM
nVidia 8600GT
Intel ICH8 82801H Chipset
Intel HDA Audio
Intel PRO/Wireless 3945ABG
160GB HDD


Hey bud I know you are looking for help and this is lame but I need to get 
 the windows drivers fort the vostro 1500 8x dvd writer. do u have the inf / dll files? i hope u do, let me know my email is [email]vtknives@hotmail.com[/email]

---

### Post by Mamsaac on 2008-04-14
> **erginemr said:**
> Then, please spend some time in this thread:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

And another relevant topic is:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Time spent, I hope it is worth it (I wonder if it will prevent this problems...)

Thanks.

---

### Post by marshall.robert on 2008-04-15
> **Kn1vez said:**
> Hey bud I know you are looking for help and this is lame but I need to get 
 the windows drivers fort the vostro 1500 8x dvd writer. do u have the inf / dll files? i hope u do, let me know my email is ***********

you can get the updated ones off the dell website, [http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=VOS_N_1500&os=WLH&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=VOS_N_1500&os=WLH&osl=en&catid=&impid=) that should be it.

---

### Post by marshall.robert on 2008-04-27
i wonder if the problem will still occur now that the new version of ubuntu is out...

---

### Post by szandor on 2008-04-27
> **marshall.robert said:**
> i wonder if the problem will still occur now that the new version of ubuntu is out...

a bug report was answered asking people to verify the error in hardy. also, development has switched from iw3945 to iwlwifi. i think it's time to try iwlwifi.

---

### Post by marshall.robert on 2008-05-02
nope.. still does it for me....

---

### Post by szandor on 2008-05-06
> **marshall.robert said:**
> nope.. still does it for me....

is this with the ipw3945 or iwl3945? i was currently using ipw3945 which i replaced with the iwl3945 module and so far, even though it's only been a couple of days, i haven't had any issues. i'll really have to wait a couple of weeks as the crashing/hanging due to the ipw3945 doesn't happen too often.

---

### Post by marshall.robert on 2008-05-20
how do i tell?

also the problem may not happen again cos i messed everything up and just reinstalled.

---

