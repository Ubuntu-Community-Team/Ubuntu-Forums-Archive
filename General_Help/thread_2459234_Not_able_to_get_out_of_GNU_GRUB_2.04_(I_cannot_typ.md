---
title: "Not able to get out of GNU GRUB 2.04 (I cannot type whatsoever)"
date: 2021-03-14
forum: General Help
---

### Post by bizyle on 2021-03-14
I just installed Ubuntu and it worked fine for an hour. I did a quick restart after fiddling around with the O.S, and I am stuck on the GNU GRUB area without the ability to type. I removed the USB, and I still somehow get to that screen! Is there any way I can get DIRECTLY to the BIOS? (The issue happens literally half a second after I turn on my pc, so there is always no time to react)

---

### Post by deadflowr on 2021-03-14
Not sure as BIOS is machine specific and outside the realm the any installed operating system.
You need to know the make and model to find the BIOS keyboard shortcut it uses.
Once you find that out I would recommend rapid tapping the shortcut concurrently while turning on the machine.

---

### Post by QIII on 2021-03-14
Exactly what do you mean when you say "I am stuck on the GNU GRUB area without the ability to type"?

What do you see on your screen?

---

### Post by bizyle on 2021-03-14
The GNU GRUB screen; where I usually type commands etc. it just is stuck on that screen

I tried spamming F-12 (the key I use to get into bios.) and there is no use. I turned on my pc and started spamming; and it just went straight to the grub screen

Here is a video of me trying to get onto BIOS, and an explanation of what is actually going on. As you can see, I am stuck on the GRUB screen and cannot type: [https://streamable.com/hnhxkd](https://streamable.com/hnhxkd)

---

### Post by CatKiller on 2021-03-14
> **bizyle said:**
> Is there any way I can get DIRECTLY to the BIOS?

Yes. If you're using UEFI mode rather than Legacy/CSM/BIOS mode, and you can boot to the OS. Then you could use ```
systemctl reboot --firmware-setup
```

Otherwise, you'd need to not be using Fast Boot (since that ignores all keyboard input and hardware enumeration) and you'd need your BIOS/UEFI to be listening for USB signals as if they were PS/2 signals, which is an ability you can turn off. If your hardware and configuration mean that you're unable to enter the setup then you need to either change the configuration (reset to defaults by button, jumper, or removing the battery) or change the hardware (by finding a PS/2 keyboard).

---

### Post by bizyle on 2021-03-14
It appears you do not understand. I cannot get to anywhere that you are talking about. Whenever I boot up my pc, it gets to the GNU GRUB console with ZERO way of getting out. If anything, it would have to be a physical fix; or I am somehow doing something wrong. Using my keyboard or mouse will not do anything, as it is unresponsive

---

### Post by CatKiller on 2021-03-14
> **bizyle said:**
> It appears you do not understand.
I understand perfectly. It wasn't us that locked the crowbar in the chest. You've got yourself into a pickle, and I've told you how you can get out of it.

---

### Post by bizyle on 2021-03-14
I just re-read your statement, and I have many questions. For one, how do I get into Fast-Boot? I am currently a beginner to all of this, and am trying to get into bios to restore my older windows instance to get out of Ubuntu

---

### Post by CatKiller on 2021-03-14
To disable Fast Boot, you'd need to get into the BIOS/UEFI setup to turn it off. Which means resetting to defaults, or booting into an OS like, say, an Ubuntu live USB, to run the command that I gave you. 

Or, if you hadn't enabled Fast Boot, your machine might not be listening for USB keyboard input, which means that you'd need to either use a different keyboard, or tell it to listen for USB input. Which means you need to get into the BIOS/UEFI setup. See above. 

None of your issues are about Ubuntu, other than your initial failure to boot, which will likely be an easy fix once you can get into the BIOS/UEFI setup.

---

### Post by bizyle on 2021-03-14
Since I cannot boot into an OS, how would I reset to defaults? That may solve all of the issues for now

I am going one by one here for the steps, so don’t feel like I am disregarding anything you say :)

---

### Post by CelticWarrior on 2021-03-14
> **bizyle said:**
> Since I cannot boot into an OS, how would I reset to defaults? That may solve all of the issues for now

> (...) [COLOR=#000000]booting into an OS like, say, **an Ubuntu live USB**[/COLOR] was the suggestion...

---

### Post by bizyle on 2021-03-14
I have Unbuntu via a USB, which is how I always boot it. It I take the USB out, Ubuntu no longer works. Both ways, I still get to the GNU screen. If you can emphasize the word “live” in the sentence that would mean a ton!

---

### Post by grahammechanical on 2021-03-14
Your video shows us what you are doing with your fingers. We have next to no time to see what is on the screen. What you are seeing is not the normal Grub boot menu screen. I am guessing that Grub cannot load its menu because it cannot access it configuration file. That file would normally be found at /boot/grub.grub.cfg. You say this:

> I did a quick restart after fiddling around with the O.S

What exactly did you do? As previously stated, by the time that you are seeing that screen the motherboard has already finished with it own boot up precess and handed over to the boot loader (Grub). The time to access the UEFI settings menu has past. Will the system still load from a USB memory stick for a Ubuntu live session? Or, has the boot priority been changed?

Edit: After reading your last post again I see this:

> I have Unbuntu via a USB, which is how I always boot it.

So, you have not installed Ubuntu to the hard drive. I think that somehow you have installed Grub to the hard driver and over written the Windows boot loader. And the Grub on the hard drive cannot find its configuration file because it is on the USB memory stick and you have removed the memory stick.

Regards

---

### Post by CatKiller on 2021-03-14
> **bizyle said:**
> Since I cannot boot into an OS, **how would I reset to defaults**? That may solve all of the issues for now

> **CatKiller said:**
> (reset to defaults **by button, jumper, or removing the battery**)

The particulars of how to reset to defaults vary by machine. Some have a (usually not very accessible, so you don't press it by accident) button. Some require you to change a jumper, and then change it back. Some need you to remove the watch battery that maintains the charge that keeps the settings. Your manual will say.

Plus you can boot into your Ubuntu USB, assuming your BIOS/UEFI settings are set to allow that. If not, see above.

---

### Post by bizyle on 2021-03-14
What exactly did you do? 
Just installed applications through terminal. It was my first time using Ubuntu, so I was exploring the OS

Will the system still load from a USB memory stick for a Ubuntu live session?
No

has the boot priority been changed?
Ubuntu was the main boot priority in Bios. I remember setting it up. Windows was second

P.S. once I think about it, I do remember installing the O.S onto my D: Drive (2TB) on the Ubuntu installer. It may have been something else, but I do not see what else I could have installed!

---

### Post by oldfred on 2021-03-14
Often cold boot, not warm reboot will give you just a few seconds to press correct key to get into UEFI/BIOS.
That is all power off, remove battery if laptop, and hold power switch for 10 sec or so, so system is totally drained. Then boot & press correct key to get into UEFI/BIOS, often f2 or del key, but varies by brand. Only press correct key.

If that does not work then you have to do CatKiller's suggestion of resetting with jumpers on motherboard, and/or removing coin battery to get system to reset to defaults. Any changes you made to UEFI to allow Ubuntu install, will have to be redone. See manual for your system for details as they vary somewhat.

---

### Post by bizyle on 2021-03-14
I think that somehow you have installed Grub to the hard driver and over written the Windows boot loader.

I remember setting The USB as the main priority, and windows as second (I used Rufus on my windows pc to convert the Ubuntu ISO to the usb, so that is how I set Ubuntu as the number one priority, and windows as second)

---

### Post by CatKiller on 2021-03-14
> **bizyle said:**
> It may have been something else, but I do not see what else I could have installed!

A relatively easy way for the inexperienced to get the symptoms you're showing - booting to the Grub prompt rather than into Ubuntu - is to install Ubuntu in one mode (UEFI, say), which is determined by how you booted the installer, but then trying to boot the installed version the other way (Legacy/CSM/BIOS, in this example). The bootloader works differently and is in a different place for each mode. You'd have exactly the same problem if you'd done the same thing with Windows. 

It's an easy fix - change the mode you're booting with - if you can get into the setup.

---

### Post by bizyle on 2021-03-14
“change the mode you're booting with - if you can get into the setup.”
I cannot get into the setup or anything for that matter. Once I think about it, I do have another computer lying around if there is any thing I can do with that to help my own pc out. Anyways, how would I change the mode?

“is to install Ubuntu in one mode (UEFI, say), which is determined by how you booted the installer, but then trying to boot the installed version the other way (Legacy/CSM/BIOS, in this example).”
I physically cannot get into the UEFI. As I said, I do have another pc I could use to help troubleshoot further if needed!

---

### Post by CatKiller on 2021-03-14
> **bizyle said:**
> I physically cannot get into the UEFI.
That's why you'd need to reset it to defaults (or potentially use a different keyboard, depending on what exactly the problem with your settings is). You've safely locked your chest-opening crowbar inside the chest.

---

### Post by bizyle on 2021-03-14
“Some require you to change a jumper, and then change it back. Some need you to remove the watch battery that maintains the charge that keeps the settings. Your manual will say.“

Tbh I do not have my manual. What I can do is try finding the manual online, but I have no idea what to do from there!

What I am going to do is call my manufacturer and ask how to restore defaults. You told me some basic examples of how to, but I want to be sure how to do it right. I hope that sounds great, and I will hopefully be back shortly!

---

### Post by deadflowr on 2021-03-14
> Tbh I do not have my manual. What I can do is try finding the manual online, but I have no idea what to do from there!
If you know the machine or motherboard you can post it and we might help narrow it down.
Some of the posters who have helped have mad search skills.

---

### Post by bizyle on 2021-03-14
It’s a cyberpowerpc. The motherboard is a gigabyte b450m ds3a wifi. The graphics card is a phantom rx580. I use an AMD Ryzen 7 2700

It’s a cyberpowerpc. The motherboard is a gigabyte b450m ds3a wifi. The graphics card is a phantom rx580. I use an AMD Ryzen 7 2700 If you can maybe help restore to defaults if possible :)

---

### Post by CatKiller on 2021-03-14
[This one](https://www.gigabyte.com/uk/Motherboard/B450M-DS3H-WIFI-rev-1x)? 
> CLR_CMOS (Clear CMOS Jumper) 
Use this jumper to clear the BIOS configuration and reset the CMOS values to factory defaults. To clear 
the CMOS values, use a metal object like a screwdriver to touch the two pins for a few seconds.
• Always turn off your computer and unplug the power cord from the power outlet before clearing 
the CMOS values.

From the picture it's on the bottom edge of the motherboard, just above the front panel connectors.

---

### Post by bizyle on 2021-03-14
This one? 
Yes!

CLR_CMOS (Clear CMOS Jumper) 
Use this jumper to clear the BIOS configuration and reset the CMOS values to factory defaults. To clear 
the CMOS values, use a metal object like a screwdriver to touch the two pins for a few seconds.
• Always turn off your computer and unplug the power cord from the power outlet before clearing the CMOS values.

Ok so, I do not know what jumper cable you are talking about. Secondly, which two pins?
Are there any photographic/video examples?

---

### Post by CatKiller on 2021-03-14
Jumpers are just pairs of pins that stick up. In Ye Olden Days you'd configure the computer by connecting some pairs together and not connecting others. Your manual is saying to temporarily connect them with something conductive when the power is off.

---

### Post by CelticWarrior on 2021-03-14
There should be a schematics in your user's manual.

---

### Post by bizyle on 2021-03-14
Just curious; do you mind sending me the manual? I would probably just want it for later if I run into a similar problem

---

### Post by CatKiller on 2021-03-14
[https://download.gigabyte.com/FileList/Manual/mb_manual_b450m-ds3h-wifi_e_1201.pdf](https://download.gigabyte.com/FileList/Manual/mb_manual_b450m-ds3h-wifi_e_1201.pdf)

---

### Post by bizyle on 2021-03-14
[https://streamable.com/aczoaa](https://streamable.com/aczoaa) Do you mind taking a screenshot of a frame in the video, and helping point out where exactly it is?

---

### Post by bizyle on 2021-03-14
[https://streamable.com/aczoaa](https://streamable.com/aczoaa) Do you mind taking a screenshot of a frame in the video, and helping point out where exactly to put the screw driver?

---

### Post by oldfred on 2021-03-14
CatKiller has your manual in post #29.
Page 12 shows layout & #18 as CLR-CMOS
and page 19 has explanation of how to do it.

My Gigabyte Intel based Z170 is almost identical, its just #16 in graphic with same explanation of details.

---

### Post by bizyle on 2021-03-14
Guys, it worked! You do not know how much I want to thank you guys! I thought I would lose all of my Data! I hope that you guys have an amazing day! :)))))

---

### Post by CatKiller on 2021-03-14
Good to hear. Don't forget to mark the thread as solved to help anyone else that might be looking for a solution to the same problem.

---

