---
title: "Boot Ubuntu LiveCD from PCMCIA flashdisk"
date: 2006-10-02
forum: General Help
---

### Post by bernstein on 2006-10-02
I want to copy the contents Ubuntu LiveCD to a PCMCIA Flashdisk and boot from it.
Why? I only have a 1GB CompactFlash Card and a PCMCIA to CF Adapter, my Notebook only supports booting off PCMCIA or HDD and has no CDDrive. And i want a full Gnome Desktop not using my HDD(noise) with as little fuss as possible.

In [this]("http://www.ubuntuforums.org/showthread.php?t=71567") thread (posts [100]("http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100"), [153]("http://www.ubuntuforums.org/showpost.php?p=1221276&postcount=153") and [158]("http://www.ubuntuforums.org/showpost.php?p=1229101&postcount=158")) people managed to copy the LiveCD to a USB Pendrive and boot from it in persistent mode. Based on this i then managed to hack the initrd.gz to boot it from a Compact Flash card in an IDE Adapter. However i was unable to make it work from a PCMCIA Adapter because :

i need to activate PCMCIA support first... so i included the pcmcia modules into the initrd.gz and loaded them before mounting the filesystem on the PCMCIA as root. After may tries i'm out of options... It simply is unable to find the PCMCIA Drive.... i know it has to be possible as i am able to access the filesystem PCMCIA Disk from a installed Ubuntu.

Please does anyone know how to properly set this up??? Probably i'm missing only a few points. I've really tried to find a solution to this on my own, searching on the net but there was simply not enough info (for me) available to make this happen (yet).

---

### Post by RelativelyQuantum on 2007-06-04
I had the same problem - lack of solid information. This is exactly what I am trying to do, however, and have posted many threads pertaining to the topic. This is one option:

[http://www.logicsupply.com/products/cfdisk_2g](http://www.logicsupply.com/products/cfdisk_2g)

Again, not as convenient, but an option nonetheless.

If anyone checks this thread anytime soon, please help us out. Feel free to benefit from the link as well; we're all in this together :)

---

### Post by kdarkentity on 2007-06-04
what is a PCMCIA flashdisk ...maybe if i knew what that is i cam help ...because im pretty good at configuring usb drives with ubuntu running persistent ...

are u trying to boot fiesty?

---

### Post by RelativelyQuantum on 2007-06-04
I'm trying to configure my pc to boot from a compact flash card in a pcmcia adapter. I would use that in place of a hard drive, since my computer uses 1.8 inch disks; I can't find a compact flash adapter which would fit.

---

### Post by RelativelyQuantum on 2007-06-04
Oh, sorry - the pcmcia post on the side of a computer is just that slot usually used for WiFi cards. Sandisk and others sell compact flash adapters for them.

---

### Post by bernstein on 2007-06-10
Actually i have some more knowledge to share on this :
In my attempts back then i actually was able to setup ubuntu to find the pcmcia stuff at boot time. however It turned out that my laptop had some nasty bios/hardware limits preventing this from ever happening.

how i could confirm that this was never(?) going to happen on my particular notebook : 

1) copied the working live image over from hdd to cf
2) hacked to initrd.gz to detect and mount the cf as root and just after that exit me to a shell
3) booted linux kernel from cf  :  not surprisingly ubuntu couldn't find and mount the cf in the pcmcia port.... > in the shell all my attempts to find anything on the pcmcia device were in vain... it's just as if it weren't in my pc > but there was no other new device wich might be the "lost" pcmcia device > big problem because i
4) copied the linux kernel and initrd.gz back to hdd
5) booted the linux kernel on hdd.... and surprise, surprise... cf in pcmcia adapter gets mounted as root without a fuss.....

---> so my conclusion was that if this is possible it would require quite a bit of kernel hacking and i am just not up to that....besides, since it was a pcmcia device and not a pccard performance was miserable (around 1.5mb/sec) 
--->i just got rid of my hdd and run a normal ubuntu installation from cf in an ide adapter.... :-)

as for a cf-adapter : does 1.8 inch hdd's use the same 44pin ide connector 2.5" hdds use? if yes, you might try the [Addonics-Adapter]("http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp").

---

