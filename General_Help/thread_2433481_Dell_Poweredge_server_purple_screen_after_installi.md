---
title: "Dell Poweredge server purple screen after installing any GUI to Ubuntu Server 19.10"
date: 2019-12-19
forum: General Help
---

### Post by bomblord on 2019-12-19
Hello all, I have a Dell Poweredge R710 server with 48GB of RAM, 2 physical Xeon E5620 CPU's.

I can install the Ubuntu Server with no issue but the person I'm working is requesting a GUI to interact with it. This is typically as simple as sudo installing a GUI of preference (ex Ubuntu-desktop) but every time the install finishes the system is exclusively booting to a purple screen. At first I just let it sit assuming that it may still be configuring/loading but after 2 hours it still didn't show anything so I rebooted and had the same problem. I've googled the issue and found a few people with a similar problem that ranged from a Raspberry Pi install that didn't support the GPU to an update breaking the install but none of what I've found seems usable for a fresh x86 install. I've re-installed multiple times now and also tried a different GUI environment (lubuntu) but none of what I've used is working any assistance on this would be greatly appreciated.

---

### Post by mörgæs on 2019-12-20
Hi, welcome to the fora.

First let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Servers often have a weak graphics processor.

---

### Post by bomblord on 2019-12-21
> **mörgæs said:**
> Hi, welcome to the fora.

First let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Servers often have a weak graphics processor.

I appreciate the response the paste was too large for here so I stuck it in pastebin
[https://pastebin.com/Aw974Jig](https://pastebin.com/Aw974Jig)

---

### Post by mörgæs on 2019-12-21
[https://www.matrox.com/graphics/en/press/releases/2018/g200-20-year-anniversary/image.html](https://www.matrox.com/graphics/en/press/releases/2018/g200-20-year-anniversary/image.html)

I think you will be better off with adding a cheap second hand graphics card from AMD or Nvidia if there is space in the cabinet for this.

---

### Post by bomblord on 2019-12-21
There's space but no power connectors. I have a literal pile of GPU's that are powered from the PCIE without external power but all the PCIE connectors in this server's board only output 25W instead of 75

---

### Post by TheFu on 2019-12-21
I suppose telling the other person that ssh is a GUI isn't a viable option?
Nobody is actually sitting at the system, are they? All access is using a DRAC or network connection, right?

---

### Post by bomblord on 2019-12-21
I've been fiddling around with using tighvnc/realvnc but I keep getting a fatal error when trying to launch it on the server. I'm certain that it won't be ideal for the person in question but I might be able to push it as a solution.

---

### Post by TheFu on 2019-12-21
> **bomblord said:**
> I've been fiddling around with using tighvnc/realvnc but I keep getting a fatal error when trying to launch it on the server. I'm certain that it won't be ideal for the person in question but I might be able to push it as a solution.

I use x2go.  Works over an ssh tunnel, which is built into the protocol. Bonehead simple and as secure as ssh.  Just need to NOT use Gnome3 or any other heavy GUI.  Works well with xfce, mate, lxde, straight openbox and fvwm.  I've never tried kde, but there is a setting for it too.  Use the x2go PPA if you go this way, then turn down the bandwidth and make the image compression 4k-jpg. Works wonders.

x2go feels 2-3x faster than any VNC or RDP solution I've seen on Linux. There are faster, paid, proprietary solutions, if you want to go that direction.  I've seen those stream hidef video over 1000 miles away.

There's always the option of putting their stuff into a VM (best practice usually), then using the SPICE display protocol. I find it a little funky (odd select/paste in my setup), but lots of people are happy with it.  

Just throwing out some other options.

---

### Post by SeijiSensei on 2019-12-22
Most Dell servers have generic Intel graphics.  My T30 has "Intel Corporation HD Graphics 510 (rev 06)."

Why not install a desktop version, then add the server software you need?

---

### Post by mörgæs on 2019-12-22
This one has a Matrox MGA G200eW. I doubt that it can run a standard desktop but yes, one could try.

---

### Post by SeijiSensei on 2019-12-23
[https://www.matrox.com/graphics/en/support/drivers/latest/](https://www.matrox.com/graphics/en/support/drivers/latest/)

There is a driver for that card from 2006 (both 32- and 64-bit).  My 19.10 release appears to have Matrox drivers as well.  See /usr/lib/modules/...-generic/kernel/drivers/video/fbdev/matrox.

I built a router/gateway for a client on an R410 which had the same graphics. We're only using it in text mode though, so I never tried the video driver.

A quick glance at the specs shows it has four PCIe slots. Maybe you could just throw a [cheap NVIDIA card]("https://www.newegg.com/evga-geforce-8400-gs-01g-p3-1302-lr/p/N82E16814130585") in there?

I'd boot up a desktop installation disk and see what happens.

---

