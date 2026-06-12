---
title: "Ubuntu doesn't run well, ATI Radeon HD4350"
date: 2015-01-02
forum: General Help
---

### Post by bajah on 2015-01-02
Hey guys,

Here is my situation. I have this hp work computer which was given to me preinstalled with Windows 7. I cleaned the hard drive, removed all partitions and installed Ubuntu 04.14. I had no problems during the installation phase. Rebooted without a problem. Sign-in with out a problem. But as soon as I got to the desktop window I couldn't do anything. The mouse would take an eternity to move just an inch. I wasn't able to open any window, couldn't click on any of the icons. 

I have installed Ubuntu especially 04.10 and 04.12 on other machines before mainly laptops, and never had a problem with speed. The issues that I'm experiencing with this one isn't simply a slow computer it's more than that, the movement of the mouse is delayed way too long. One of the advantages I was told of Ubuntu was that it works great even on old computers. This new experience shocked me. I really like Ubuntu and want to get it working on this desktop.

Ravi

---

### Post by Bucky Ball on 2015-01-02
*Thread moved to **General Help**.*

Welcome. How old is the computer? How low are the specs (amount of RAM and which processor)? Ubuntu may be too heavy for it. Tried Xubuntu or Lubuntu? Did you 'Try Ubuntu' from the install media before the install and experience the same issues?

---

### Post by Sef on 2015-01-02
What are your specs?

---

### Post by bajah on 2015-01-03
Sorry about that guys. My bad.

Computer Type: HP 505B MICROTOWER PC
Processor: Athlon-II X2 255 3.1GHz Dual Core Processor
Memory Card: DIMM 2GB PC3-10600 DDR3-1333
Hard Drive: 250GB SATA
Graphics Card: ATI Radeon HD4350 (RV710D2) PCIe x16 graphics card - 512MB

---

### Post by sudodus on 2015-01-03
Thanks :-)

2 GB RAM is a bit low for standard Ubuntu. It should work, but Lubuntu or Xubuntu will work better.

But with the current information, I think your problem might be the graphics - poor cooperation between the graphics driver and the graphics card.

Have you tried with a proprietary driver? (I use intel and nvidia graphics, but other people know more about Radeon graphics.) Maybe you can try to find something via the software centre.

---

### Post by bajah on 2015-01-03
Hi Sudodus,

I don't understand what you mean when you say "poor cooperation between the graphics driver and the graphics card." Also now that I have completely erased windows off the hard drive all I have on the hard drive is the Ubuntu installation, which at the moment I can't do anything with cause the mouse doesn't move in real time I have to wait like for 10-15 minutes to get any movement from the mouse. With that said I haven't been able to do anything with the installation.

---

### Post by Bucky Ball on 2015-01-03
Try Xubuntu or Lubuntu. The full Ubuntu with Unity desktop environment may be causing the sluggishness. As I asked in post #2, did you try Ubuntu from the install media prior to installing it and did you have the same sluggish mouse issue?

Anyhow, try the other two flavours from the install media and see if it makes a difference.

---

### Post by sudodus on 2015-01-03
> **bajah said:**
> Hi Sudodus,

I don't understand what you mean when you say "poor cooperation between the graphics driver and the graphics card." Also now that I have completely erased windows off the hard drive all I have on the hard drive is the Ubuntu installation, which at the moment I can't do anything with cause the mouse doesn't move in real time I have to wait like for 10-15 minutes to get any movement from the mouse. With that said I haven't been able to do anything with the installation.

The free driver might not work well with your graphics card. You might have better luck with a proprietary driver (a driver from the manufacturer of the graphics card).

-o-

Try Lubuntu and Xubuntu (both 14.04.1 LTS) without installing, running 'live' from the DVD/USB drive! They might work better, at least well enough, that you should be able to move the cursor (mouse pointer).

---

### Post by mörgæs on 2015-01-03
There are no closed source drivers available for this graphics card in the recent Buntus but the open source drivers are getting good, especially in 14.10.

---

### Post by Yellow Pasque on 2015-01-03
I used to have a very similar system (with a RadeonHD 4550 based off the same RV710 core) running Linux. There's no reason that hardware should be struggling running Ubuntu/Unity. 2GB of RAM is sufficient unless you're doing some serious multitasking.

---

### Post by bajah on 2015-01-04
> **Bucky Ball said:**
> Try Xubuntu or Lubuntu. The full Ubuntu with Unity desktop environment may be causing the sluggishness. As I asked in post #2, did you try Ubuntu from the install media prior to installing it and did you have the same sluggish mouse issue?

Anyhow, try the other two flavours from the install media and see if it makes a difference.

Yes I did try to use the install media but it wasn't able to load up, I kept getting an error message.

---

### Post by bajah on 2015-01-04
> **Temüjin said:**
> I used to have a very similar system (with a RadeonHD 4550 based off the same RV710 core) running Linux. There's no reason that hardware should be struggling running Ubuntu/Unity. 2GB of RAM is sufficient unless you're doing some serious multitasking.

It puzzles me just the same. Especially as it was used to run Windows 7 before without any problems what so ever. I completely removed the Windows 7 because I already have Windows on two other laptops didnt want the same system on the desktop. What also puzzled me is that they the running it live aspect didn't work as I would like. It started well and then stop with an error followed by a black screen.

---

### Post by mörgæs on 2015-01-04
No matter what it should be able to run I think we need some more data points. It would be interesting to see how the install of X/Lubuntu works.

---

### Post by bajah on 2015-01-07
Ok guys. Thanks for all the advice. I decided to install Lubuntu 14.04 and it works fine. Mouse moves as it should. Really appreciate the support.

---

### Post by Bucky Ball on 2015-01-08
> **bajah said:**
> Ok guys. Thanks for all the advice. I decided to install Lubuntu 14.04 and it works fine. Mouse moves as it should. Really appreciate the support.

All good news. Could you please mark the thread as solved and post a new one for any further support. ;)

(See the second link in my sig for how to mark as solved.)

---

