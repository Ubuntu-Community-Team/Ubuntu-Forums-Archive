---
title: "[SOLVED] Sound problem"
date: 2007-12-03
forum: General Help
---

### Post by samurailink3 on 2007-12-03
I have sound in VLC, but not in miro or totem. This is pretty annoying to say the least. Any ideas? Thanks in advance!!

---

### Post by marcopolo1981 on 2007-12-03
Hi.
Is your sound card fully set up? ie. When you boot up, do you hear the start-up tune? If not, What sound card are you using?

---

### Post by Crafty Kisses on 2007-12-03
> **samurailink3 said:**
> I have sound in VLC, but not in miro or totem. This is pretty annoying to say the least. Any ideas? Thanks in advance!!

Hmmm, post the following output: 
```
lspci
```

---

### Post by samurailink3 on 2007-12-03
```
samurailink3@FragProLaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
samurailink3@FragProLaptop:~$ 

```

Just to let you all know, this isn't a fresh install. The problem just popped up this morning, I've been running Gutsy since release, and previous versions for a while now.

---

### Post by ericesque on 2007-12-03
What are you trying to play?  MP3s?  I think VLC can play MP3s out of the box.  Other apps like Totem (maybe miro)  would require the installation of restricted codecs in order to play MP3s.

Go to Applications> Add/Remove Applications   

Make sure the drop down selection  Show:  says 'All Available Applications'  Then search for Restricted Extras.

Install the restricted extras *mind the usage warnings* and you should be able to listen to MP3s in your apps :)

---

### Post by samurailink3 on 2007-12-03
The only problem is that yesterday it was playing all of the formats just fine (I installed the codecs when I first installed when gutsy was released), now it loads the file, but alas! No sound feedback :( . I get video, but the audio icon is grayed out (see [screenshot]("http://samurailink3.googlepages.com/totem.png")). Thanks again for all the help so far!

---

### Post by samurailink3 on 2007-12-03
To further the problem, I get no sound in games or flash based videos. Youtube in firefox yields no sound, and NES emulators don't give any sound either. Even under a different username. This is confusing me... :confused:  Any ideas?

---

### Post by samurailink3 on 2007-12-03
Could this be an alsa problem? If so, where can I 'factory default' my sound settings? I know with apps, I can just delete the (in the case of firefox) .mozilla folder and viola! It defaulted... any way to do that with alsa? And if so, how?

Ok.. amarok and songbird both freeze on startup... that's telling me that there's something wrong with the sound.. but then why is vlc working... Thanks for help and/or speculation!!

EDIT!!

Ok... Amarok loaded. But All I can hear is static... OSS works, but I would much rather prefer alsa.

EDIT AGAIN!!

Ok... I feel really stupid. Simple mistake. Somehow, someway, by some act of Tux himself... PCM was turned all the way down... The master volume.. the one I had been playing with all day, was up. But PCM got shot down to nothing... needless to say, check the smallest things first. I learned my lesson ;)   Thanks for helping anyway!! Hopefully this helps someone else someday!

---

