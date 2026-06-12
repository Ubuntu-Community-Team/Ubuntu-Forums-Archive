---
title: "Bios Screen is Black"
date: 2012-11-21
forum: General Help
---

### Post by MikeT23 on 2012-11-21
When I boot my computer, the Gigabyte motherboard screen shows in the wrong resolution so that much of the information is off the screen. If I press Del at this time the boot stops and instead of the BIOS settings I have a completely black screen. If I allow the boot to continue, the screen shows normally & correctly.

How can I change the initial screen resolution and be able to see the BIOS settings - can anyone help?

My system is:
intel HD graphics 4000
HDMI connection to a TV
Kubuuntu 12.04.

/etc/default/grub:
```
#GRUB_GFXPAYLOAD_LINUX=1280x720
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_DEFAULT=2
GRUB_HIDDEN_TIMEOUT=0
GRUB_GFXMODE=1280x720
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by Bashing-om on 2012-11-21
MikeT23; Hi !

As the graphics are bad BEfore an operating system is loaded, and good when the operating system is loaded, that to me indicates the problem is related to bios.
As you can not get the bios screen by keyboard, I suggest that you reset bios to factory defaults.
On my desktop machines I can do this in 2 manners; 1) remove the motherboard's battery for a few seconds (minutes wont hurt). 2) I have a jumper pin for cmos I can pull and replace to effect the reversion to factory defaults.

Consult your manual or google your mother board.

If you have a lap top, I expect pulling the battery would have the same affect. (but I do not know this - I have never had to do so on our lappies).

[INDENT]good luck <== BDQ

[/INDENT]

---

### Post by elliotn on 2012-11-21
BIOS have nothing to do with your OS....take the advice above and reset BIOS

---

### Post by coldcritter64 on 2012-11-21
> **Bashing-om said:**
> ...If you have a lap top, I expect pulling the battery would have the same affect. (but I do not know this - I have never had to do so on our lappies)....
I don't *think* that is correct, I used to run a Acer laptop without the battery and on mains power only. That system would maintain it's time etc. when powered off. I'm pretty sure that laptops also have a cmos battery.

I also agree with a BIOS reset in this case, with the problem existing before an OS is loaded.

---

### Post by gnusci on 2012-11-21
BIOS hard reset as our fellas just have said.

---

### Post by MikeT23 on 2012-11-28
Thanks for taking the time to provide advice. Unfortunately I don't think it's right. Since then I've had a (separate) complete nightmare with the PC & reinstalled Kubuntu from scratch. I'm now back where I was with the OS and I have more info:

1) When the LCD screen is a DVI connection:
  - screen is identified by xrandr as HDMI1
  - screen size is correctly set to max size before & after boot
  - BIOS shows ok
  - sound plays ok through Analogue Stereo o/p

2) When the screens are a DVI connection (LCD) and HDMI (TV):
  - screens are identified by xrandr as HDMI1 & HDMI2 (in that order)
  - screen size is set to min size 640x480 before & after boot (but can be changed). screen does not quite fit on TV (may be a TV issue)
  - BIOS page is black on both screens
  - sound plays ok through Analogue Stereo o/p or through HDMI. The option to use both only plays through HDMI.

3) When the screen is an HDMI connection:
  - screen is identified by xrandr as HDMI2
  - screen size is correctly set to max size (for TV) after boot but during boot it's wrong
  - BIOS page is black 
  - sound plays only through Analogue Stereo o/p. HDMI sound is not possible under any circumstances even with aplay.

Now I'm a relative newbie but I think all this mess is related to the fact that the LCD/DVI screen or port is identified as HDMI1 and the TV/HDMI as HDMI2 but I have no idea how to change that.

I have tried to produce an xorg.conf but I get the usual message "Number of created screens does not match number of detected devices". I've not found a solution to that and xorg.conf is deprecated anyway. I've no idea how I might force the system to identify screens correctly.

I have read somewhere that a (kernel ?) bug causes sound to only be available from a first HDMI screen so when my TV connects as HDMI2 I get no HDMI sound and I suspect the same sort of problem exists in pre-boot graphics.

---

