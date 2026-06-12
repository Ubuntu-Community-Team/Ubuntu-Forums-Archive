---
title: "Packard Bell EasyNote XS"
date: 2008-01-08
forum: General Help
---

### Post by reza81 on 2008-01-08
Hello,
I would loke to buy a EasyNote XS & I need to know how Ubuntu compatible it is! 

Is there anybody who has any kind of expiriace with the EasyNote XS
```

Operating System 
Operating System Genuine Windows® XP Home Edition 
Chassis 
Chassis dimensions 230x171x29mm 
Weight 950g 
Processor 
CPU Model C7-M 1.2GHz 
Cache 128kB 
Bus Speed 400MHZ 
Memory 
Installed memory 1024MB DDR 
Hard Disk Drive 
HDD size 30GB 
Card reader / Floppy drive 
Card reader 4 in 1 card reader 
CD-RW / DVD-RW 
Optical drive NO (sold separately) 
Graphics 
Chipset VIA VX700 upto 128MB shared 
Screen 
Internal resolution 800x480 
Monitor size 7" 
Technology and ratio TFT  
Sound 
Integrated on motherboard or on PCI Slot Integrated 
Communication 
Modem No 
Ethernet 10/100 LAN 
WIFI YES 
Connectors 
USB Port (total/front/rear) 2 x USB 2.0 
TV out NO 
DVI Yes 
Audio out YES 
Microphone IN YES 
Headphone out YES 
Keyboard and pointing device 
Keyboard type 90 Key Qwerty 
Accessories 
Accessories VGA Webcam 
Bluetooth YES 
Warranty 
Standard warranty 1 Year Standard 

```

---

### Post by duckthvader on 2008-01-09
Assuming I would somehow manage to install Linux on it, I couldn't resist the temptation to buy one. Alas, it ain't that easy :(
I created an Ubuntu pen drive , which my HP Pavillon dv1000 graciously booted from, but the EasyNote just won't boot from the pen drive, even though the phoenix bios will let you change the boot order to include the usb stick.

So far, I've been able to find one [post ]("http://data.plaintext.cc/nanobook/")where someone had been able to install Debian on that box, albeit not Ubuntu, and with major driver issues related to display and wifi. So it doesn't seem to be impossible, but definitely not for the faint of heart.

For the time being, I've limited myself to running XP on it, until I find some more time, or someone else comes up with a solution. Needless to say, XP runs like a dog. 

Hope this helps

---

### Post by duckthvader on 2008-03-26
After failing on the pen drive, tried Ubuntu 7.04 , 7.10 , and 8.04 beta life cds. Results were mixed:
- 7.04 ran , including wifi, but sound didn't work
- 7.10 crashed
- 8.04 seemed to work fine, so installed it. First impressions:
huge performance improvement over preinstalled XP.Overall, system works fine, with satisfactory performance and display characteristics. No problems with wifi or sound drivers, even flash works fine.
Things that don't work : 
- display resolution cannot be changed. Actually only a minor problem, as standard resolution sufficient.
- audio output only works on built-in speakers. Hooking up headphones or external speakers will mute internal speakers, but not redirect output to external sink. PulseAudio problem ?

---

### Post by BartNotelaers on 2008-04-14
My EasyNote XS20-005 **can** boot from USB (but not all USB drives i have can be made bootable), using the instructions on [this distribution's wiki ]("http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive#Method_I"). Using [Syslinux]("http://syslinux.zytor.com/wiki/index.php/SYSLINUX#NT.2F2K.2FXP") you can set the USB partition to "bootable" or active.

This EasyNote can boot over network as well (NIC is shown in boot list). I have neither tried this nor if the laptop can boot from SD/MemoryStick in builtin cardreader.

I am now waiting for a 4Gb USB key i ordered to back up the Packard Bell restore-partition ("you need a partition of at least 2Gb" but how large is their 2Gb..?) , so after i did that i will post more about how the Ubuntu installation went.

Edit ; 
I used "Packard Bell Smart Restore" to back up the complete system, in order to reinstall default OS, settings and programs if necessary. 
Installing Ubuntu is a problem because of the "VIA S3G UniChrome Pro II IGP" adapter ; after printing all kinds of lines with the loaded modules etc, the screen is blank save for a flickering purple , and not seeing anything i cant proceed... will open a new thread for this problem.

---

