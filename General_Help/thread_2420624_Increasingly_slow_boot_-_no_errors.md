---
title: "Increasingly slow boot - no errors"
date: 2019-06-07
forum: General Help
---

### Post by makem2 on 2019-06-07
I have noticed that the boot time appears to be getting noticeable slower and slower as if there is an accumulating error somewhere. I hope the information posted is helpful.

Guidance to resolve the issue would be appreciated.

```

makem@ssdTOSH:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
makem@ssdTOSH:~$

```

```

makem@ssdTOSH:~$ dmesg | pastebinit
[http://paste.ubuntu.com/p/N6g6cxKHQK/]("http://paste.ubuntu.com/p/N6g6cxKHQK/")
makem@ssdTOSH:~$

```

```

makem@ssdTOSH:~$ sudo dmidecode | pastebinit
[http://paste.ubuntu.com/p/FDwYxPphpS/]("http://paste.ubuntu.com/p/FDwYxPphpS/")
makem@ssdTOSH:~$

```

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=7f90b906-206f-4806-b66d-a83db8f7f3d0 /               ext4    errors=remount-ro 0    $
# /boot/efi was on /dev/sda1 during installation
UUID=CCBC-12A0  /boot/efi       vfat    umask=0077      0       0
# /home was on /dev/sda3 during installation
UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1 /home           ext4    defaults        0      $
# swap was on /dev/sda4 during installation
#UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5 none            swap    sw              0     $
UUID=0178c9df-c13e-434d-bb57-b6c19095f4aa none  swap    0       0
none /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1024M 0 0
#WinData
UUID=D232DC8B32DC75C7   /media/WinData  ntfs defaults   0       0

```

```

