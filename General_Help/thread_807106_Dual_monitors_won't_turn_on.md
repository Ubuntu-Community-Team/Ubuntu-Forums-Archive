---
title: "Dual monitors won't turn on"
date: 2008-05-25
forum: General Help
---

### Post by skydiver|goose on 2008-05-25
I've got an HP/Compaq NC6000 laptop, and I want to run a VGA cable out to a monitor to set up dual monitors off of my laptop and the other monitor, but when I go to System > Admin > Screens and Graphics, my "Screen 2" is grayed out and when I select it, I can ONLY set it to "Default" or "Disabled" (Disabled being what it's already set to). The option to set it to "Secondary Screen" is grayed out.

Any suggestions?

---

### Post by Nexano on 2008-05-25
whats your video card?

Did you install the video card drivers?

---

### Post by skydiver|goose on 2008-05-25
I haven't installed any card drivers

How do I check what my video card is? It's whatever the factory for this laptop is. And if they're not installed, could you help me install them?

---

### Post by Nexano on 2008-05-25
sure thing man. open a terminal (alt+f2 and type in gnome-terminal and hit enter) then type lspci and copy/paste that here :)

---

### Post by skydiver|goose on 2008-05-25
goose@goose-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
goose@goose-laptop:~$ 


and if it's any consolation to my noob-ness, I DO know how to open terminal ;)

---

### Post by Nexano on 2008-05-25
Well, theres a LOT of new people on these forums, so i thought id play it safe ;(

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] <--- that line tells us that youre video card is Mobility Radeon 9600 M10 :) now lemme find you some drivers.

in the meantime, could you post your xorg.conf?

safe again: /etc/X11 - gedit is a nice graphical text editor :p

copy/paste it on [www.pastebin.com](www.pastebin.com) and link me up ;)

---

### Post by skydiver|goose on 2008-05-25
here you go:

[http://pastebin.com/m157a9c55](http://pastebin.com/m157a9c55)

I'm a total failure at installing drivers on linux by myself, fyi..

---

### Post by Nexano on 2008-05-25
it seems the drivers are allready installed :o

do you have an ati control panel?

whats the resolution you want to run on your tv?

---

### Post by skydiver|goose on 2008-05-25
I'm not sure what an ATI control panel is.. It's actually a monitor, but it may eventually be plugged into a TV. But let's do 1024x768 just to be safe. Although I think the monitor is opitmal at 1440x something...

---

### Post by Nexano on 2008-05-25
im sorry, im on several forumthreads at the moment, i got tv from another one :p but ok, 1024x768 it is. give me a few minuts to toy around with your xorg and figure out how the **** we will get it done with ATI ;(

---

### Post by skydiver|goose on 2008-05-25
take your time. it's much appreciated.

---

### Post by Nexano on 2008-05-25
allright, sorry about the time it took to reply you, but try replacing the contents of xorg.conf with this: [http://pastebin.com/m17aef5e4](http://pastebin.com/m17aef5e4)

but first, terminal and:
cd /etc/X11
sudo cp xorg.conf xorg.conf.backup


when replaced ctrl+alt+del to restart the x server, if nothing happens when restarting hit ctrl+alt+f1, login and type:
cd /etc/X11
sudo cp xorg.conf.backup xorg.conf
sudo /etc/init.d/gdm restart

Good Luck :)

---

### Post by skydiver|goose on 2008-05-25
ok, did what you said, restarted, now my monitor is mirroring my laptop screen, and both are locked in 600x800

---

### Post by Nexano on 2008-05-25
really? that sounds weird oO

hmm, i dont have an ATI card myself.. but ill try to look it over, lets hope someone can answer you quicker then me tho :p

---

### Post by Nexano on 2008-05-25
[http://pastebin.com/m3ef0f378](http://pastebin.com/m3ef0f378)

try that one :/

---

### Post by skydiver|goose on 2008-05-25
before I give it a try, when I hit control alt delete, it brought up the main shutdown menu with "shut down" "restart" "log off" ect.. which one do you want me to click to restart the x11 server? I just restarted my whole laptop the first time.

---

### Post by skydiver|goose on 2008-05-25
I asked some guys on IRC and figured out you mean Control Alt Backspace, but I'm still getting the same result.

---

### Post by Nexano on 2008-05-25
well, just ctrl+alt+f1 and sudo /etc/init.d/gdm restart then, that should do the trick

---

### Post by skydiver|goose on 2008-05-25
ok, so to make I'm doing this all right before I do anyting:

I'm going to gedit my xorg.conf file and overwrite it with the one you've provided me in pastebin, then I'm going to save, then ctrl+alt+f1 and type in "sudo /etc/init.d/gdm" and then...?

---

### Post by Nexano on 2008-05-25
"sudo /etc/init.d/gdm stop"
"sudo /etc/init.d/gdm start"

then hopefully it works :p

if not, im out of clues right now, as i dont use an ati card myself :/

---

