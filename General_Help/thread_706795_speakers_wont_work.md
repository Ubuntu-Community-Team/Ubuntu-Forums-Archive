---
title: "speakers wont work"
date: 2008-02-24
forum: General Help
---

### Post by pain1337 on 2008-02-24
i keep getting this error
.

No volume control GStreamer plugins and/or devices found.

and

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

help me

---

### Post by xarquid on 2008-02-24
I'm interested in this as well...

This cropped up upon reinstallation.

I am using a Soundblaster Audigy ZS card...

I have tried selected all audio options for OUTPUT and none work (even when testing).

Thanks guys. I'm continuing to work through it myself...I can't get alsamixer to open and this is generally my "first line" of troubleshooting for this, so I'm dead in the water. I'm looking into other work arounds myself.

What sound card are you using?

XQ

---

### Post by pain1337 on 2008-02-24
im not sure where do i find it???

---

### Post by polmir on 2008-02-24
Type in terminal
```
alsamixer
```
and item it

---

### Post by pain1337 on 2008-02-25
i get this error  


alsamixer: function snd_ctl_open failed for default: No such device:(

---

### Post by xarquid on 2008-02-26
Same error.

XPS 720. ... sound card noted above.
NVidia video card.

Etc.

---

### Post by superprash2003 on 2008-02-26
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by polmir on 2008-02-26
type in terminal
```
lspci 
```
and post output of it

---

### Post by pain1337 on 2008-02-26
> **polmir said:**
> type in terminal
```
lspci 
```
and post output of it

i got this:

home@home-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:05.0 Communication controller: Agere Systems Unknown device 0620
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


> **superprash2003 said:**
> try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

that didnt work

---

### Post by polmir on 2008-02-27
Red this
[HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
[SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28CategoryDocumentation%29")

---

### Post by pain1337 on 2008-02-27
> **polmir said:**
> Red this
[HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
[SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28CategoryDocumentation%29")

thanks dude:KS

---

