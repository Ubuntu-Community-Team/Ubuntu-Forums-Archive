---
title: "Ubuntu LiveCD freezes on splash screen"
date: 2005-04-17
forum: General Help
---

### Post by iroko on 2005-04-17
On booting up the Ubuntu 5.04 LiveCD my peripherals are detected, I choose the settings but when I get to the splash screen, my mouse stops working and the screen freezes. I didn't have this problem the one time I tried the Warty LiveCD. 

I have checked the iso MD5sum and it is correct.

I had a similar problem when I tried the preview LiveCD and was given the following advice by Steffen 
[INDENT]"I don't have the technical expertise myself, but if you post your /var/log/Xorg.0.log and
/etc/X11/xorg.conf files, someone might be able to assist you..."
[/INDENT]
Unfortunately I haven't the slightest idea how to go about getting hold of those files.

My set up is
AMD Athlon 64 3200+ (939 pin)
ASUS A8N-SLI MOTHERBOARD (nvidia NfORCE4 SLI chipset)
512 MB PC3200 DDR RAM
Seagate 200GB SATA hard disk
Nvidia nForce Onboard sound
128MB ATI Radeon X600Pro Graphics card

I had a similar problem when I tried installing Suse 9.2 Pro alongside Win XP Pro. It appeared to instal OK (I can still boot WinXP) and appears to boot OK before dying just when I would expect the Splash screen or log in screen.

Any help with the Ubuntu problem would be appreciated.

---

### Post by OneSeventeen on 2005-05-05
I just wanted to say that I'm having the same problem.
I've got an HP Pavilion zv6005US laptop with an AMD Athlon 64 3200+ (939 as well) and it just freezes.

Since I'm using the liveCD, and I can't seem to get into gnome to do anything, I don't know how to post the Xorg.0.log and xorg.conf files.

Any tips on this would really help!

**EDIT:** According to [this redhat bugzilla page](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=109256) it looks like it might be an ATI driver issue.  I have a Radeon Xpress 200M, and it looks like the 7800's and above should be using VESA instead of RADEON.

Is there a way to choose a different video driver in the live CD?

---

### Post by w3bu53r on 2005-05-08
I had the similar problem, the Ubuntu i386 LiveCD freezes at the splash screen. All I could see is brown background w/ a moveable mouse pointer. I ain't able to log into DE (Desktop Environment).

System specs:

Intel Pentium 4
Nvidia Geforce 6800
1G RAM

Other LiveCDs such as Slax & Knoppix worked fine for me

---

### Post by iroko on 2005-05-11
Still no joy! I had a similar problem using Suse 9.2 Professional.

No problems with Knoppix though. It works fine.

Any ideas will be welcomed. I'd like to install Ubuntu but I'd rather not trash my Windows installation in the process. Hence my attempt to use the LiveCD first.

---

### Post by w3bu53r on 2005-05-18
Bump

---

### Post by Paradoxdruid on 2005-08-06
[QUOTE=w3bu53r]I had the similar problem, the Ubuntu i386 LiveCD freezes at the splash screen. All I could see is brown background w/ a moveable mouse pointer. I ain't able to log into DE (Desktop Environment).[/QUOTE]

I'm having the exact same problem (makes it to brown background with mouse cursor).

I'm trying this on a Intel MB with a 3.2 GHz P4, NVidia graphics.

The only hint I saw while loading was that when Ubuntu started (after the LiveCD detection routines), it said that it failed to load the cdrom...  I will try again in non-X mode later, to see if I can sort it out.  But if anyone has a possible solution, I'd appreciate it.

Thanks!

---

### Post by r53s on 2005-08-10
I've tryed on three computers, and it only works when the cd burner is set as a slave, one set as slave of the hard drive and one set as slave of another cd burner...
And it runs faster on the Via chipset...

---

### Post by cadmma on 2005-08-12
I had this problem on my laptop. Don't know if the same problem affects desktop machines but I managed to get it working by adding the following to the command line: noapic nolapic acpi=off vga=771

---

### Post by Paradoxdruid on 2005-09-08
[QUOTE=cadmma]I had this problem on my laptop. Don't know if the same problem affects desktop machines but I managed to get it working by adding the following to the command line: noapic nolapic acpi=off vga=771[/QUOTE]

I'm not sure I have the same problem...  I tried *noapic nolapic acpi=off* and got the same result:  The screen shows the orange background, and hangs there.  I have a mouse cursor, and can move it around, but nothing loads.  Additionally, Ctrl-Alt-Bckspc and Ctrl-Alt-F1 both don't respond.

---

