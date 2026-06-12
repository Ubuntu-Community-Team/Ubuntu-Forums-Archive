---
title: "Disabling one of multiple sound cards"
date: 2008-01-27
forum: General Help
---

### Post by jeremysan on 2008-01-27
Hi all.
I recently installed Ubuntu to find that it cannot use my sound card, thus I have no sound.
The problem for me is that my computer has two sound cards: an integrated one which came with my computer when I got it, and a newer PCI sound card, which I bought for use with games and other things with my Windows XP (I have dual boot on this computer).
Before I installed my newer sound card, sound in Ubuntu worked perfectly fine; there was no problem with the integrated sound card.  However, once I had installed the new PCI sound card, it turns out that it is incompatible with Ubuntu.  
Right now, the only way for me to be able to have sound in Ubuntu is to physically remove the sound card from the PCI slot, and when I boot up Ubuntu there is sound; it uses my integrated sound card.  
However, I don't want to do that.  I want to be able to leave the sound card installed, so that I don't have to keep taking it out and putting it back in when I boot up Windows XP...  that just isn't a proper thing to do.

What I want is to be able to disable my PCI sound card in Ubuntu, which is obviously the dominant one that Ubuntu tries to use, yet cannot because it is incompatible.  That way, Ubuntu could use my old sound card and simply ignore my PCI one, and I could have sound.

So:  at this point, anyone of any help will at least need some information, so I will provide all that I can.

Firstly, I cannot change any sound settings.  The volume icon in the top right-hand corner of my screen has a red "restricted" type symbol on it.
     [IMG]http://i240.photobucket.com/albums/ff258/jergsan/VolumeIcon.jpg[/IMG]
And when I try to go to preferences or volume control, I am stopped by this message:     [IMG]http://i240.photobucket.com/albums/ff258/jergsan/Screenshot-gnome-volume-control.png[/IMG]

Next, I cannot find the name of my integrated card on ALSA.  
The model number of my computer is HP m1095c, searching that term into Google brings me to the link on HP's website which gives me specifications of my computer, which, for the sound card are as follows:


Sound
Integrated Intel High Definition(TM) audio (Azalia)

    * Realtek ALC 880 chipset
    * THX certification support
    * 8-channels for Full Dolby 5.1/6.1/7.1 surround sound support with Dolby Pro Logic IIx

From that information given, I cannot find the card on ALSA, although the card does work with Ubuntu.
When I type "lspci -v" into my terminal, here is the output:





jeremy@jeremy-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
        Subsystem: Hewlett-Packard Company Unknown device 2a08
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: c7f00000-c7ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at b480 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at b800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at b880 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at bc00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at c7effc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: c8000000-cfffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at b400 [size=8]
        I/O ports at b080 [size=4]
        I/O ports at b000 [size=8]
        I/O ports at ac00 [size=4]
        I/O ports at a880 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 2a0a
        Flags: medium devsel, IRQ 5
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0b12
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c7fe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at c000 [size=256]
        Expansion ROM at c7fc0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0b13
        Flags: bus master, fast devsel, latency 0
        Memory at c7ff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a0c
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at cffff800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a0b
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at e800 [size=256]
        Memory at cffff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: ASUSTeK Computer Inc. ASUS PVR-416
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at cd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

03:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: ASUSTeK Computer Inc. ASUS PVR-416
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

03:05.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs X-Fi Platinum
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at e480 [size=32]
        Memory at cfc00000 (64-bit, non-prefetchable) [size=2M]
        Memory at c8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>






I think that is all of the information I can provide.  I apologize for making this post so long, and I am thankful if you took the time to read it.

All I want to do is disable my Creative SB X-Fi sound card (my PCI one), or simply get my sound working any other way.  Any knowledge or information would be greatly appreciated.  Please help

---

### Post by DarkStarAeon on 2008-01-27
I'm half asleep, so don't expect much out of me, but I'll take a stab at this...

Go into your BIOS and find the part about sound devices,  then try disabling the sound device you don't want.

If that doesn't work all by itself, then go back to where you were earlier:

System > Preferences > Sound

then where it says "Default Mixer Tracks" click the "Device" drop down and see if the sound device you want to use is listed there after having changed the BIOS setting for sound device.

By the way, the "Auto" setting for sound devices in BIOS never works well for me. I disabled my onboard audio there completely and just use my Audigy 4 sound card I installed.

Like I said, I'm tired, I could be wrong, but hopefully that helps.

---

### Post by hahahan on 2008-01-27
I tried a similar thing once but it appeared that once Linux is up and running CMOS settings didn't switch off the device, it was still present.

---

### Post by shadyedsan on 2008-01-27
try this, type this in in a terminal:

less /proc/asound/modules

That will show you which soundcards occupy which slot and what their names are.

output should be something like this (if you have more than one sound device)

0 snd_au8830
1 snd_intel8x0


Now identify which cards you don't want to use and take their names.

In terminal now type

sudo gedit /etc/modprobe.d/alsa-base

Find the place where it says something like
# Prevent abnormal drivers from grabbing index 0
and in the list below add
options snd_whateveryourcardnameswere index=-2

Since you have more than one card you want to blacklist, you put in the lines of every card you dont want.

Now save /etc/modprobe.d/alsa-base and reboot the computer. It *should* now set the "wrong" sound cards to slot -2 (making them disabled) and the correct soundcard should grab slot 0 and work.

please post back the results :KS

---

### Post by shadyedsan on 2008-01-27
> **shadyedsan said:**
> try this, type this in in a terminal:

less /proc/asound/modules

That will show you which soundcards occupy which slot and what their names are.

