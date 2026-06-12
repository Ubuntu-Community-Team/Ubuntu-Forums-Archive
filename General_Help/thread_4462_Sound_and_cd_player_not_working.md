---
title: "Sound and cd player not working"
date: 2004-11-15
forum: General Help
---

### Post by CAPTAIN RON FL on 2004-11-15
I finally got Ubuntu up!!!!! YEA!!!!  I tried a bunch of live cd's and I liked Ubuntu the best because it found everything except for my wifi card. I burned a copy [two really... first one kept hanging up] and now I have it on my emachine. It is a 433 intel pII, 96mb, 4gb hd, with a cd. The problem is that the sound and the cd player does not work. They worked with the live cd. What gives. Do I need to burn another cd and reinstall or is there another way???  ](*,)  Also How do I get into the command line [I think that is what it is called] to change things.?? I have been reading a lot , but I am lost. This is the first linux distro that I have put on a hard drive. Let the fun begin!!!!! Thanks, Ron

---

### Post by Ozitraveller on 2004-11-15
Yes I'd interested in the answer as well. I have a pII 400, 389mb ram, 2 x 30gb drives, and a std SoundBlaster PCI card, Nvidia 64mb video card.

If I change the sound card, will the OS redetect the new card?

---

### Post by FLeiXiuS on 2004-11-15
You can get to a command terminal by simply right clicking on the 'desktop' then clicking 'open terminal'.

Also, once in the command prompt I'd reccommend setting a root password for more security.  

```
sudo passwd root
```

After this then you can worry about the sound.  Check your mixers to make sure nothing is wrong.  No muted channels or anything.  Click on "Applications" and it should be under the "Multimedia" section if I remembered correctly.  

