---
title: "Nothing works after fresh Ubuntu 14.04 install"
date: 2014-12-21
forum: General Help
---

### Post by ugrin.lu on 2014-12-21
Hi everyone, I'm a linux newbie so sorry for my ignorance...

I used unetbootin to create a live USB with Ubuntu 14.0.4
I gave it a try first, everything was working perfectly so I installed it. Now I boot up and nothing works!? Only the keyboard works and I have very low graphics. No USB, no WiFi, no mouse...

I tried connecting through ethernet, it won't work. I've searched everywhere, I've only found one user having the same problem, but there was no answer... I have no other options but to ask for help, I don't have another machine to create new live USB, I only have my phone to access internet.
I will post all the info you guys need to get this thing to work...

Lenovo IdeaPad Y570
OS: Ubuntu 14.04 LTS
RAM: 4GB
Processor: Intel® Core&#8482; i5-2410M CPU @ 2.30GHz × 4

Anything else you need from the terminal you can ask and I will post, because I don't know the commands...

I also downloaded the wireless_script I saw posted in the forums, I will post results.

Thanks!

Edit:

This is all the info from the script.

```
########## wireless info START ##########

Report from: 21 Dec 2014 16:08 CET +0100

Booted last: 21 Dec 2014 15:53 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe [14e4:16b1] (rev 10)
    Subsystem: Lenovo Device [17aa:3975]

08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]

09:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)

##### lsusb #############################

Bus 002 Device 004: ID 5986:a006 Acer, Inc 
Bus 002 Device 003: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

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

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

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

[[/etc/NetworkManager/system-connections/ZiggoFE450]] (600 root)
[connection] id=ZiggoFE450 | type=802-11-wireless
[802-11-wireless] ssid=ZiggoFE450 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

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
rtc

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b1 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0084 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############
```

Edit: Its not solved, i just gave up and used another distro...

---

### Post by TheFu on 2014-12-21
Sorry that things didn't "just work" for you. Really, that is what happens for most people - things just work these days.

It is really weird.  If nothing worked, I'd attempt a fresh install and select all the defaults.  Of course, if you are trying to dual-boot, that really isn't possible (might wipe the other OS), so be careful.

No way to tell what's wrong, but suspect the flash drive used to install it was corrupt in some way or the userid selected had something funny about it - lowercase, no funny characters or spaces. I'm guessing big time.

BTW, opening a thread for each issue might be smarter and putting the laptop model in the title might get folks with that model to help.  People who know about video drivers don't always know about wifi. See what I mean?  Also, does the wired ethernet work? That will make things easier to fix.

If this isn't a single OS install, you could run a virtual machine with Ubuntu inside. Ask if you'd like more information. Your processor and RAM can easily handle this.

Regardless, Ubuntu does require a little maintenance to stay happy. [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) explains and was republished by lifehacker.

---

### Post by ugrin.lu on 2014-12-21
I read somewhere while I´m researching this that unetbootin has some trouble with Ubuntu 14.04 but I don´t know what.

I did a clean install 3 times, formated the whole hard disk and everything. All the time with the default settings.

Now I decided to try with different distro. I installed Elementary OS because I liked how it looks (I´m not a power user as you can tell probably). Everything runs smoothly and I´m very happy with how it turned out.

Now I only have to get used to using Linux, it´s very different then Windows.

Thanks anyway

---

### Post by TheFu on 2014-12-21
So - have you tried something other than unetbootin?  Yumi?

Linux **is** a very different OS than Windows.  This [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) will save you a bunch of frustration and clearly state some fundamentally different assumptions that former-Windows people might get wrong about Linux. 10 minutes now will save you a bunch of frustration.

Glad you found something that works. That is the important part.

---

