---
title: "After running dpkg, disable secure boot, reboot, no networking devices are available"
date: 2017-01-12
forum: General Help
---

### Post by digital-larry on 2017-01-12
I am running 16.04 LTS on my Asus laptop.  It is a dual boot with Windows 10.  Ubuntu has been working fine for months.

Today, I saw a big red dot in the upper right, and clicked on it.  Got a message talking about running the configuration manager to fix some missing packages.

I copied the suggested command to the terminal window and ran it and as far as I can tell, several packages updated.  Then a window appeared with a message about 3rd party drivers and UEFI booting.  It said something like 3rd party drivers could not be installed unless I temporarily disabled secure booting.  It sounded a little fishy so I googled it and found some postings here that led me to believe that it could be a legitimate thing to do.  So I went ahead and did it.  It asked me for the password twice, which I supplied, then it rebooted.

I noticed the following differences upon reboot:

1) After first seeing "Ubuntu" with the 5 dots below (the progress indicator), the screen went blank and then I just saw the 5 dots by themselves, little squares against a black background.
2) After booting, and logging into the desktop, the display seems a bit brighter and possibly my icons on the left hand side are larger than I had set them.
3) Empty trash does not work
4) By far the worst problem is that I no longer have any network devices.  If I run ifconfig I am only shown the local loopback device.  Normally I expect to see both eth0 and wlan0.

Wow, this is really a mess!  At no time during reboot did it ask me for the secure boot password I had supplied earlier, so I think that maybe some/all of my device drivers are turned off.

Any clues as to how I can get my network adapters back in Ubuntu?

---

### Post by digital-larry on 2017-01-13
Wow, lots of traffic here.  All I can say is that I have rebooted probably a dozen times.  I either enable or disable secure boot in the BIOS setup.  It makes no difference to the situation.  However I can still log in and copy/backup my files to another partition on the hard drive.  After that I don't see anything else to do other than reinstall Ubuntu.  Sigh...

---

### Post by geeksmith on 2017-01-13
I have not played with UEFI booting before, so I'm not much help there.

However, it's possible there are still some issues with packages on your system, so you might try some of the steps at the following link before going to a full reinstall:
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by digital-larry on 2017-01-13
That procedure is probably going to be harder than reinstalling, though I appreciate it.  I did manage to run the backup mgr to make a backup of my home directory.  I have no network connections so I can't copy-paste the couple dozen debug commands directly on the laptop.  I also noticed that audio is not working, so it looks like drivers for all HW peripherals other than disk drives are disabled (or something like that).  It seems odd that there is no documentation of this scenario, or at least I haven't found it yet.

---

### Post by oldfred on 2017-01-14
It is correct that UEFI Secure Boot must be off for binary blob kernel drivers can be added. Ubuntu has no control over those blobs, so cannot confirm they are Secure Boot.

What driver(s) did you install?
Is your Asus dual video, and you have wrong video mode?
What video card/chip do you have?

I do not know networking issues, but best to run this script. 
You can boot live installer so you can download & upload data.

Are you just using Wireless, or does wired not work also?
From sticky thread at top of Network & wireless sub-forum
 Before posting in Networking & Wireless 

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by digital-larry on 2017-01-14
What precipitated all of this was a red ball notification saying something was goofed up and I should run the package manager.

Specifically it suggested that I run **sudo dpkg --configure -a**.

I did not keep track of what packages were updated here.  I was NOT trying to do anything other than make the red ball complaint go away.

After that I got a pop up warning dialog talking about Secure Boot and 3rd party drivers.  I know I should have screen capped all of this!  But I didn't.

Summary of post-reboot condition:
1) Video looks a little different than before
2) No networking devices are found with ifconfig.  I used to have eth0 and wlan0.  They are gone.  
3) There are no audio devices

Anyway unless I get some sort of solution by tomorrow morning, I'm prepared to simply reinstall Ubuntu.

Thanks to all who have replied.

---

