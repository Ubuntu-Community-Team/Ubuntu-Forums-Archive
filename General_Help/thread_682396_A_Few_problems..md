---
title: "A Few problems."
date: 2008-01-30
forum: General Help
---

### Post by drkie18 on 2008-01-30
Hey guys.
I just recently got a laptop from a friend a while back, and finally got a around to messing around with it. I was fed up with Windows XP and decided to branch off into a new OS. I picked Ubuntu. Great stuff. I have a few problems though..

Anyways. he gave me
 an old IBM Thinkpad 600E.
54 Gig HD.
Pentium 2 Pros. (Runs Ubuntu fast somehow)

Prob. 1
I tried using Compix, and well when i went into Appearance and tried Normal Visual Effects, it says it cannot display.

As i read around, i found out that when i typed *glxinfo * in terminal i get the crappy message of "Unable to open display".

What do i do???


Prob.2
I cannot open Terminal from desktop. I have to use the ctrl+Alt+F1 Command. When i click Terminal from the menu, it says loading o nthe taskbar and then it just disappears.

Prob.3
Volume does not work. Nothing much to say..

Prob.4
When i try to play a CD i get an error message of "could not open source for writing"


Thats it for now. Any help guys???

---

### Post by doddo on 2008-01-30
> **drkie18 said:**
> 
Prob. 1
I tried using Compix, and well when i went into Appearance and tried Normal Visual Effects, it says it cannot display.

As i read around, i found out that when i typed *glxinfo * in terminal i get the crappy message of "Unable to open display".

What do i do???

This issue is connected to the not able to launch terminal problem ur facing.Try to fix the gnome terminal emulator and launch glxinfo from there!
> 
Prob.2
I cannot open Terminal from desktop. I have to use the ctrl+Alt+F1 Command. When i click Terminal from the menu, it says loading o nthe taskbar and then it just disappears.

Thats really strange! Can u make a launcher with xterm in it and see if that works?
> 
Prob.3
Volume does not work. Nothing much to say..

Have u tried alsamixer or something. Is the sound module loaded properly? Are u able to play sound?
> 
Prob.4
When i try to play a CD i get an error message of "could not open source for writing"

Thats strange!  Sounds as if it thinks ur trying to write to the cd
What program do u use to play the CD? Is it an audio cd ur trying to play?

---

### Post by drkie18 on 2008-01-31
I reinstalled last night Ubuntu entirely.
Got terminal to load.

Volume still does not work. When i click "open volume Control"  I get
"No volume control GStreamer plusgins and/or devices found.:"
I know the sound card is working, i had XP on it about 3 days ago and was listening to music.

Also. Compiz doesnt work either. It is now detecting my Display. When i type Xompiz into the terminal i get:
""Checking for XGL: not present
No whitelisted driver found.
aborting and using fallback: /usr/bin/metacity"
I tried going into and install Xserver-xgl, but i could not find it in the list.

thanks for the help.

---

### Post by jan quark on 2008-01-31
first enable all sources 

go to the sources window somewhere in the menu you will find it
and select all except the last ones source code and cd

then reload and try to find xserver-xgl again in the synaptic

---

### Post by pointone on 2008-01-31
That's a fairly old machine you're running on. The video card probably won't support Compiz, and if it does, it certainly won't perform too well. I'd also wager the machine is a bit on the light side RAM-wise. You might get better results running a less resource-intensive window manager like Fluxbox or Xfce. Try giving Xubuntu a shot, perhaps?

---

### Post by drkie18 on 2008-01-31
I was originally going to set up Xubuntu, but i thought maybe i can squzze around with Ubuntu. Should i move to Xubuntu? Would you reccomend that?

---

### Post by doddo on 2008-02-01
You can try out xubuntus window manager withourt having to reinstall ur box.

Just open up that terminal of yours and install xubuntu desktop either with apt-get or aptitude

or you could install it via synaptic aswell 

And regarding your sound issues.
Could you attach the output of "lspci -v", and " ls /dev/snd/"

---

### Post by drkie18 on 2008-02-04
Sorry for the delay.
I installed Xubuntu and ran the codes Via terminal.

```
jason@Xubuntu:~$ ls /dev/snd
seq timer 
```
 
```
jason@Xubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at 40000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 168
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=176
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: 70000000-dfffffff
        Prefetchable memory behind bridge: e0000000-f7ffffff
00:02.0 CardBus bridge: Texas Instruments PCI1251A
        Subsystem: IBM Unknown device 00eb
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50102000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10000000-13fff000 (prefetchable)
        Memory window 1: 14000000-17fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001
00:02.1 CardBus bridge: Texas Instruments PCI1251A
        Subsystem: IBM Unknown device 00eb
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 18000000-1bfff000 (prefetchable)
        Memory window 1: 1c000000-1ffff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001
00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM CS4610 SoundFusion Audio Accelerator
        Flags: medium devsel, IRQ 11
        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
        Memory at 50000000 (32-bit, non-prefetchable) [size=1M]
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 48
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fcf0 [size=16]
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 48, IRQ 11
        I/O ports at 8400 [size=32]
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad 570
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=16M]
        Memory at 70000000 (32-bit, non-prefetchable) [size=4M]
        Memory at 70400000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

```

---

### Post by drkie18 on 2008-02-04
Im not getting anywheres with this.
I have an old laptop with only a dialup connection port, no friends have Dialup anymore. They all have either Cable or DSL.
I have DSL, and that makes it impossible for this computer to get online without going out to buy a expensive piece of equipment just toget a damn OS working. Not worth it.
Ubuntu in general isnt "easy" as they say it is. You need one thing, your gonna need another, and it very dependant on other things. That is what has me all worked up. Dont have one thing, your screwed..

Is there any possible way to get this damn thing to work or am i screwed? 

What do i do next? Im wasting my sleep on this, havent gotten any at all. Staying up surfing looking for answers, when i find one. Oh look i need this, then i need this and that, and that and this.
Very unreliable.

---