### Post by nwjsmith on 2005-09-20
[QUOTE=iroko]On booting up the Ubuntu 5.04 LiveCD my peripherals are detected, I choose the settings but when I get to the splash screen, my mouse stops working and the screen freezes. I didn't have this problem the one time I tried the Warty LiveCD. 

I have checked the iso MD5sum and it is correct.

I had a similar problem when I tried the preview LiveCD and was given the following advice by Steffen 
[INDENT]"I don't have the technical expertise myself, but if you post your /var/log/Xorg.0.log and
/etc/X11/xorg.conf files, someone might be able to assist you..."
[/INDENT]
Unfortunately I haven't the slightest idea how to go about getting hold of those files.

My set up is
AMD Athlon 64 3200+ (939 pin)
ASUS A8N-SLI MOTHERBOARD (nvidia NfORCE4 SLI chipset)
512 MB PC3200 DDR RAM
Seagate 200GB SATA hard disk
Nvidia nForce Onboard sound
128MB ATI Radeon X600Pro Graphics card

I had a similar problem when I tried installing Suse 9.2 Pro alongside Win XP Pro. It appeared to instal OK (I can still boot WinXP) and appears to boot OK before dying just when I would expect the Splash screen or log in screen.

Any help with the Ubuntu problem would be appreciated.[/QUOTE]
 I have the same problem, my configuration:

AMD 64 3200+
**ATI RADEON XPRESS 200**
512 MB RAM
160 GB HD

The new Breezy Badger Preview LiveCD doesn't fix the problem
HELP!

---

### Post by putz3000 on 2005-09-21
I have not yet tried the nolapic acpi=off vga=771 command (will try shortly), but I am having the exact same problem.  mouse freezes and cd-rom drive shuts down and nothing works.  I am woundering if it is the ATI drivers/chipset.

