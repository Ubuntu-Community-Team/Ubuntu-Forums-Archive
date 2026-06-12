---
title: "I cannot hear sound in Kubuntu Feisty"
date: 2007-05-05
forum: General Help
---

### Post by bcasanov on 2007-05-05
Hi,

I have been having this problem with not being able to hear any sound ever since I have freshly installed Kubuntu Feisty on my system, a Dell Optiplex GX150.  

Here is the output of the command lspci:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

Here is the output of the command aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The output of lspci -v:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
        Subsystem: Dell Unknown device 00be
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 00be
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Memory at fe080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: 20000000-200fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11) (prog-if 80 [Master])
        Subsystem: Dell Unknown device 00be
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 00be
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff80 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
        Subsystem: Dell Unknown device 00be
        Flags: medium devsel, IRQ 10
        I/O ports at dcd0 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 00be
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff60 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
        Subsystem: Dell Unknown device 00be
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]

01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: Dell Unknown device 00be
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at ec80 [size=128]
        Memory at fcfffc00 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <access denied>


I'm open to any suggestions and advice, as I really want this to work.

---

### Post by anirban.sam on 2007-05-05
Type alsamixer in a console and disable all IEC devices. Save alsactl config.

---

### Post by bcasanov on 2007-05-05
> **anirban.sam said:**
> Type alsamixer in a console and disable all IEC devices. Save alsactl config.
anirban.sam,

Thank you for your response.  The thing is that I am a newcomer to Linux, and when I put in the alsamixer command in Konsole, I got a graphical interface showing different volume bars like the master volume, etc.  I do not know how to disable IEC devices from there.  I am kind of lost as to the alsactl config thing you mentioned.  I searched for alsactl on my computer, and the search came up with a file named "alsactl" that I could not launch when I double-clicked on it.  In the the properties, I saw that it was an executable.  I really do not know what to do to implement your advice, unless you could explain step-by-step for a newbie...  :) 

Regards,
bcasanov

---

### Post by knightnet on 2007-05-05
Hi bcasanov,

To disable something, use the left/right cursor keys to highlight the entry and then press M to mute that entry.

---

### Post by bcasanov on 2007-05-05
> **knightnet said:**
> Hi bcasanov,

To disable something, use the left/right cursor keys to highlight the entry and then press M to mute that entry.

Thank you knightnet for your explanation!  Now that I know how to disable something in alsamixer, I forgot to tell you that I do not know which devices listed are IEC devices, as I do not see any reference to "IEC" there.

Regards,
bcasanov

---

### Post by orangep on 2007-05-05
RE: "run alsamixer"
I get:
alsamixer: function snd_ctl_open failed for default: No such device

I see boot messages saying that Kubuntu is running an experimental
dual-mode driver, something like oss and alsa.

I got XMMS running by choosing the OSS driver, rather than ALSA, which it
defaulted to. But not much else gives sound. Youtube videos, Firefox, CD player,
Totem movie player, all silent. I can't choose the driver that they will talk to.

Apparently the ALSA driver is not working.

---

### Post by orangep on 2007-05-06
There is a permissions problem involved here.
I was getting:
alsamixer: function snd_ctl_open failed for default: No such device
when I tried to run alsamixer.

Go to /dev/snd and
sudo chmod 666 *

Also in /dev, likewise change the modes of all of the audio devices.

