---
title: "Blank Screen On Startup -_-"
date: 2007-04-23
forum: General Help
---

### Post by villevol666 on 2007-04-23
I have tried 6.06 and 7.04 live and installed versions of Ubuntu. The furthest i have gotten is hearing the system logon sounds. It doesnt display anything on the screen at all. So i know that ubuntu is started, but i cant see anything. 

Here are my specs:
DFI nForce4 LanParty MotherBoard
AMD FX-60 CPU
(2) nVidia 7950 GX2's (running in Quad SLI mode)
Corsair 550MHZ XMS 4GB 
74GB WD Raptor SATA I
(2) 500GB WD SATA II
250GB WD IDE 150
ONboard audio
ONboard Ethernet 

After the Ubuntu Logo Loading screen it goes blank.
Thanks in advance, 
Brandon

---

### Post by Andrej_BB on 2007-04-23
Same goes for me - I could boot until yesterday, and now i cannot do it anymore ( i haven't installed or upgraded anything - it works in recovery mode, though...

---

### Post by stchman on 2007-04-23
> **villevol666 said:**
> I have tried 6.06 and 7.04 live and installed versions of Ubuntu. The furthest i have gotten is hearing the system logon sounds. It doesnt display anything on the screen at all. So i know that ubuntu is started, but i cant see anything. 

Here are my specs:
DFI nForce4 LanParty MotherBoard
AMD FX-60 CPU
(2) nVidia 7950 GX2's (running in Quad SLI mode)
Corsair 550MHZ XMS 4GB 
74GB WD Raptor SATA I
(2) 500GB WD SATA II
250GB WD IDE 150
ONboard audio
ONboard Ethernet 

After the Ubuntu Logo Loading screen it goes blank.
Thanks in advance, 
Brandon

It might be the SLI configuration you have.  Download and install Envy.  Invoke the CLI version of envy by typing envy -t in recovery mode.  Then select option 1.  I have never done the SLI thing, but I hear it can be a PITA.

---

### Post by Andrej_BB on 2007-04-23
I realised that i can run feisty if i do just the startx, but cannot get in through gdm.
Whatever i do gdm refuses to start, i already apt-get removed and apt-get installed it - no change...

---

### Post by Andrej_BB on 2007-04-23
I have tried other search options and realised that adding 
vga=795 in the kernel line in the /boot/grub/menu.lst works :)

---

### Post by leisuretime on 2007-04-24
> **Andrej_BB said:**
> I have tried other search options and realised that adding 
vga=795 in the kernel line in the /boot/grub/menu.lst works :)


ok, I'm a newb....and I have this same problem...can someone spell out the process to get that plz?:confused:

---

### Post by Zeroedout on 2007-04-26
Bieng a newb is fine. We all were once. Go to application ---------> accessories ---------> terminal. type ```
sudo gedit /boot/grub/menu.lst
``` To make things easier i turn word wrapping off, (edit ------> preferences-----------> uncheck enable text wrapping). [this will let you see the config file in a more human readable manner with proper spacing) The first kernel entry should say something to this effect ```
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=e59e15ec-8ec4-44c7-ba2b-d5fae9c8775c ro quiet splash
``` right after splash, add ```
vga=791
``` Now the line should look like this, ```
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=e59e15ec-8ec4-44c7-ba2b-d5fae9c8775c ro quiet splash vga=791
``` Assuming vga=791 change defoptions (line 89) to look like this ```
# defoptions=quiet splash vga=791
``` (you're adding vga=791 here so when you get a new kernel, it will automatically add vga=791 to it's options). 
Though this might seem a touch complex, just follow this step by step and it should work fine. If you get an error that says it can't find the specified video mode, at boot, you might have to change 791 to another number (but that shouldn't happen).

---

