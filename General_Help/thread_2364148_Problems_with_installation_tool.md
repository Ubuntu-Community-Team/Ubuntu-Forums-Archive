---
title: "Problems with installation tool"
date: 2017-06-19
forum: General Help
---

### Post by damnporthos on 2017-06-19
I'm trying to install Ubuntu GNOME 16.04.2 LTS 64 bits on my HP Ultrabook Pavilion (currently with Windows 10) but something strange is happening.

While I get no problems during the boot and even started installing the OS, right after "Choose if you want to updante and/or install default software"-screen no "Installation type"-screen is offered, instead the Installer is sending me to the Partioning Menu - which is pretty a deadpoint, since every relevant button I click retorn an error. 

I've already tried changing pendrive, changing ISO, changing Ubuntu - using the Unity/defeault instead of GNOME - and even changing boot applications, but none of that works. I also tried using the Try without installing option, which works good until I try to install; then, happens what I described above. Oh, I also tried partioning my HD on Windows and then procceed like it was a dual-boot installation, but the problem persists. 

To be clear, I do not want to dual-boot my laptop: I want it to have, only, GNOME. 

Here are some (low-quality) photos of my screen with additional description: [http://imgur.com/a/o9ddp](http://imgur.com/a/o9ddp)

Additional information: 
- I haven't to deceive UEFI (I think this computer model doesn't even have it, but whatever);
- Except that, the computer works normally. Also, no problems while loading Ubuntu directly from the pendrive;
- One of the ISOs I have tried (the Unity one) worked good on both my friend's computer and my other notebook.

---

### Post by kc1di on 2017-06-19
Hello damnporthos  and welcome to Ubuntu,

I had a similar problem with a friend's hp laptop the solution was to install with the machine disconnected from the Internet and do not choose to do updates or 3rd party software.
the bug has to do with the uefi boot in the Hp's once it installs you can connect it to the Internet and do updates and upgrades and add third party restricted codecs. 
try that.

---

### Post by damnporthos on 2017-06-19
Hello kc1di, thank you for the warming reception.

I just tried your method, but it seems it doesn't work either. The installer is still going to the Partioning Menu and the buttons are all alike.
If the UEFI boot is restricted, may the process run without major issues? If not, remove Windows 10 manually and then boot Ubuntu will work?

---

### Post by kc1di on 2017-06-20
[This thread]("https://ubuntuforums.org/showthread.php?t=2147295") may be of use to you also.  
I really can't see anything on the pictures that gives a clue to the problem. 
hope this helps.

---

### Post by damnporthos on 2017-06-22
I've fixed the problem. In BIOS, I denied every single option available and removed the RAID structure (apparently, my notebook has a default option that join both it's HD and SSD on a RAID). Then, proceed normally and it magically worked. 
Just hoping **** doesn't hit the fan now.

---

