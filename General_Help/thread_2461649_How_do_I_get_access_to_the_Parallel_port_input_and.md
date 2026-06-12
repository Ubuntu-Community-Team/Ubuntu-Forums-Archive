---
title: "How do I get access to the Parallel port input and using bash scripts?"
date: 2021-05-04
forum: General Help
---

### Post by adrian-h on 2021-05-04
Not sure if General is the correct forum,  so if wrong please move, but I doubt this is a hardware issue.

Ubuntu 20.04 minimal install on headless Thin client.

Going back to around 2013 I could use a Linux package called parashell and pin to gain access to the parallel port using bash scripting, the two packages would allow me to write byte's to the output pins and read the input status pins of the port.

I get the impression things have changed and as a standard user I can no longer do this.  Most of the posts I have found are from years in the past and some later ones suggested that access to the port is now only through the kernel.  After a couple of hours trying things out I am a bit lost.  Could someone please point me in the correct direction, are there any Ubuntu packages that allow me to do get this functionality.

Just a project for simple automation and adding a A2D circuit to the parallel port.

TIA

Adrian

---

### Post by him610 on 2021-05-04
I believe it can be downloaded from SourceForge...
[https://sourceforge.net/projects/parashell/]("https://sourceforge.net/projects/parashell/")

---

### Post by adrian-h on 2021-05-05
Yes it can be downloaded from Souceforge still and I tried that, but the latest update on that project seems to be around 2010 although still working and being discussed in Feb 2014, which I think is before changes in the kernels locked out direct access to ports for security reasons, or that is what I gleaned from reading various threads last night before I got confused on the whole thing.

I am hoping that someone is playing with direct port access for automation or for the fun of it and could point me in the correct direction with something that would work on today's distro's.  One option would be to go back to an old distro with earlier Kernel I think I was using Precise Puppy at the time.

Adrian

---

### Post by HermanAB on 2021-05-05
You have a machine with a parallel printer port that still works???

Anyhoo, see this for a more modern solution to pin I/O.  It may also give you some clues on how to do what you want:
[https://www.aeronetworks.ca/2015/01/serial-port-io.html](https://www.aeronetworks.ca/2015/01/serial-port-io.html)

---

### Post by GhX6GZMB on 2021-05-05
Is this an ECP port? Rare as hen's teeth nowadays.

---

### Post by adrian-h on 2021-05-05
The computer is a small HP Thin client a T5550, think it was around £30 with power supply delivered when I got it, the processor is not fantastic being a VIA Nano u3500 at 1GHz.  So a 64 bit single core processor.  It came with 2 Gig memory and a small 2 GB flash drive, but I added a 4 GB memory and a 2.5" 160GB SATA drive, it's fanless and a nice small form factor and Built in Network card, RTC, 6 USB 2.0 ports, PS/2 Mouse and Keyboard ports. basic sound system. Two DVI Video ports.  Parallel and serial ports.  The parallel can be the old Standard, or,  ECP or EPP or ECP/EPP selectable in Bios, you can even fit a Wi-Fi card in the PCI-E mini socket.  So I thought it would make a good home automation unit, or something to play with that had access to all the Ubuntu packages rather than a raspberry PI.

I wanted to monitor a couple of External DC voltages and found a circuit to tag on an 8 input 12 bit A2D to the parallel port, thinking it would be the similar to what I did back in 2013, still stuck, the USB stuff above sees to be for the FTDI chip sets built into the USB devices after a quick look. Perhaps I can find some A2D USB devices I can use that are not the lets monitor how mucgh current another USB device is taking from me, some thing I can interrogate remotely or with a bash script can message me.  I am only just capable of a bit of scripting after much effort.  C prog is probably pushing it.  :)

Adrian

---

