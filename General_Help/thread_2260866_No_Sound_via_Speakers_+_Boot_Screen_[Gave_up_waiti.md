---
title: "No Sound via Speakers + Boot Screen [Gave up waiting for root device]"
date: 2015-01-14
forum: General Help
---

### Post by Lightning Dragon on 2015-01-14
Hello,

So after not being able to boot into Ubuntu for some time now, I decided to just suck it up and lose all my data on my Ubuntu try and install fresh. I now have Ubuntu 14.04 LTS installed and working fine. Everything was running smooth. I could play music through my speakers and case headphone jack, edit files and boot into the computer just fine (which, by the way, [I fixed that annoying problem with in this thread!]("http://ubuntuforums.org/showthread.php?t=2203177") yay!).  Ubuntu then began updating. I restarted after it was all done and noticed two things:


[LIST=1]
[*]Speakers would not work but the audio jack on the case does (works in Windows 7). 
[*]Upon booting, [I get this screen]("http://s7.postimg.org/5at8t4miz/boot.jpg"). Type "exit" to get out of it and about 60 seconds later, it boots into Ubuntu. 
[/LIST]

So I ran BootRepair once again and it gave me a whole bunch of commands to run into the Terminal, which I did and they reported to work as intended, until the end of the bootrepair gave me the instructions of:

[IMG]http://s3.postimg.org/lbcebtysz/Screenshot_from_2015_01_14_18_27_11.png[/IMG]

(to be clear: I get a menu to select which OS to install and booting actually works)

 I ran sudo blkid and got this:

/dev/sda1: UUID="5263-5DAA" TYPE="vfat" 
_**/dev/sda2: UUID="4b155022-74d0-409c-97ae-fbb8827deb0b" TYPE="ext4"**_ (drive it reports in boot)
/dev/sda3: UUID="e25ccd0b-5fa3-4212-ad90-07d477583371" TYPE="swap" 
/dev/sdb1: UUID="641C-3B35" TYPE="vfat" 
/dev/sdb3: UUID="AA941EAA941E78D1" TYPE="ntfs"

I do not dual boot with Windows 8, but to be sure, I went and disabled Windows 8 features and fast boot options in the BIOS. Did not fix it. I also tried editing bootdelay, did nothing. I have no idea how to begin on the instructions in the image. Any help?

[CENTER]** :OTHER PROBLEM:**
[/CENTER]

As for audio, I installed pavucontrol to see if it was picking up my speakers etc. It reported a lot of the stuff as "unplugged" but I can guarantee that it is all plugged in currently. Some outputs:

```
LD@Ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
LD@Ubuntu:~$ uname -a
Linux Ubuntu 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```
LD@Ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k3.13.0-44-generic.
```

```
LD@Ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Intel Haswell HDMI

==> /proc/asound/card1/codec#0 <==
Codec: Realtek ALC892
```

Thanks for reading!

[SIZE=1]_**P.S**_

I installed Ubuntu 14.04 LTS on my mother's computer for her, dual boot with Windows 8, and cannot get her resolution to work correctly. If anyone can point me towards a solution for that too, that would be awesome. Her computer uses integrated graphics, Intel HD 2500 (i3 in it) if that helps.[/SIZE]

---

### Post by Lightning Dragon on 2015-01-18
UPDATE;

Booting into Windows first seems to fix the Ubuntu error upon restart. However, it persists if the first boot is Ubuntu. I have to type exist and wait nearly two minutes for it to boot into the machine. Anyone have anything to suggest me to try, or how I go about the instructions Boot-repair gave me?

As for the audio, I managed to fix it. I uninstalled pulseaudio, purged its contents, rebooted and reinstalled, rebooted and used pavucontrol to fix the speakers not working. Hopefully the next update won't break them again. lol

As always, any and all help would be welcomed. :)

Thanks!

---