output should be something like this (if you have more than one sound device)

0 snd_au8830
1 snd_intel8x0


Now identify which cards you don't want to use and take their names.

In terminal now type

sudo gedit /etc/modprobe.d/alsa-base

Find the place where it says something like
# Prevent abnormal drivers from grabbing index 0
and in the list below add
options snd_whateveryourcardnameswere index=-2

Since you have more than one card you want to blacklist, you put in the lines of every card you dont want.

Now save /etc/modprobe.d/alsa-base and reboot the computer. It *should* now set the "wrong" sound cards to slot -2 (making them disabled) and the correct soundcard should grab slot 0 and work.

please post back the results :KS

forgot to mention, the names may appear either 1 snd-intel8x0 or 1 snd_intel8x0 (note the underslash)

---

### Post by jeremysan on 2008-01-27
shadyedsan:

Well, as much as I appreciate your help, I ran unto a few problems.:(
First problem:  When I put "less /proc/asound/modules" into my terminal, my result is:

jeremy@jeremy-desktop:~$ less /proc/asound/modules
/proc/asound/modules: No such file or directory


So, although that didn't work. I simply went on to the next step, hoping that I could still possibly figure out the name that I wanted to blacklist.
However, I ran into another problem:  in the alsa-base file, the index value for every sound card is already -2::x


# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2


So unfortunately, atleast as far as I can see, nothing here will work at the moment.

---

### Post by shadyedsan on 2008-01-27
ok, have you got all the alsa plugins installed, including esound?

you should be able to open the less /proc/asound/modules file ok from a terminal

the alsa-base file might be ok, choose the card from which you want to have sound work as the default and replace the -2 for a 0 and keep all the rest -2

---

### Post by shadyedsan on 2008-01-27
> **shadyedsan said:**
> ok, have you got all the alsa plugins installed, including esound?

you should be able to open the less /proc/asound/modules file ok from a terminal

the alsa-base file might be ok, choose the card from which you want to have sound work as the default and replace the -2 for a 0 and keep all the rest -2

does the directory /proc/asound exist on your system as a matter of interest?

---

### Post by shadyedsan on 2008-01-27
> **shadyedsan said:**
> ok, have you got all the alsa plugins installed, including esound?

you should be able to open the less /proc/asound/modules file ok from a terminal

the alsa-base file might be ok, choose the card from which you want to have sound work as the default and replace the -2 for a 0 and keep all the rest -2

"the alsa-base file might be ok, choose the card from which you want to have sound work as the default and replace the -2 for a 0 and keep all the rest -2" - ignore that bit please!! i just relised that can't work, the card you want to use mustn't be listed in the list - i'm such a dummy :(

---

### Post by jeremysan on 2008-01-27
> **shadyedsan said:**
> ok, have you got all the alsa plugins installed, including esound?

you should be able to open the less /proc/asound/modules file ok from a terminal



Um, I don't believe I had, although I opened Synaptic package manager and installed everything beginning with ALSA, and then proceeded to install esound.
I now have them installed.


> **shadyedsan said:**
> does the directory /proc/asound exist on your system as a matter of interest?

No it does not.

---

### Post by shadyedsan on 2008-01-27
does the following command work?

sudo gedit /etc/modprobe.d/alsa-base

if it does, then where it says something like # Prevent abnormal drivers from grabbing index 0, make sure your card[COLOR="Red"] ISNT[/COLOR] listed and that all other cards are marked index=-2

save the file and restart your computer.

i can't understand why you don't have the /proc/asound directory though. another way to list sound devices would be to type in a terminal:

aplay --list-devices

if sound still doesn't work, try installing and running asoundconf-gtk in a terminal window and select the card you want sound to come from.

there may be hardware problems if sound still doesn't work or another underlying problem for which i do not know.

please post back your results :)

---

### Post by jeremysan on 2008-01-27
> **shadyedsan said:**
> does the following command work?

sudo gedit /etc/modprobe.d/alsa-base

if it does, then where it says something like # Prevent abnormal drivers from grabbing index 0, make sure your card[COLOR="Red"] ISNT[/COLOR] listed and that all other cards are marked index=-2

save the file and restart your computer.

i can't understand why you don't have the /proc/asound directory though. another way to list sound devices would be to type in a terminal:

aplay --list-devices

if sound still doesn't work, try installing and running asoundconf-gtk in a terminal window and select the card you want sound to come from.

there may be hardware problems if sound still doesn't work or another underlying problem for which i do not know.

please post back your results :)


Okay.  The first command worked and I was able to remove a line which I thought was the one that I wanted.  However, upon restarting my computer, I find that there is no apparent changes; what I deleted has done nothing.

The next line also apparently doesn't work;

```
jeremy@jeremy-desktop:~$ aplay --list-devices
aplay: device_list:204: no soundcards found...
```

and lastly, with Synaptic I installed asoundconf-gtk, and it showed up in System --> Preferences --> Default Sound Card.
However, when I run that program, I see it at the bottom of my screen "Starting Default Sou.."  And after about 20 seconds it just disappears, as though the program was unable to start.


I'm simply beginning to think that as long as this Creative PCI sound card is in my computer, Ubuntu will be unable to work with sound, as this sound card is incompatible with it.  If you have any other suggestions or ideas, feel free, but don't worry yourself over my problem.

---

### Post by shadyedsan on 2008-01-28
it appears that quite a few others are experiencing sound issues with this soundcard. some fixes work better than others and some don't work at all. try looking in some other linux forums or even the creative labs website, maybe there are updated drivers you could install for the card to work properly in gnu/linux.

sorry i couldn't be of more assistance. good luck in finding your solution.

---

