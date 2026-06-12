---
title: "New USB 3 Flash Drive not Recognized"
date: 2018-09-25
forum: General Help
---

### Post by ricky25 on 2018-09-25
Hi, I'm running Ubuntu Mate 18.04, I have three flash drives including a Toshiba usb 3 16GB, all work fine. I decided to buy a bigger drive for media storage and bought an identical Toshiba usb 3 flash drive but a 64GB one, the flash drive isn't recognized or shows up in Disks, gparted or any terminal command I've tried, it simply doesn't exist when plugged into my Intel NUC mini pc.  

All other usb devices run perfectly, including my Toshiba 500GB usb 3 hard drive, 16GB usb flash drive etc, the new flash drive is recognized and shows up when plugged into my PS4, is this a software issue or do you think it's hardware related, thanks.

---

### Post by oldfred on 2018-09-25
Is it already formatted as exFAT?

I have many USB flash drives, both 32 & 64GB. But they are MicroCenter's house brand and just work. I found USB3 flash drive was about 10% faster in USB2 ports on old system, so I converted to USB3 drives when price fell to just a dollar or two more than USB2.

---

### Post by ricky25 on 2018-09-26
Thanks for your reply and help, I'll read the article in your link, just need to get a longer hdmi cable, my main monitor is a hdtv and doesn't support the bios resolution so I need to keep plugging it into a 22" monitor to view the bios settings.

---

### Post by ricky25 on 2018-09-26
Forgot to ask, would buying usb 2 flash drive work? or could there still be a problem, any recommend brands, I live in the UK, thank you.

---

### Post by Yellow Pasque on 2018-09-26
> the flash drive isn't recognized or shows up in Disks, gparted or any terminal command

First, run this, just to make lsusb a bit more human-readable:
```
sudo update-usbids
```

Then, plug the drive in and look at:
```
lsusb
dmesg | tail -n 20
```

---

### Post by Autodave on 2018-09-26
USB 2 and 3 will all work.  However, there are instances where a USB2 stick will not work in a USB3 receptacle.  Why? Dunno.  They are *supposed*to work, but every once in awhile.........

Have you tried the new stick in another machine just to make sure it works?  I had a brand new once that was bad.

---

### Post by C.S.Cameron on 2018-09-26
They are starting to make some really cheepo multiple layer flash drives.
Large and cheap, but only good for 50 -100 writes.
Single layer are most reliable but expensive.
Seagate claims that they sell only MCL drives.
MCL should be good for 5000 to 10000 writes.

---

### Post by ricky25 on 2018-09-26
Hi, thank you for helping, will run those commands when I get home and post the results.

---

### Post by ricky25 on 2018-09-26
> **Temüjin said:**
> First, run this, just to make lsusb a bit more human-readable:
```
sudo update-usbids
```

Then, plug the drive in and look at:
```
lsusb
dmesg | tail -n 20
```

I think I did it correctly, I did have my Toshiba 500GB external hard drive plugged in, here's the output.


ricky@Mate:~$ sudoupdate-usbids
[sudo] password forricky: 
--2018-09-2621:31:28--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
Resolvingwww.linux-usb.org ([www.linux-usb.org](www.linux-usb.org))... 216.105.38.10
Connecting towww.linux-usb.org ([www.linux-usb.org)|216.105.38.10|:80](www.linux-usb.org)|216.105.38.10|:80)... connected.
HTTP request sent,awaiting response... 200 OK
Length: 597855(584K) [text/plain]
Saving to:‘/var/lib/usbutils/usb.ids.new’


/var/lib/usbutils/u100%[===================>] 583.84K   272KB/s    in 2.1s    


2018-09-26 21:31:31(272 KB/s) - ‘/var/lib/usbutils/usb.ids.new’ saved[597855/597855]


Done.


ricky@Mate:~$ lsusb
Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006:ID 8087:0aa7 Intel Corp. 
Bus 001 Device 005:ID 0480:a200 Toshiba America Inc 
Bus 001 Device 003:ID 045e:07f8 Microsoft Corp. Wired Keyboard 600 (model 1576)
Bus 001 Device 002:ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub




ricky@Mate:~$ dmesg| tail -n 20
[   15.893294]audit: type=1326 audit(1537992069.467:48): auid=4294967295 uid=0gid=0 ses=4294967295 pid=1324 comm="usb_modeswitch"exe="/snap/usbmode-switch/27/usr/sbin/usb_modeswitch" sig=0arch=c000003e syscall=41 compat=0 ip=0x7f5e1dc9b5a7 code=0x50000
[   16.304642]audit: type=1326 audit(1537992069.879:49): auid=4294967295 uid=0gid=0 ses=4294967295 pid=1339 comm="usb_modeswitch"exe="/snap/usbmode-switch/27/usr/sbin/usb_modeswitch" sig=0arch=c000003e syscall=41 compat=0 ip=0x7f5b2798d5a7 code=0x50000
[   16.709637]audit: type=1326 audit(1537992070.283:50): auid=4294967295 uid=0gid=0 ses=4294967295 pid=1354 comm="usb_modeswitch"exe="/snap/usbmode-switch/27/usr/sbin/usb_modeswitch" sig=0arch=c000003e syscall=41 compat=0 ip=0x7f599ba185a7 code=0x50000
[ 1609.555754]wlp2s0: authenticate with b8:ee:0e:f0:a5:a6
[ 1609.560316]wlp2s0: send auth to b8:ee:0e:f0:a5:a6 (try 1/3)
[ 1609.564255]wlp2s0: authenticated
[ 1609.568060]wlp2s0: associate with b8:ee:0e:f0:a5:a6 (try 1/3)
[ 1609.571920]wlp2s0: RX AssocResp from b8:ee:0e:f0:a5:a6 (capab=0x431 status=0aid=2)
[ 1609.573928]wlp2s0: associated
[ 1609.628255] IPv6:ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 1612.494795]Bluetooth: RFCOMM TTY layer initialized
[ 1612.494806]Bluetooth: RFCOMM socket layer initialized
[ 1612.494814]Bluetooth: RFCOMM ver 1.11
[ 1615.824190]EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts:(null)
[ 1615.909602]FAT-fs (sdb2): Volume was not properly unmounted. Some data may becorrupt. Please run fsck.
[ 1615.982294]EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts:(null)
[ 1706.534862] [UFWBLOCK] IN=wlp2s0 OUT= MAC=01:00:5e:00:00:01:b8:ee:0e:f0:a5:94:08:00SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0DF PROTO=2 
[ 1831.803982] [UFWBLOCK] IN=wlp2s0 OUT= MAC=01:00:5e:00:00:01:b8:ee:0e:f0:a5:94:08:00SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0DF PROTO=2 
[ 1956.834183] [UFWBLOCK] IN=wlp2s0 OUT= MAC=01:00:5e:00:00:01:b8:ee:0e:f0:a5:94:08:00SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0DF PROTO=2 
[ 2081.556858] [UFWBLOCK] IN=wlp2s0 OUT= MAC=01:00:5e:00:00:01:b8:ee:0e:f0:a5:94:08:00SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0DF PROTO=2 
ricky@Mate:~$

---

### Post by ricky25 on 2018-09-27
Well I seemed to have inadvertently solved the problem, I bought a usb 3 hub and new Sandisk flash drive, confirmed by Sandisk to work with Linux, when I tried the Toshiba in the hub it just popped up on screen, yet would not work in any of the four PC's usb ports. Thanks for all your replies.

---

