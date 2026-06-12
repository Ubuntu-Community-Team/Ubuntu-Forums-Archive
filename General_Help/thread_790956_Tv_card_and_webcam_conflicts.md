---
title: "Tv card and webcam conflicts"
date: 2008-05-11
forum: General Help
---

### Post by mumx2 on 2008-05-11
TV card and Webcam conflicts.
Trying to install webcam, whithout success. Installed drivers, but all the applications detect TV card instead of my Webcam.
I'm using WinFast Dtv2000 (works with Me TV application) and Creative web camera (found drivers at [https://help.ubuntu.com/community/EasyCam?action=fullsearch&value=linkto%3A%22EasyCam%22&context=180](https://help.ubuntu.com/community/EasyCam?action=fullsearch&value=linkto%3A%22EasyCam%22&context=180))
I'll very much appreciate some help. Thanks

---

### Post by fragos on 2008-05-11
webcam and TV cards are both mounted to /dev/video0 thru /dev/video{number}. With paralell startup either may end up being video0. The answer is to create a rule to mount by vender:device to a fixed mount point. here's my /etc/udev/rules.d/95-perso.rules:

KERNEL=="video*", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYSFS{name}=="ivtv0 encoder MPEG", SYMLINK+="video/pvr150"
KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/bttv"
KERNEL=="video*", SYSFS{vendor}=="0x046d", SYSFS{device}=="0x092e", SYMLINK+="video/webcam"

In my case I have two TV cards and a webcam.

---

### Post by mumx2 on 2008-05-12
Thanks for your quick reply.
I don't have the file you mentioned /etc/udev/rules.d/95-perso.rules,but I'd found another that it looks to me that can be edited with the information you gave me. Is
/etc/udev/rules.d/z80_user.rules which at the moment it is empty or must I create a new one for 95-perso.rules?
The webcam info in my lsusb is: 
Device 003: ID 041e:405f Creative Technology, Ltd
I don't know where to find about WinFast TV card details.
Thank you

---

### Post by fragos on 2008-05-12
I'm not an expert on UDEV but did create 95-perso.rules myself. I chose that name based on a long forgotten tutorial. In the following, I used your lsusb data to change the webcam rule

KERNEL=="video*", SYSFS{vendor}=="0x041e", SYSFS{device}=="0x405f", SYMLINK+="video/webcam"

Note that the new mount point is /dev/video/webcam

"lspci -nn" will give you the data you need. Below is my TV card, "[109e:036e]" were the numbers I needed.

00:0a.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)

---

### Post by mumx2 on 2008-05-14
I have to ask for your help again, because I can't "see" where is the details of the TV video card. I'm writing my lspci -nn for you so perhaps you can point it out to me.
00:00.0 Host bridge [0600]: nVidia Corporation nForce3 250Gb Host Bridge [10de:00e1] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 250Gb LPC Bridge [10de:00e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation nForce 250Gb PCI System Management [10de:00e4] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 EHCI USB 2.0 Controller [10de:00e8] (rev a2)
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce3 250Gb AC'97 Audio Controller [10de:00ea] (rev a1)
00:08.0 IDE interface [0101]: nVidia Corporation CK8S Parallel ATA Controller (v2.5) [10de:00e5] (rev a2)
00:0a.0 IDE interface [0101]: nVidia Corporation CK8S Serial ATA Controller (v2.5) [10de:00e3] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge [10de:00e2] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge [10de:00ed] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GS] [10de:02e1] (rev a2)
02:07.0 Multimedia video controller [0400]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
02:07.1 Multimedia controller [0480]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
02:07.2 Multimedia controller [0480]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
02:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

Is WinFast Dtv card anywhere up there? 
I'm really appreciating your help.

Thank you

---

### Post by fragos on 2008-05-14
I believe the following lines are from your TV card

02:07.0 Multimedia video controller [0400]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
02:07.1 Multimedia controller [0480]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
02:07.2 Multimedia controller [0480]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)

I'd give the following rule a try.

KERNEL=="video*", SYSFS{vendor}=="0x14f1", SYSFS{device}=="0x8800", SYMLINK+="video/tv"

TV mount point will be /dev/video/tv

---

### Post by mumx2 on 2008-05-15
Hi George,
I tried your suggestion, but it is not responding. Still ignoring my Webcam despite its lights are on. This indicates that is ready to work. Tried all software (Cheese, Camorama, Ekiga) all registering the Tv card but no sign of Webcam. I'm on Ubuntu 8.04 Kernel 2.6.24.16 (last Ubuntu version). Perhaps the best way is to leave up to the distro find out the problem to fix it. I guess lots of people have the same problem as per commentaries in the forums. Meanwhile if I find a solution I'll post it here.
I had lots of problems installing my Tv Card too. At the end only a new (low rated!!) package -MeTv- did the trick for me and put my channels configuration and audio in place to work at the first instance. 
Hopefully is going to work that way for webcam very soon.   
Thanks for your interest and help.

---

