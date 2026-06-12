---
title: "toshiba laptop no sound i have done everything i can find"
date: 2008-01-05
forum: General Help
---

### Post by lninjo on 2008-01-05
i have a toshiba laptop a135-4487 and it recognizes my sound card as a intel hd it also recognizes realtek analog modem sound card i have done everything in the forums i could find is there anyone out there that can help me get this fixed. and thanks for all of those who spend there time helping people through there problems here at ubuntu forums. I am really impressed with the courtesy and i am proud to be apart of the community.:):):confused:

---

### Post by balaknair on 2008-01-05
Hi
Could you please enter the following commands in a terminal and copy-paste the output
```
aplay -l
```
```
lspci -v
```

To open a terminal just go the menu applications> system> terminal

---

### Post by balaknair on 2008-01-05
if you have an intel hda card, these steps might help

open a terminal and enter the following command
```
cat /proc/asound/card0/codec#* | grep Codec
```

this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A
Next find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

(the alsa-config should also be on your system at usr/src/(your kernel version)/sound/alsa/alsa-configuration.txt)

in that page find your card model and check the details given
eg
```
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)

```
select the description that best matches your system(eg a 5.1 surround system with 6 audio-out channels/ports would be 6stack)

then go back to the terminal and type
```
sudo nano /etc/modprobe.d/alsa-base
```

Paste this into the last line of the file
```
options snd-hda-intel model=MODEL

```
replace MODEL with your model(6stack, 3stack, laptop etc.)

reboot.

if this doesn't work you might have to consider recompiling the alsa-kernel(though if you followed the ubuntuforums guide above I guess you've already tried it.
These steps are just a part of the howto guide at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If it works please post a reply and mark the thread as solved.
Lotsa luck

---

### Post by lisati on 2008-01-05
I have a Toshiba A100 laptop which had no sound when I first installed Ubuntu 7.04 - installing the available updates, rebooting, and setting the Ubuntu volume control seemed to do the trick. 

p.s. I'm not sure if that will work with newer versions of Ubuntu.

---

### Post by lninjo on 2008-01-05
here is my information



ard 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Codec: Realtek ALC861-VD
Codec: Generic 11c1 Si3054
l
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lninjox@lninjox-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC861-VD
Codec: Generic 11c1 Si3054
lninjox@lninjox-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
        Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 8c000000-8ffff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 20
        Memory at dc005800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by lninjo on 2008-01-05
i did everything you stated and still no sound i appreciate your help what do you think i should do next?

---

