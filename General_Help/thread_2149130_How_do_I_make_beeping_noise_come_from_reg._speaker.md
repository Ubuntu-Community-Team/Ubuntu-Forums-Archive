---
title: "How do I make beeping noise come from reg. speakers?"
date: 2013-05-27
forum: General Help
---

### Post by s3a on 2013-05-27
I am trying to get the "beep" command to come out of my regular speakers as regular sound instead of the speaker whose sole purpose is to make the beeping sound.

If someone could help me get that done, I would really appreciate it!

Here is my lspci output:
```
lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
```

and kernel version:
```
uname -r
3.2.0-4-amd64
```
```
uname -m
x86_64
```

I am using Debian 7 / Wheezy / Stable and, I started a thread there but, nobody answered it and, since this seems to be something that shouldn't vary across distributions, I was hoping that someone from these forums could help me. I am using Xfce, if that matters.

---

### Post by Charlotte18 on 2013-05-27
Have you checked your bios settings to see what kind of internal/external speaker options might be there?

---

### Post by tgalati4 on 2013-05-27
```
man beep
```

There is a switch to specify the device (-e devicename)

Try all of the devices in /dev/snd:

```
ls -la /dev/snd
```

If you get permission denied, you may have to add yourself to group "audio".

---

### Post by HiImTye on 2013-05-27
if you want to turn off your system speaker, you might have some luck with
```
alsamixer
```otherwise you might be able to reroute system speaker sounds in your .asoundrc

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by s3a on 2013-05-30
Actually, what tgalati4/you suggested is even better than what I had in mind initially! The only problem is that I can't get it to work!

What I had in mind originally was to just make the beeping noise come from the speakers instead of the speaker whose sole purpose is to make beeping sounds because I have a script that requires beeping noises (which I use as a heavily-personalized alarm clock) but, I always hated the beeping noises when I do something “wrong” while using the OS.

Assuming I understood correctly, what tgalati4/you suggested basically would allow me to completely remove any annoying beeping noises from my regular use while allowing me to use beeping noises from my regular speakers in my script without having to modify anything manually each time I want to run the script!

_Now for my challenges._:

(1)
My account DOES belong to the audio group (among other ones).

(2)
```
ls -la /dev/snd
total 0
drwxr-xr-x   3 root root      220 May 24 18:00 .
drwxr-xr-x  17 root root     3560 May 29 16:30 ..
drwxr-xr-x   2 root root       60 May 24 18:00 by-path
crw-rw---T+  1 root audio 116,  7 May 24 18:00 controlC0
crw-rw---T+  1 root audio 116,  6 May 24 18:00 hwC0D0
crw-rw---T+  1 root audio 116,  5 May 24 18:00 hwC0D3
crw-rw---T+  1 root audio 116,  4 May 24 18:01 pcmC0D0c
crw-rw---T+  1 root audio 116,  3 May 28 11:41 pcmC0D0p
crw-rw---T+  1 root audio 116,  2 May 24 18:01 pcmC0D3p
crw-rw---T+  1 root audio 116,  1 May 24 18:00 seq
crw-rw---T+  1 root audio 116, 33 May 24 18:00 timer
```

(3)
None of the devices listed in /dev/snd work when passed through the -e parameter of the beep command (assuming that I am running the command correctly).:
```
s3a@hostname:~$ beep -e /dev/snd/controlC0
ioctl: Inappropriate ioctl for device
ioctl: Inappropriate ioctl for device
s3a@hostname:~$ beep -e /dev/snd/hwC0D0
ioctl: Invalid argument
ioctl: Invalid argument
s3a@hostname:~$ beep -e /dev/snd/hwC0D3
ioctl: Invalid argument
ioctl: Invalid argument
s3a@hostname:~$ beep -e /dev/snd/pcmC0D0c
ioctl: Inappropriate ioctl for device
ioctl: Inappropriate ioctl for device
s3a@hostname:~$ beep -e /dev/snd/pcmC0D0p
ioctl: Inappropriate ioctl for device
ioctl: Inappropriate ioctl for device
s3a@hostname:~$ beep -e /dev/snd/pcmC0D3p
ioctl: Inappropriate ioctl for device
ioctl: Inappropriate ioctl for device
s3a@hostname:~$ beep -e /dev/snd/seq
ioctl: Inappropriate ioctl for device
ioctl: Bad address
s3a@hostname:~$ beep -e /dev/snd/timer
ioctl: Inappropriate ioctl for device
ioctl: Inappropriate ioctl for device
s3a@hostname:~$
```

Any help in getting the beep command's -e parameter to work successfully such that I can use the regular speakers to make the beeping noise through my script (or a terminal) but without having the beeping noise occur at any other time would be greatly appreciated!

---

### Post by tgalati4 on 2013-05-30
I got the same errors, so I suspect that the hardware device names may be something different.  Or the beep commands expect devices in /dev, not /dev/snd, so it would require a link to make new devices in /dev that link to the devices in /dev/snd.  You will have to continue your research.

I'm not sure if xmms2 will take tone commands, but the old xmms did.  That would be another way to make beep tones through your speakers.  To turn off system sounds, there might be an XFCE setting in the control panel.

---

### Post by Dwebtron on 2013-08-02
I'd like to throw my 2 cents in. 

I'm having this same issue, but I was able to fix it by using /dev/dsp instead of /dev/mixer like I was. An example command looks like: > beep -f 1000 -l 1000 -e /dev/dsp  instead of > beep -f 1000 -l 1000 -e /dev/mixer 

Well... "Fix" it anyway, now I have a "ioctl: Invalid argument" message. I figured this would help if this issue is still going on. =)

---