### Post by digital-larry on 2017-01-14
I created a new Ubuntu 16.04 DVD and booted up in Live mode.  My networking adapters are found and working.  I was able to go find the /var/log/dpkg.log from last Thursday when the disaster occurred.  I have grep'ed this, filtering on the date and the full word "configure" to narrow down the results a bit.  This at least shows what packages were updated when I ran dpkg --configure -a.

Sorry it's still a lot of info.

```
2017-01-12 10:45:34 startup packages configure
2017-01-12 10:45:34 configure gcc-5-arm-linux-gnueabihf-base:amd64 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:45:34 configure libapt-inst2.0:amd64 1.2.18 <none>
2017-01-12 10:45:35 configure deja-dup:amd64 34.2-0ubuntu1.1 <none>
2017-01-12 10:45:35 configure libwbclient0:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:45:35 configure cpp-5-arm-linux-gnueabihf:amd64 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:45:36 configure apt-transport-https:amd64 1.2.18 <none>
2017-01-12 10:45:36 configure samba-libs:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:45:36 configure libpam-systemd:amd64 229-4ubuntu13 <none>
2017-01-12 10:45:41 configure firefox-locale-en:amd64 50.1.0+build2-0ubuntu0.16.04.1 <none>
2017-01-12 10:45:42 configure ifupdown:amd64 0.8.10ubuntu1.2 <none>
2017-01-12 10:45:44 configure samba-vfs-modules:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:46:12 configure isc-dhcp-common:amd64 4.3.3-5ubuntu12.6 <none>
2017-01-12 10:46:13 configure apt-utils:amd64 1.2.18 <none>
2017-01-12 10:46:15 configure libopenshot-audio3:amd64 0.1.2+0+46+105+201612202317~ubuntu16.04.1 <none>
2017-01-12 10:46:19 configure python-samba:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:46:21 configure libavutil-ffmpeg54:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:46:22 configure gcc-5-cross-base:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:46:22 configure samba-common:all 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:46:23 configure libswscale-ffmpeg3:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:46:24 configure libgomp1-armhf-cross:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:46:24 configure libatomic1-armhf-cross:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:46:24 configure libsmbclient:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:46:24 configure isc-dhcp-client:amd64 4.3.3-5ubuntu12.6 <none>
2017-01-12 10:46:25 configure python3-problem-report:all 2.20.1-0ubuntu2.4 <none>
2017-01-12 10:46:26 configure libpostproc-ffmpeg53:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:46:26 configure smbclient:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:46:27 configure udev:amd64 229-4ubuntu13 <none>
2017-01-12 10:46:29 configure grub-common:amd64 2.02~beta2-36ubuntu3.6 <none>
2017-01-12 10:46:32 configure chromium-codecs-ffmpeg-extra:amd64 55.0.2883.87-0ubuntu0.16.04.1263 <none>
2017-01-12 10:46:33 configure firefox:amd64 50.1.0+build2-0ubuntu0.16.04.1 <none>
2017-01-12 10:47:35 configure snap-confine:amd64 2.20.1ubuntu1 <none>
2017-01-12 10:47:36 configure initramfs-tools-bin:amd64 0.122ubuntu8.7 <none>
2017-01-12 10:47:36 configure libgme0:amd64 0.6.0-3ubuntu0.16.04.1 <none>
2017-01-12 10:47:36 configure samba-common-bin:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:47:38 configure samba-dsdb-modules:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:47:38 configure linux-firmware:all 1.157.6 <none>
2017-01-12 10:50:14 configure libswresample-ffmpeg1:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:50:15 configure libavresample-ffmpeg2:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:50:15 configure python3-distupgrade:all 1:16.04.20 <none>
2017-01-12 10:50:15 configure libavcodec-ffmpeg56:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:50:16 configure libavutil-dev:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:50:16 configure libgcc1-armhf-cross:all 1:5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:50:16 configure libstdc++6-armhf-cross:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:50:16 configure grub-efi-amd64-bin:amd64 2.02~beta2-36ubuntu3.6 <none>
2017-01-12 10:50:16 configure initramfs-tools-core:all 0.122ubuntu8.7 <none>
2017-01-12 10:50:17 configure deja-dup-backend-gvfs:all 34.2-0ubuntu1.1 <none>
2017-01-12 10:50:17 configure libasan2-armhf-cross:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:50:17 configure libavformat-ffmpeg56:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:50:17 configure grub2-common:amd64 2.02~beta2-36ubuntu3.6 <none>
2017-01-12 10:50:17 configure initramfs-tools:all 0.122ubuntu8.7 <none>
2017-01-12 10:50:18 configure ubuntu-release-upgrader-core:all 1:16.04.20 <none>
2017-01-12 10:50:18 configure python3-apport:all 2.20.1-0ubuntu2.4 <none>
2017-01-12 10:50:19 configure libswresample-dev:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:50:19 configure apport:all 2.20.1-0ubuntu2.4 <none>
2017-01-12 10:50:21 configure ubuntu-core-launcher:amd64 2.20.1ubuntu1 <none>
2017-01-12 10:50:21 configure samba:amd64 2:4.3.11+dfsg-0ubuntu0.16.04.3 <none>
2017-01-12 10:50:23 configure libopenshot10:amd64 0.1.3+0+570+106+201612202337+daily~ubuntu16.04.1 <none>
2017-01-12 10:50:23 configure libubsan0-armhf-cross:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:50:23 configure libgcc-5-dev-armhf-cross:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:50:24 configure linux-image-4.4.0-59-generic:amd64 4.4.0-59.80 <none>
2017-01-12 10:50:45 configure libavfilter-ffmpeg5:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:50:45 configure ubuntu-release-upgrader-gtk:all 1:16.04.20 <none>
2017-01-12 10:50:45 configure grub-efi-amd64:amd64 2.02~beta2-36ubuntu3.6 <none>
2017-01-12 10:51:06 configure libavcodec-dev:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:51:06 configure apport-gtk:all 2.20.1-0ubuntu2.4 <none>
2017-01-12 10:51:06 configure grub-efi-amd64-signed:amd64 1.66.6+2.02~beta2-36ubuntu3.6 <none>
2017-01-12 10:51:19 configure libavformat-dev:amd64 7:2.8.10-0ubuntu0.16.04.1 <none>
2017-01-12 10:51:19 configure gcc-5-arm-linux-gnueabihf:amd64 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:51:20 configure libstdc++-5-dev-armhf-cross:all 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:51:20 configure g++-5-arm-linux-gnueabihf:amd64 5.4.0-6ubuntu1~16.04.4cross1 <none>
2017-01-12 10:51:20 configure libnss3-nssdb:all 2:3.26.2-0ubuntu0.16.04.2 <none>
2017-01-12 10:51:20 configure libnss3:amd64 2:3.26.2-0ubuntu0.16.04.2 <none>
2017-01-12 10:51:21 configure google-chrome-stable:amd64 55.0.2883.87-1 <none>
2017-01-12 10:51:22 configure flashplugin-installer:amd64 24.0.0.194ubuntu0.16.04.1 <none>
```