I have HP ze2117US, sempron 2800+, 512 megs ram (128 devoted to ATI xpress 200m, dvd drive/cd burner.  This laptop also has internal wireless.  I wouldnt think it would keep it from loading (just not work), but I guess that could be another problem.

---

### Post by putz3000 on 2005-09-21
The nolapic acpi=off vga=771 does not work for me either.  So either there is a hardware  incampatibility or a problem with the live cd.

---

### Post by noerter on 2005-09-24
Same problem here with live CD,

AMD64 3200  939
ASUS A8V-Deluxe
OEM nVidia
Seagate SATA+3IDE
1gb ram.

After the yello screen appers (no login) the system freezes. The mouse responds but there is nothing i can do. I only get a mouse cursor on a yellow screen. HDD and CDROMS stop functioning. Happens with both x86 and AMD64

Any help please?

No problem running knoppix live CD, i'm dloading now gnoppix to give it a try.

---

### Post by wawa on 2005-09-24
Did you try booting with "gdth=disable:y" or "noapic nolapic" ?

---

### Post by noerter on 2005-09-25
[QUOTE=wawa]Did you try booting with "gdth=disable:y" or "noapic nolapic" ?[/QUOTE]
 tried noapic nolapic but no luck

---

### Post by noerter on 2005-09-25
[QUOTE=wawa]Did you try booting with "gdth=disable:y" or "noapic nolapic" ?[/QUOTE]
 thank you for your fast reply and advice. Nothing works. The PC just freezes. Ctr-Alt-F2 yields no result. CDROM stops. I get a sound, a yellow screen and a otherwise fully functional mouse cursor. I sure hope Ubuntu is more than that.

---

### Post by quixote8 on 2005-09-26
[QUOTE=nwjsmith]I have the same problem, my configuration:

AMD 64 3200+
**ATI RADEON XPRESS 200**
512 MB RAM
160 GB HD

The new Breezy Badger Preview LiveCD doesn't fix the problem
HELP![/QUOTE]

Same deal for me ...
Amd64 3000+
asus A8N SLI
 .... *geforce 6200* vid card (nvidia) ...
2 x 512 mb DDR4
2 x 160 Gb WD sata hdd's
 .... thinking, thinking, thinking ... nVidia vid card drivers ... ????
but dont know how / what to do about it.

---

### Post by noerter on 2005-10-02
[QUOTE=quixote8]Same deal for me ...
Amd64 3000+
asus A8N SLI
.... *geforce 6200* vid card (nvidia) ...
2 x 512 mb DDR4
2 x 160 Gb WD sata hdd's
.... thinking, thinking, thinking ... nVidia vid card drivers ... ????
but dont know how / what to do about it.[/QUOTE]

i just run knoppix and its runs perfectly OK. Its uses however "vesa" drivers and not nvidia. Is there any way we can configure LIVECD to use vesa?

---

### Post by eneanito on 2005-10-06
I am trying w/ AMD64 live CD
My Machine is

Board MSI R480 939
Atlon64 3.0 GH
mem DDR 2X256 /400 Markvision
HD IBM Histachi 8060 (I believe it is SATA - I don´t know what it means)
LCD 17" ACER monitor, a truly jewel!

Upload goes very well as far displaying a central rectangle near 15cm long X 6 cm tall with UBUNTU name, logo and down text "for human beings"

Cursor has movility while that rectangle is drawing and stay cool in the too moment it is lfinished?

Anyone knows What happens?

---

### Post by noerter on 2005-10-13
does this problem persist in 5.10?

---

### Post by Paradoxdruid on 2005-11-10
[QUOTE=noerter]does this problem persist in 5.10?[/QUOTE]

It most definitely does persist.  I just downloaded the latest LiveCD and tried it.

Like usual, it gets to the orange/brown desktop background and a mouse cursor, and then..  stops.  The cursor can be moved, but the system doesn't respond to keyboard commands (Ctrl-Alt-Backspace, Ctrl-Alt-F2, Return, etc).  After about 20 seconds, CD-ROM activity stops and it just sits there..  after 20 minutes, no changes and no hard drive or CD activity.

I use Ubuntu on another desktop, and it's very frustrating that it gets so close to working on my main system.

The system in question is:
Chaintech V915P motherboard
Pentium 4, 3.2 GHz
1024 MB RAM
one IDE cable with Harddrive on Master, CD-drive on slave
one SATA harddrive
NVidia GeForce 6200 with two monitors attached


Does anyone have any ideas?  Thank you in advance.

---

### Post by noerter on 2005-12-11
anything new about this bug? any way to fix this?

---

### Post by creatix on 2005-12-14
hi,
i have exactly the same problem. i don't understand why a live cd doesn't use the standard vesa drivers wich every graphic-card supports. the (nv)idia drivers don't support my graphic-card: aopen nvidia geforce 6800le.

i have the same problem with other live-cd's too, not just ubuntu. is there any "cheat-code" i could enter at the prompt before booting, to use the vesa drivers. after auto-login, the screen stays brown. no panels, no icons...

---

### Post by creatix on 2006-01-01
i found a solution:
type "live-expert" at the bootprompt, then i can choose the vesa drivers later.

---

### Post by w3bu53r on 2006-01-16
Bah, 5.10 also hates me.

/bump for justice

---

### Post by Giant81 on 2006-01-19
I'm having the same problem with a ZV6000 HP laptop and have been completely unable to find a solution.  I've tried 

noapic 
debian-installer/framebuffer=false
nolapic
acpi=false
live-expert

NOTHING WILL WORK.  I'm almost completely convinced that you cannot run the live CD with this laptop.  If anyone has anything else I can try I'm up for trying anything.

Thank you

---

### Post by Brave on 2006-01-25
Hi all ive got the same problem.

Im running a amd64 x2 3800
asus a8n32sli
2 gig of ram
1 x pata & 1 x sata
geforce 7800gt

I know its no the system as im already running a dual boot with windozz and pclinuxos but i down loaded the ubuntu amd64 bit for a 64 bit os

---

### Post by aristotlewilde on 2006-02-03
This is my issue as well (posted elsewhere).  System specs below.  It seems all of us are running AMD processors...

Hangs on brown screen w/ mouse movement, and nothing else.  Login screen works fine.  Occasionally can see Ubunto logo all pixelated/scrambled/squished on brown screen...

Have it workign fine on my old crappy system, but I want a dual boot!

AMD 64 3500+
Nforce a-939 mobo
nvidia geforce 7800gt-oc video
soundblaster x-fi extreme sound
2 gig of ram
1 SATA drive (w/ OS's on it)
1 IDE drive

---

### Post by jonmac on 2006-02-21
I am having the same problem, brown screen with rectangle in the middle saying "Ubuntu", however my rectangle is frizzy and hard to read.  My machine is:

AMD64 X2 4400+
ASUS A8N-SLI Deluxe
nVidia GeForce 7800Gt
4GB Ram (4X 1GB)
2X WD Raptor 74GB SATA in RAID 0
80GB WD SATA

I would love to find a solution to this problem as I hope to be able to dual boot in XP and Ubuntu, just want to make sure I like/can run Ubuntu first.

Gracias,
Jon

---

### Post by aurifex on 2006-03-09
I am also having the same problem, both with the live and standard install version.

**Motherboard:** ABIT IC7-MAX3
**Processor:** P4 3.0GHz
**RAM:** Corsair PC3200 2GB
**Video:** nVidia 6800nu
**Audio:** Sound Blaster Audigy 2
**Hard Drive 1:** Samsung SP0812C (80GB, 7200RPM, SATA)
**Hard Drive 2:** Samsung SP1614C (160GB, 72000RPM, SATA)
**DVD-Drive:** Plextor DVDR PX-712A

Ubuntu loads itself and boots up, but I only get to a brown background, and it doesn't progress past that. I have a mouse pointer, which I can move around freely, but nothing else responds. This is most aggrivating.

---

### Post by Lord Illidan on 2006-03-10
[quote=aurifex]I am also having the same problem, both with the live and standard install version.

**Motherboard:** ABIT IC7-MAX3
**Processor:** P4 3.0GHz
**RAM:** Corsair PC3200 2GB
**Video:** nVidia 6800nu
**Audio:** Sound Blaster Audigy 2
**Hard Drive 1:** Samsung SP0812C (80GB, 7200RPM, SATA)
**Hard Drive 2:** Samsung SP1614C (160GB, 72000RPM, SATA)
**DVD-Drive:** Plextor DVDR PX-712A

Ubuntu loads itself and boots up, but I only get to a brown background, and it doesn't progress past that. I have a mouse pointer, which I can move around freely, but nothing else responds. This is most aggrivating.[/quote]

I know this tip when installing.

Edit the /etc/X11/xorg.conf after installation, with a text editor like nano or vi.
Do it in failsafe mode.

Scroll down until you see something resembling this

```
Section "Device"
    Identifier    "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection
```

Change "nv" to "vesa".

Reboot and try again. Then you should have a go at installing the official nvidia drivers..

---

### Post by aurifex on 2006-03-10
[quote=Lord Illidan]I know this tip when installing.

Edit the /etc/X11/xorg.conf after installation, with a text editor like nano or vi.
Do it in failsafe mode.

Scroll down until you see something resembling this

```
Section "Device"
    Identifier    "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection
``` 
Change "nv" to "vesa".

Reboot and try again. Then you should have a go at installing the official nvidia drivers..[/quote]

How would I get to failsafe mode?

---

### Post by Paradoxdruid on 2006-03-15
I just wanted to give everyone who has experienced this problem a update:

The Dapper flight 5 Live CD has fixed this bug for me, and boots just fine.  Give it a try.  :mrgreen:

---

### Post by youBun2 on 2006-03-16
Alright, I am in the same boat as you all but far worse.

I currently run Windows XP Home Edition on my desktop that was bought last February. The file system on my main and only hard drive of 200 GB is NTFS.

Yesterday a friend gave me a copy of Ubuntu (official copy from the website) and I decided to load up the Live CD. Without a result I found that perhaps it is just the Live CD and so I went ahead and started with an installation.

Using a partioning program I managed to create a 10 GB partition for Linux etc. I carried on with the install and towards the end it asked me if I wanted to have the GNU GRUB installed on my C: (with Windows XP) as to have a choice in OS when at boot-up.

Innocent me went ahead with that choice and enjoyed the first few steps at seeing Ubuntu. I managed to create myself a user account and I logged in... it froze. I then decided to restart and load up Windows XP instead. It won't load. When I select Windows XP Home Edition it has:

root (hd0,1)
savedefault
makeactive
chainloader +1

and stops. When I checked out the same boot-up process for Ubuntu, I saw that it reads:

root hd(0,2)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
intrid /boot/initrd.img-2.6.12-9-386
savedefault
boot

and obviously loads Ubuntu and allows me to log in but freezes on the centered image.

From what I can see, it appears Windows XP doesn't load up its kernal or something like that. Are there any ways I can simply log on to my Windows system?

---

### Post by fasteddy86 on 2006-04-04
[QUOTE=youBun2]
Innocent me went ahead with that choice and enjoyed the first few steps at seeing Ubuntu. I managed to create myself a user account and I logged in... it froze. I then decided to restart and load up Windows XP instead. It won't load. 




From what I can see, it appears Windows XP doesn't load up its kernal or something like that. Are there any ways I can simply log on to my Windows system?[/QUOTE]

I had a similar problem. I installed Ubuntu, couldn't get it to work, then tried to wipe it. Unfortunately, it also killed GRUB, and I couldn't log into Windows. The solution is to use your XP installation CD to repair the Master Boot Record (MBR).
So, load up the XP install cd, and then type R when it gives you the option. Select XP from the menu.
Enter the Administrator password if asked.
At the command prompt, type fixmbr.
Hopefully that solved it.

---

