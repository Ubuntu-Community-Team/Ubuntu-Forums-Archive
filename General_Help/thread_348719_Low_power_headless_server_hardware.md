---
title: "Low power headless server hardware"
date: 2007-01-29
forum: General Help
---

### Post by flightmaker on 2007-01-29
I want to build a low powered, headless server for use at home, to pick up and sort email, service the printer, provide backup storage, etc.

What I've come down to is a choice of two likely motherboards:-

EPIA CN10000E-RS Fanless
Jetway J7F2 1.2GHz fanless EDEN

Has anybody got experience of using Dapper Drake Server on either of these? Any problems?

I intend to use a SATA hard drive, hence my interest in these particular boards.

---

### Post by stuarttaylor on 2007-04-18
Hi there,

I am also looking at doing the same sort of thing using the Jetway J7F2 1.5Ghz motherboard, and SATA hard-drive. I intend to set up a small web server for development that I can leave on all the time without driving my electricity bill through the roof.

Have you put your system together yet? I was wondering how well Ubuntu/Xubuntu operate on these motherboards. 

Looking through the archives I see that there were issues using Xubuntu relating to the graphic and sound devices.

Have these issues been sorted in Edgy or Fiesty???

---

### Post by flightmaker on 2007-04-18
I have now bought some hardware - the mainboard (fanless Jetway), memory and the power supply. These I hooked up spread about on the table top to an old PATA HDD and installed Kubuntu Dapper Drake, on the principle that if it can run Kubuntu (it does, slowly) it should have no problems with Ubuntu Server. I left the system running for a week just to make sure nothing fails prematurely, then stripped it down and put the parts away again to keep them away from beer and red wine.

What I'm doing when I get time is designing my own case. I want it to be as small and low profile as possible, fitted around the motherboard, power supply and hard drive and nothing else. I also need to make up the PCB to hold the front panel switches and LEDs. That's intended to connect to the 10 way header with a ribbon cable and IDCs. The cable that comes with the mainboard, for connecting a serial port to the back panel looks like it will be very suitable for this, following surgery to amputate the D connector and add a matching IDC.

I'll hold off buying the hard drive until I'm ready to install it - the prices are dropping all the time and there's no point having it sitting around doing nothing. The 500G Seagate SATA drives are looking attractive.

IMHO I think the fanless processor is probably better unless you really need that extra little bit of power. It's one less moving part and a little less noise if the machine is in a domestic environment.

---

### Post by stuarttaylor on 2007-04-18
Was Kubuntu really that slow? What are the minimum requirements for Kubuntu and Ubuntu? Perhaps Xubuntu maybe the better option as it is tailored towards older/slower hardware.

I like the idea of having a fan as a backup in case my needs (master plan) change. I can always unplug it or change the heatsink if it really becomes a problem. Plus the unit will be stuck in a cupboard out of the way so noise isn't too much of an issue.

I have a very active 4 month old son who I'm sure will be creating more noise anyway ;-)

---

### Post by flightmaker on 2007-04-18
Not Kubuntu, Kubuntu running on this hardware. Remember I'm used to using KDE on a 3GKz P4 with 2G RAM. Everything is relative.

I'm aiming to have the case as air tight as I can get it, except for the power supply fan vent at the back, and ventilation holes at the front so that the power supply fan pulls air in past the hard drive and over the processor heat sink.

---