---

### Post by wildmanne39 on 2017-01-14
If you post the information asked for in post 5 we will probably be able to help you.

If you had secure boot turned off and wifi was working and you turned it on and it stopped that is probably the problem, secure boot will not let third party drivers load when it is on.

---

### Post by digital-larry on 2017-01-15
I will try.  I'll have to save all the commands and then copy them when I'm booted into the actual hard drive.  Whether I enable Secure Boot or disable it (in BIOS) makes no difference.  I'll follow up tomorrow.  Thanks!

---

### Post by digital-larry on 2017-01-15
I downloaded the wireless-info.txt file to a USB drive from Windows then rebooted into Ubuntu.  Ubuntu did not mount the USB stick automatically, so I went back to Windows and put the file onto the D:/ drive (partition) which is available from both Ubuntu and Windows.

See next post for the script output.

---

### Post by digital-larry on 2017-01-15
All right, I tried it with sudo this time, and renamed the script to .sh from .txt prior to running it. 

 Report follows:

```



########## wireless info START ##########


Report from: 15 Jan 2017 20:20 PST -0800


Booted last: 15 Jan 2017 00:00 PST -0800


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]


03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave AR9485 Wireless Network Adapter [1a3b:2126]


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 004: ID 0457:1023 Silicon Integrated Systems Corp. 
Bus 002 Device 003: ID 13d3:5195 IMC Networks 
Bus 002 Device 002: ID 13d3:3402 IMC Networks 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root       964     1  0 20:16 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Weaved-a07b80]] (600 root)
[connection] id=Weaved-a07b80 | type=802-11-wireless
[802-11-wireless] ssid=Weaved-a07b80 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-C46518]] (600 root)
[connection] id=BUZZI-C46518 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-C46518 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D08D1C]] (600 root)
[connection] id=BUZZI-D08D1C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D08D1C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-C45E3C]] (600 root)
[connection] id=BUZZI-C45E3C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-C45E3C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/OPENWRT-WIFI_1]] (600 root)
[connection] id=OPENWRT-WIFI_1 | type=802-11-wireless
[802-11-wireless] ssid=OPENWRT-WIFI_1 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D08C6C]] (600 root)
[connection] id=BUZZI-D08C6C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D08C6C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/weaved]] (600 root)
[connection] id=weaved | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=weaved
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OPENWRT-WIFI_2]] (600 root)
[connection] id=OPENWRT-WIFI_2 | type=802-11-wireless
[802-11-wireless] ssid=OPENWRT-WIFI_2 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CE99F0]] (600 root)
[connection] id=BUZZI-CE99F0 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CE99F0 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CE9D0C]] (600 root)
[connection] id=BUZZI-CE9D0C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CE9D0C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D09AE0]] (600 root)
[connection] id=BUZZI-D09AE0 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D09AE0 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CEA2EC]] (600 root)
[connection] id=BUZZI-CEA2EC | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CEA2EC | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D090FC]] (600 root)
[connection] id=BUZZI-D090FC | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D090FC | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D08E58]] (600 root)
[connection] id=BUZZI-D08E58 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D08E58 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Weaved-a07aa0]] (600 root)
[connection] id=Weaved-a07aa0 | type=802-11-wireless
[802-11-wireless] ssid=Weaved-a07aa0 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Panera]] (600 root)
[connection] id=Panera | type=802-11-wireless
[802-11-wireless] ssid=Panera | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-C46524]] (600 root)
[connection] id=BUZZI-C46524 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-C46524 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/LGPLPublicWiFi]] (600 root)
[connection] id=LGPLPublicWiFi | type=802-11-wireless
[802-11-wireless] ssid=LGPLPublicWiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Mountain-Charlie]] (600 root)
[connection] id=Mountain-Charlie | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Mountain-Charlie
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/OpenWrt]] (600 root)
[connection] id=OpenWrt | type=802-11-wireless
[802-11-wireless] ssid=OpenWrt | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-C46238]] (600 root)
[connection] id=BUZZI-C46238 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-C46238 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D08C08]] (600 root)
[connection] id=BUZZI-D08C08 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D08C08 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CE99EC]] (600 root)
[connection] id=BUZZI-CE99EC | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CE99EC | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Weaved-a07cd8]] (600 root)
[connection] id=Weaved-a07cd8 | type=802-11-wireless
[802-11-wireless] ssid=Weaved-a07cd8 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D0982C]] (600 root)
[connection] id=BUZZI-D0982C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D0982C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TLGPublic]] (600 root)
[connection] id=TLGPublic | type=802-11-wireless
[802-11-wireless] ssid=TLGPublic | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Weaved-a07938]] (600 root)
[connection] id=Weaved-a07938 | type=802-11-wireless
[802-11-wireless] ssid=Weaved-a07938 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/HOME-DF02]] (600 root)
[connection] id=HOME-DF02 | type=802-11-wireless
[802-11-wireless] ssid=HOME-DF02 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CEA8AC]] (600 root)
[connection] id=BUZZI-CEA8AC | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CEA8AC | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CEAB90]] (600 root)
[connection] id=BUZZI-CEAB90 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CEAB90 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D08E2C]] (600 root)
[connection] id=BUZZI-D08E2C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D08E2C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CE99F8]] (600 root)
[connection] id=BUZZI-CE99F8 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CE99F8 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AJ_OpenWRT <MAC address>]] (600 root)
[connection] id=AJ_OpenWRT <MAC address> | type=802-11-wireless
[802-11-wireless] ssid=AJ_OpenWRT <MAC address> | mac-address=54:27:1E:AB:1E:97
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/WAPD-235N_29fef9]] (600 root)
[connection] id=WAPD-235N_29fef9 | type=wifi | permissions=user:gary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WAPD-235N_29fef9
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Weaved]] (600 root)
[connection] id=Weaved | type=802-11-wireless
[802-11-wireless] ssid=Weaved | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-CA1840]] (600 root)
[connection] id=BUZZI-CA1840 | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-CA1840 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D08D4C]] (600 root)
[connection] id=BUZZI-D08D4C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D08D4C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/BUZZI-D08D0C]] (600 root)
[connection] id=BUZZI-D08D0C | type=802-11-wireless
[802-11-wireless] ssid=BUZZI-D08D0C | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


nl80211 not found.


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rndis_host)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[    1.802508] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)


########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-01-15
Please do:
```
sudo modprobe ath9k
```
does wifi come on? if so do not reboot and see if it continues to work if not we will add it to the modules file.

---

### Post by digital-larry on 2017-01-15
gary@gary-S551LA:~$ sudo modprobe ath9k
[sudo] password for gary: 
modprobe: FATAL: Module ath9k not found in directory /lib/modules/4.4.0-59-generic

---

### Post by wildmanne39 on 2017-01-15
Was that all the error message? did you upgrade to a new kernel? if so please give link and commands used.

That driver comes with ubuntu, I have used it for several years.

You can boot an older kernel and it will probably have wifi.

We can install the driver if needed.

---

### Post by digital-larry on 2017-01-15
That was the full error message.  To my knowledge I did not upgrade the kernel.  Wifi worked when booting from Live DVD.

Out of curiosity, how do we exhaust fully the suspicion of "Secure Boot and 3rd party drivers"?  I know I have said that the situation doesn't change whether Secure Boot is enabled or not in BIOS, but how can I be sure I'm doing the right thing?

I can try loading an older version through GRUB. I suppose there's no harm in trying.

Thanks,

DL

---

### Post by wildmanne39 on 2017-01-15
It is not secure boot and third party drivers because that driver is part of the kernel when you install ubuntu.

Did you do a minimal install by chance? I suspect something went wrong with the install, are you having any other issues?

---

### Post by digital-larry on 2017-01-15
Thanks a lot for your help.

To summarize, everything was working fine up until last Thursday.  It is not a minimal install.  It is a default install.

I got a warning from the package manager telling me to run dpkg --configure -a.  I did that and an overview of the updated packages is a few posts up.

I got another dialog asking me to disable secure boot so drivers could be installed or updated.  I was asked for a password.  Then I rebooted and now I'm in the state I'm in.

No eth0 or wlan0 devices.  Audio does not work.  USB does not mount a flash drive plugged in.  Before Thursday, EVERYTHING worked fine.

---

### Post by digital-larry on 2017-01-17
I guess this one stumped our panel of celebrity judges!  Something bad and out of the ordinary must have happened although I cannot tell you what it was.  I did a backup of my home directory to the shared partition then reinstalled 16.04 from DVD.  Other than the launcher disappearing (sudo service lightdm restart solved that) and all of my previously installed applications and carefully setup up file and folder permissions for Debian package creation, I guess I am back in business.  I hope that doesn't happen again!

---

### Post by wildmanne39 on 2017-01-17
I am sorry I did not receive an email telling me there had been a new post in this thread and I missed seeing it without the notification.

---

### Post by digital-larry on 2017-01-17
I appreciate your efforts to assist.  I just needed to get back to productivity and while not completely back to where I was, I'm pretty close.  If it happens again I'll certainly come back.

DL

---