makem@ssdTOSH:~$ ifconfig -a
enp8s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 2c:60:0c:8a:6e:27  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 757  bytes 81594 (81.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 757  bytes 81594 (81.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.33  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::3e1:80ed:4079:7704  prefixlen 64  scopeid 0x20<link>
        ether 34:e6:ad:ba:1f:d0  txqueuelen 1000  (Ethernet)
        RX packets 4306390  bytes 6477261466 (6.4 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1718804  bytes 175123825 (175.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

makem@ssdTOSH:~$ iwconfig
wlp7s0    IEEE 802.11  ESSID:"makem_5GH"  
          Mode:Managed  Frequency:5.56 GHz  Access Point: AC:9E:17:66:5D:5C   
          Bit Rate=433.3 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:378   Missed beacon:0

lo        no wireless extensions.

enp8s0    no wireless extensions.

makem@ssdTOSH:~$

```

```

makem@ssdTOSH:~$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @19.355s
&#9492;&#9472;multi-user.target @19.355s
  &#9492;&#9472;smbd.service @19.246s +109ms
    &#9492;&#9472;winbind.service @19.164s +80ms
      &#9492;&#9472;nmbd.service @9.087s +10.075s
        &#9492;&#9472;network-online.target @9.084s
          &#9492;&#9472;NetworkManager-wait-online.service @2.824s +6.259s
            &#9492;&#9472;NetworkManager.service @2.577s +246ms
              &#9492;&#9472;dbus.service @2.559s
                &#9492;&#9472;basic.target @2.521s
                  &#9492;&#9472;sockets.target @2.521s
                    &#9492;&#9472;snapd.socket @2.517s +2ms
                      &#9492;&#9472;sysinit.target @2.515s
                        &#9492;&#9472;apparmor.service @1.676s +839ms
                          &#9492;&#9472;local-fs.target @1.675s
                            &#9492;&#9472;run-user-1000-gvfs.mount @15.488s
                              &#9492;&#9472;run-user-1000.mount @13.445s
                                &#9492;&#9472;swap.target @1.162s
                                  &#9492;&#9472;dev-disk-by\x2duuid-0178c9df\x2dc13e\x2d434d\x2dbb57\x2db6c19095f4aa.swap @1.147s +15ms
                                    &#9492;&#9472;dev-disk-by\x2duuid-0178c9df\x2dc13e\x2d434d\x2dbb57\x2db6c19095f4aa.device @1.146s

```

---

### Post by him610 on 2019-06-07
Maybe the slowness is due to the effect of the recent cpu microcode updates.

---

### Post by makem2 on 2019-06-08
I see it was updated in March 2019 but is that an automatic update? I never updated it unless it came with a Linux update.

---

### Post by garvinrick4 on 2019-06-12
I always try a different kernal when problems arise. Boot screen arrow down select kernel hit enter.
if the same i of course fix broken packages 
> sudo dpkg --configure -a
All the simple things first i start with. If still slow boot
> sudo gedit /etc/default/grub
  change this entry to "text" hit save
GRUB_CMDLINE_LINUX_DEFAULT="text"
> sudo update-grub
reboot you will see if all is starting up fine with text mode. Interesting for you really.
If your boot stays terribly slow backup your files to USB stick or other type of drive. 
and reinstall will be the fastest way to go. Sure you have your install USB handy if not
make one. 
I have myself screwed up  installs messing with things but never had an install just start slow boot on its own.
If you want to learn to put in latest kernel follow this. Just to learn. 
Go to:  kernel.[ubuntu.com/~kernel-ppa/mainline/v5.1.9/]("http://kernel.ubuntu.com/~kernel-ppa/mainline")
Choose these four one at a time and hit save and will go to downloads
   [linux-headers-5.1.9-050109_5.1.9-050109.201906111132_all.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-headers-5.1.9-050109_5.1.9-050109.201906111132_all.deb")
    [linux-headers-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-headers-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb")
  [linux-image-unsigned-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-image-unsigned-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb")
  [linux-modules-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-modules-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb")

I move them to Desktop so know other .deb files because i install all together such as.
Open terminal
> cd Desktop
To make sure files there
> ls
Install
> sudo dpkg -i *.deb
now reboot and you have latest kernal
I would say most likely to reinstall but if one of these does anything good then cool.
Hopefully this helped you learn a few things new installing new kernel is just learning you have other kernels to test already installed to use. 
  Just so hard to figure something like slow boot but every once in a will Bingo! Put it in a document and pass it down if needed

---

### Post by makem2 on 2019-06-24
Thank you. I have just got back from a 2 week break and will start sorting this out using your suggestions.

---

### Post by makem2 on 2019-06-24
> **garvinrick4 said:**
> I always try a different kernal when problems arise. Boot screen arrow down select kernel hit enter.
if the same i of course fix broken packages 

All the simple things first i start with. If still slow boot

  change this entry to "text" hit save
GRUB_CMDLINE_LINUX_DEFAULT="text"

reboot you will see if all is starting up fine with text mode. Interesting for you really.
If your boot stays terribly slow backup your files to USB stick or other type of drive. 
and reinstall will be the fastest way to go. Sure you have your install USB handy if not
make one. 
I have myself screwed up  installs messing with things but never had an install just start slow boot on its own.
If you want to learn to put in latest kernel follow this. Just to learn. 
Go to:  kernel.[ubuntu.com/~kernel-ppa/mainline/v5.1.9/]("http://kernel.ubuntu.com/~kernel-ppa/mainline")
Choose these four one at a time and hit save and will go to downloads
   [linux-headers-5.1.9-050109_5.1.9-050109.201906111132_all.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-headers-5.1.9-050109_5.1.9-050109.201906111132_all.deb")
    [linux-headers-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-headers-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb")
  [linux-image-unsigned-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-image-unsigned-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb")
  [linux-modules-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.1.9/linux-modules-5.1.9-050109-generic_5.1.9-050109.201906111132_amd64.deb")

I move them to Desktop so know other .deb files because i install all together such as.
Open terminal

To make sure files there

Install

now reboot and you have latest kernal
I would say most likely to reinstall but if one of these does anything good then cool.
Hopefully this helped you learn a few things new installing new kernel is just learning you have other kernels to test already installed to use. 
  Just so hard to figure something like slow boot but every once in a will Bingo! Put it in a document and pass it down if needed

snip>
change this entry to "text" hit save
GRUB_CMDLINE_LINUX_DEFAULT="text"

reboot you will see if all is starting up fine with text mode. Interesting for you really.
If your boot stays terribly slow backup your files to USB stick or other type of drive. 
and reinstall will be the fastest way to go. Sure you have your install USB handy if not
make one. 
snip>

How to stop the text scrolling and disappearing? Tried |more.

---