(sorry I'm at work on XP :-()

IF its still no working, then lets get down and dirty...

Probing for the correct sound card module
```
sudo modprobe emuk101
```

Print some output please, its always helpful.   

If no output is displayed, check your sound / audio mixers.

---

### Post by Crisp on 2004-11-15
I'm having the exact same problem.  Sound is fine on the LiveCD but not on the install.  Firstly, here is my lspci:

```

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:06.0 Communication controller: Intel Corp. 536EP Data Fax Modem
0000:01:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:01:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
0000:03:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

```

It's clear that there is probably a conflict between the onboard sound and the pci soundcard.  I turned off the onboard sound in BIOS but it made no difference.  I installed the nvidia audio drivers from their site, but again nothing happened.  Actually something happened, before in Volume Control I got the following 4 tabs:

[i]RealTek ALC650 rev 3 [OSS Mixer]
CMedia PCI [OSS Mixer]
NVidia nForce2 [Alsa Mixer]
C-Media PCI CMI8738 [Alsa Mixer][/i]

But now I have these 2:

[i]NFORCE AUDIO [OSS Mixer]
C-Media PCI CMI8738 [Alsa Mixer][/i]

I take it I want to be using the Alsa mixer.   I've wondered about taking my pci card out too, but I'm not convinced that would work if disabling my onboard sound device did nothing.  I'm willing to try it as a last resort though, but it's a bit of a mission to do, just because of how tucked away my computer is.

I've checked that all the volume levels and whatnot are full, and nothing is on mute etc.  This is system wide silence too, not just application specific.  Any help?

-Crisp

---

### Post by CAPTAIN RON FL on 2004-11-15
OK .I did the modprobe emu10k1. I got back warning: error inserting ac97_codec (/lib/modules/2.6.8.1-386/kernel/sound/oss/ac97_codec.ko): operation not permited . What does that mean and how do I fix it? Thanks, Ron
 ARE WE HAVING FUN YET :grin:  I KNOW I AM :grin:  THIS STUFF IS GREAT :grin:

---

### Post by Ozitraveller on 2004-11-16
Hi this is what I got:


WARNING: Error inserting ac97_codec (/lib/modules/2.6.8.1-3-386/kernel/sound/oss/ac97_codec.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.8.1-3-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting sound (/lib/modules/2.6.8.1-3-386/kernel/sound/oss/sound.ko): Operation not permitted
FATAL: Error inserting emu10k1 (/lib/modules/2.6.8.1-3-386/kernel/sound/oss/emu10k1/emu10k1.ko): Operation not permitted

---

### Post by Rodney on 2004-11-16
If you did > sudo passwd root 
you need to type " su "    minus the quotes, hit enter
then your password
then I would type " alsaconf "  hit enter
after it has found your soundcard type " alsamixer "  hit enter
set your levels using the m key to un-mute and the up/down arrows for volume levels
once your happy type " alsactl store " hit enter
this will save your settings

---

### Post by FLeiXiuS on 2004-11-16
Sorry about that, it would be: 

```
sudo modprobe emu10k1
```

---

### Post by Danrarbc on 2004-11-16
I've had a sound issue installing with the install disc. It's a permissions issue, sound works as root but not as normal user. I know how to fix that though, I've done it before, so it's not a big deal.

It's the oddest thing :-s



Beyond that I'm loving Ubuntu. I can see this being my favorite distro, I've tried Red Hat, Fedora, Gentoo, and Arch.

---

### Post by Crisp on 2004-11-16
root@benson:/home/crisp # modprobe emuk101
FATAL: Module emuk101 not found.


Hrm that doesn't look good.  Since sound works with the LiveCD but not on install, are there any relevant config files that I could copy from the live CD to the hdd?  Anyway, still no sound :(

-Crisp

---

### Post by TravisNewman on 2004-11-16
[QUOTE=Crisp]root@benson:/home/crisp # modprobe emuk101
FATAL: Module emuk101 not found.


Hrm that doesn't look good.  Since sound works with the LiveCD but not on install, are there any relevant config files that I could copy from the live CD to the hdd?  Anyway, still no sound :(

-Crisp[/QUOTE]
 You misspelled it. It's emu10k1, not emuk101

---

### Post by Crisp on 2004-11-16
Oh right, looks like Flexius got it wrong twice :)  Reglardless, the new output:

```

crisp@benson:~ $ su
Password:
root@benson:/home/crisp # modprobe emu10k1
root@benson:/home/crisp #

```

So zero output.  And yes I've run alsamixer and made sure all bars are full and unmuted.  Althogh my volume control now has 2 tabs which read, in order:

[i]NFORCE AUDIO [OSS Mixer]
C-Media PCI CMI8738 [Alsa Mixer][/i]

I'm not sure if the order of the tabs is relevent, but if they are then it looks like OSS Mixer is coming first, when I've only configured Alsa Mixer.  But I don't know how to configure OSS Mixer, plus I believe it's redundant now.

-Crisp

---

### Post by FLeiXiuS on 2004-11-16
[QUOTE=Crisp]Oh right, looks like Flexius got it wrong twice :)  Reglardless, the new output:
[/QUOTE]

Sorry about that, I meant emu10k1..it was just a quick typo.

---

### Post by CAPTAIN RON FL on 2004-11-16
OK : I this is what I did

I typed " alsaconf " and got command not found.

I typed " alsamixer ". It open the mixer control. 
The Master was at62; Master Mono was at off; Headphones 71; The first two 3D Control were set at 0; the next 3D Control was set at off ; PCM was set at 71 ; Line was set at off.
Do I need to change any of these? Also how do I change something from off to on? I tried the controls and could not get them to change to on. The volume slides work OK. 
After I did that, I typed " alsactl store" and got alsactl: save_state:1088: Cannot open /var/lib/alsa/asound.state for writing. So , I guess these things did not get saved. How do I go about saving them?

 Also on start up I noticed, failure in PCIEHP andSHPCHP. Could these things have anything to do with it?

Thanks, Ron

---

### Post by CAPTAIN RON FL on 2004-11-16
OK; I finally got sound to work somewhat. Now I need help with the cd player. It starts to play then stops. I hear about a second of sound. I tried to get it to go to another track. It would start to play that track. Then it would go back to the first track with no sound. Can some one help me figure this out. Thanks, Ron

---

### Post by CAPTAIN RON FL on 2004-11-21
Hey just wanted to let everyone know that sound and cd problem was fixed by uninstalling Ubuntu and then reinstalling it. Seems Everything was fixed in the updates. Thanks, Ron :D

---

### Post by Crisp on 2004-11-21
Shame, my sound is still non existent, and worked on the LiveCD.  I'm too busy to put in much effort trying to fix it now though, so it's something I'll have to live without for a while.
 
 -Crisp

---