If you do this:
ls -l /dev/* | grep audio
you should see:

crw-rw-rw- 1 root audio    14,  12 2007-04-21 20:47 /dev/adsp
crw-rw-rw- 1 root audio    14,   4 2007-04-21 20:47 /dev/audio
crw-rw-rw- 1 root audio    14,   3 2007-04-21 20:47 /dev/dsp
crw-rw-rw- 1 root audio    14,   5 2007-04-21 20:47 /dev/dspW
crw-rw-rw- 1 root audio    14,   2 2007-04-21 20:47 /dev/midi
crw-rw-rw- 1 root audio    14,  18 2007-04-21 20:47 /dev/midi1
crw-rw-rw- 1 root audio    14,   0 2007-04-21 20:47 /dev/mixer
crw-rw-rw- 1 root audio    10, 135 2007-04-21 20:47 /dev/rtc
crw-rw-rw- 1 root audio    14,   1 2007-04-21 20:47 /dev/sequencer
crw-rw-rw- 1 root audio    14,   8 2007-04-21 20:47 /dev/sequencer2
crw-rw-rw- 1 root audio 116,  0 2007-04-21 20:47 controlC0
crw-rw-rw- 1 root audio 116, 24 2007-04-21 20:47 pcmC0D0c
crw-rw-rw- 1 root audio 116, 16 2007-04-21 20:47 pcmC0D0p
crw-rw-rw- 1 root audio 116, 25 2007-04-21 20:47 pcmC0D1c
crw-rw-rw- 1 root audio 116, 18 2007-04-21 20:47 pcmC0D2p
crw-rw-rw- 1 root audio 116, 33 2007-04-21 20:47 timer

I know that it shouldn't be necessary. If I put my name in the audio group,
in /etc/group,
I should have permission to read and write those devices. But it hasn't ever
worked, not in the 7 years that I've been running Debian.
So change the permissions, and suddenly you have ALSA and sound.
And alsamixer will suddenly run correctly.

---

### Post by bcasanov on 2007-05-06
Thank you very much orangep for taking the time to share your experience and advice.  > There is a permissions problem involved here.
I was getting:
alsamixer: function snd_ctl_open failed for default: No such device
when I tried to run alsamixer.
 
Go to /dev/snd and
sudo chmod 666 *  
   When I put alsamixer in the command line, I do not get the error you have experienced.  But I have impemented your advice, and I did: cd /dev/snd, then 
sudo chmod 666 *
> Also in /dev, likewise change the modes of all of the audio devices.  I'm sorry, I'm kind of a newbie; I do not know what you mean.  Does that mean to put in the command line "kdesu konqueror" and go to the folder /dev/snd and right-click on each device listed and change their permissions?  In that case, I found for each device that the owner, group and others have permission to read and write, but I do not know what permission to change.
> If you do this:
ls -l /dev/* | grep audio
you should see:  This is the output for my computer: 

crw-rw---- 1 root audio    14,  12 2007-05-06 01:27 /dev/adsp
crw-rw---- 1 root audio    14,   4 2007-05-06 01:27 /dev/audio
crw-rw---- 1 root audio    14,   3 2007-05-06 01:27 /dev/dsp
crw-rw---- 1 root audio    14,   0 2007-05-06 01:27 /dev/mixer
crw-rw---- 1 root audio    10, 135 2007-05-06 01:26 /dev/rtc
crw-rw---- 1 root audio    14,   1 2007-05-06 01:27 /dev/sequencer
crw-rw---- 1 root audio    14,   8 2007-05-06 01:27 /dev/sequencer2
crw-rw-rw- 1 root audio 116, 7 2007-05-06 01:27 controlC0
crw-rw-rw- 1 root audio 116, 6 2007-05-06 01:27 pcmC0D0c
crw-rw-rw- 1 root audio 116, 5 2007-05-06 01:27 pcmC0D0p
crw-rw-rw- 1 root audio 116, 4 2007-05-06 01:27 pcmC0D1c
crw-rw-rw- 1 root audio 116, 3 2007-05-06 01:27 seq
crw-rw-rw- 1 root audio 116, 2 2007-05-06 01:27 timer

> I know that it shouldn't be necessary. If I put my name in the audio group,
in /etc/group, 
I should have permission to read and write those devices. But it hasn't ever
worked, not in the 7 years that I've been running Debian.
So change the permissions, and suddenly you have ALSA and sound.
And alsamixer will suddenly run correctly.  I checked in etc/group and found that my username is listed in the audio group.  I do not know exactly to which file I should change permisssions and which permissions I should change.

Regards,
bcasanov

---

### Post by bcasanov on 2007-05-07
So I take it that my sound issue is not related to a permissions problem?

---

### Post by bcasanov on 2007-05-11
Do any of you know what could be causing this problem?

---

### Post by bcasanov on 2007-05-14
> **anirban.sam said:**
> Type alsamixer in a console and disable all IEC devices. Save alsactl config.

I forgot to ask this fundamental question (stupid me): how do I know which devices are IEC in my alsamixer?

---

### Post by bcasanov on 2007-05-22
I guess I will have to bump this thread, as I have not received  a response for a week.  I really need to solve this sound issue.

---

### Post by knightnet on 2007-05-25
I'm afraid that you have found out the hard way that sound problems are rife in Linux and that they cannot always be resolved.

I'm afraid that you are looking at a rebuild. You could try uninstalling all of the sound packages first and then reinstalling them but it may be easier to reinstall the OS.

I have a problem where I only get sound on my rear speakers and sub-woofer on a specific digital output - I've tried everything to fix this and booting off a live CD works fine so I know it is a setting somewhere. Even following all of the help I've found I can't fix this issue so I am going to have to do a rebuild myself :(

Regards.

---

### Post by bcasanov on 2007-05-25
Yea, I found it out the hard way.  However, just to give a bit of background, I had Linspire installed before, and the sound worked fine, and when I first put in the Ubuntu live CD, the sound worked.  Then I had a sudden weird problem with my hard disk drive, where I could boot from it, [http://ubuntuforums.org/showthread.php?p=2571193&highlight=cannot+boot+from+neither#post2571193](http://ubuntuforums.org/showthread.php?p=2571193&highlight=cannot+boot+from+neither#post2571193), but I got that problem resolved.  The only thing was that, this time, when I put in the Ubuntu live CD, I did not hear any sound, nor when I tried the Kubuntu live CD.  I installed Kubuntu and I still am not hearing any sound.  ](*,)

---

### Post by bcasanov on 2007-07-02
As an update, I found out, interestingly, that I CAN hear sound, but the sound is so low that it is almost muted.  I went to see a youtube video, and just discovered that the sound can actually be heard, but it is very low.  I have all the sound volume meters turned up as high as they can go, yet the sound is almost inaudible.  Another thing I forgot to mention is that my sound speakers are actually attached to the monitor.  It is a Nokia Multigraph 447Za.  On this monitor-speaker, the sound volume meter is set as high as it can go.

---

### Post by bcasanov on 2007-07-21
Hey, I want to inform everyone that I finally fixed my sound problem!  It turns out that it was related to a hard drive problem I was having.  A few weeks ago, I could no longer boot into Kubuntu because my hard drive had so many logical errors.  I went and bought a new internal hard drive, and unfortunately lost all my data. :(   However, when I configured the new drive and booted into it with the live CD, I finally heard sound!  Yippeee!  I then made a fresh install of Kubuntu, and everything works now.

---