### Post by balaknair on 2008-01-05
Sorry for the delay in replying.
Checked the alsa-project.org site and the module you need is indeed snd-hda-intel. So this is what worked for me with the same card(not on a laptop though that shouldn't be too significant)
Sound may just be muted so you should try adjusting volume before trying anything else.
Open alsamixer by typing [#]alsamixer[/#] in a terminal, and adjust the volume settings.

If nothing works I suggest you try recompiling the alsa kernel from source. These steps are what worked for me and a few others with the intel hda cards, in ubuntu, mandriva and pclinuxos.
Did you try [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) yet?
You'll find detailed steps on how to recompile the alsa kernel here(the latest stable version of alsa is 1.0.15, i would suggest trying 1.0.14(I had a few issues with 1.0.15- ubuntu 7.10 refused to load the snd-hda-intel module, but 1.0.14 worked fine, not sure why that is)

And oh yes one more thing-

---

### Post by lninjo on 2008-01-05
i will do that now, another question in my hardware information it say the sound is disabled and needs configured how do you do that i checked the forums but it seems the instructions arent working for me thanks for the patience for the noob

---

### Post by balaknair on 2008-01-05
I'm not sure about just what you mean by hadware information, so I can't really offer an opinion about that(I'm a noob myself), but I'm assuming the improper configuration is what we're trying to fix.
Once you finish with the above steps(adjust volume, if that doesn't work recompile ALSA), do let me know how it went.
All the best.

---

### Post by lninjo on 2008-01-05
i sure will 

im talking about the hardware information under settings>hardware information
im using the kde enviroment but its still ubuntu
ive tried uninstalling and reinstalling no go
ive been on this issue for 2 days and i wont quit intill its finished
im tempted to uninstall and reinstall the os but i spent alot of time building my enviroment
im trying to compile the alsa lib tar ball now
and after all this i still love my ubuntu
funny thing is i bought this laptop for vista
so i got vista on one side and ubuntu on the other
if i can get my ubuntu side to work only time i will have to go to vista
is to write programs with visual studio
i cant wait to get out of school and get rid of microshit forever
i will get back with you soon 
my email is [email]lamarjohnsonwichita@gmail.com[/email]

---

### Post by lninjo on 2008-01-05
ooh and the volume ive tried that a million times already sound works in vista and xp with virtual machine but no ubuntu

everyother computer in my house runs linux and all sounds work except the newest computer which is this one wierd...

---

### Post by lninjo on 2008-01-05
and for your help i will help others what a great community huh 
if life was this way there would never be poverty take what you need and give what you can

---

### Post by lninjo on 2008-01-05
i did everything you suggested 
now it doesnt recognize the soundcard 
and the alsamixer crashes when try and open
tried uninstall and reinstall of alsa mixer
now will try uninstall and reinstall of alsa

---

### Post by balaknair on 2008-01-05
the easiest way to dump alsa and recompile is by using the terminal
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

this will remove alsa completely and reinstall from the ubuntu repositories

then try the modprobe steps


I know just how frustrating it can be- I had the same issues, nothing I tried for sound seemed to work, and I'd just managed to get everything else configured to my liking, and didn't want to mess that up. took me almost 8 hours but finally it was modprobe which worked for me(though it didn't seem to work at first) after God knows how many reboots later somehow got sound working(but it was worth it, Kubuntu is the best distro I've tried(and I've tried Fedora 8, Mandriva 2008, OpenSuse 10.3, PCLinuxOS, Sabayon- all had trouble with my sound card) and Amarok is the only way I listen to music now- sounds great now).


And yeah, the Ubuntu community really is pretty great(I've tried the Mandriva, OpenSuse, Fedora, Gentoo forums- except for Mandriva forums, the rest seem to be made up largely of very busy expert Linux users with little time for noobs, Gentoo guys actually seemed hostile to noobs- just my personal experience). It's the best 'feature' of Ubuntu- acommunity that lives up to the meaning of 'Ubuntu'.
So I hope that you'll be able to fix your sound problems soon( and will be able to others with similar issues)

---

### Post by lninjo on 2008-01-06
well what i did was try and upgrade to 7.10 but lost all my beryl functionality so i went ahead and reinstalled 7.04. Ive spent most of the night trying to get my settings and features back to where i had them not counting my files. I will try again tomorrow on this issue so i can call it solved thanks again for your help..:)

---

### Post by [L2G] Slapshot on 2008-01-06
Hi Ininjo

If all else fails to get sound then as a last resort you could try this thread out rather than ditch Linux on this machine. It helped me after weeks of trying to get sound on a friends laptop. It ditches Alsa and uses OSS. OSS seems to support more of the newer HDA sound cards at the moment. Rather than go back to Windows you could try OSS and then when Alsa fix their problems with these cards you can maybe switch back to Alsa. The link is here.


[http://ubuntuforums.org/showpost.php?p=3768914]("http://ubuntuforums.org/showpost.php?p=3768914")

Hope this helps if you don't get anywhere with Alsa.

Slap

---

### Post by balaknair on 2008-01-06
OK buddy
Hope you have better luck in Feisty(I had a much easier time with sound in Feisty, but video card (nVidia Geforce8) issues led to major X11 problems, tried fixing it, made things worse, and in the end corrupted the root partition(I think it had something to do with improperly restoring the xorg.conf file) so finally just formatted the partition and installed Gutsy on the second HDD. Video was no problem with Gutsy(just enable proprietary drivers and everything worked) but audio was a big headache.
You could try mailing me [email]balaknair@gmail.com[/email], I'll help in whatever way I can when I get back from work tomorrow.
Wishing you luck

---

### Post by lninjo on 2008-01-10
ok its the weekend and im gonna go back at it i will let you know where im at. Im gonna try and uninstall alsa reinstall it again. If that doesnt work i will uninstall and try install the oss module wish me good luck

---

### Post by [L2G] Slapshot on 2008-01-11
Good luck m8, hope you get some form of working sound this weekend.

Slap

---

### Post by lninjo on 2008-01-21
i have come to the conclusion its unattainable with my system intill maybe theres an update i have sent email to the support team to see if we can get a fix. I have ubuntu on one partition, windows xp on another and windows vista on its own so i will be ok for awhile. but i will keep this post updated for those who are going through similiar issues. oh yea triple boot was a pain but it is worth it. and dont buy vista its not worth it

---

### Post by lninjo on 2008-01-21
toshiba a135-s447

---

