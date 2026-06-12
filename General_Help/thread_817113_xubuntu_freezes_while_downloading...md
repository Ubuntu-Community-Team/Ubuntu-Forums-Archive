---
title: "xubuntu freezes while downloading.."
date: 2008-06-03
forum: General Help
---

### Post by BSMan on 2008-06-03
hi everyone
a couple of days ago, ive installed the xubuntu 8.08 (something like that) in my computer, as a dual boot system.
the problem is that every time im trying to download something (like openoffice) or update the system (or even when im just surfing the internet sometimes), the system freezes after  a while, and i have to restart my computer to get it work again.

 - im pretty shore it freezes while im on the internet, because i did some tests.. i started the system and waited about half an hour without doing nothing, and it was all ok.. then i played chess for about half an hour, and nothing happened. but then i tryed to download update, and it stucked..

 - i really dont thing this is a hardware problem, but that is my specs anyway:
pentium 3 1 GHZ
RAM 256MB
VGA GF 2 mx440
xp is working perfect on that computer...

 - when the system freezes, the 3 LED in my keyboard are turning on and off (forgot the word XDDDD).. wired..

thankes alot,
              ben

---

### Post by bingoUV on 2008-06-03
very likely network card problem. Wired or wireless? Which model of network card? Did you have to do something to make your network card work in Xubuntu, or did it work in the fresh Xubuntu install?

---

### Post by BSMan on 2008-06-03
i have a wireless card, edimax 802.11g card. it warked perfectly without doing anything.. 

i really dont think thats the problem, becuse i bought that card half a year ago..

---

### Post by bingoUV on 2008-06-03
Linux driver for the network card could be faulty. Now you have said that it is wireless, so my suspicions on the card have doubled. Most manufacturers do not create linux drivers, or create horrible drivers. 

Search this forum, and the wide internet if this card works well with linux. Include exact model number to be sure. Could be that edimax is just the supplier but chipset of the card is manufactured by some other company. So, you will need to search for the chipset. You can find the chipset by the looking in the following command's output : 
```

sudo /sbin/lspci

```

---

### Post by wpshooter on 2008-06-03
What browser are you using with Xubuntu ?

Have you tried to change to another browser ?

I have read somethings about the latest version of Firefox that comes with the Ubuntu version is causing some problems.  I don't really know if the same is true with whatever browser comes with Xubuntu.

---

### Post by bingoUV on 2008-06-03
happens with system updates too, so browser may not be the problem.

---

### Post by BSMan on 2008-06-03
i tryed to download from firefox and epiphany something.. so i dont thing thats the problem.. but thank u anyway..

and bingoUV - thank u so much for the help..

i have another question:
can i browse my xp files from the xubuntu? (i have a dual boot..)

---

### Post by aaronhahn777 on 2009-03-28
BSman:

I have the same problem... and the exact same wireless device.  According to this website (sells ONLY out-of-the-box compatible linux devices) the Edimax 802.11g is compatible:
[http://www.linuxemporium.co.uk/products/wireless/#pid88171](http://www.linuxemporium.co.uk/products/wireless/#pid88171)

I've spent hours using ndiswrapper with other devices (such as D-Link) but they are all kinda flaky.  So far this one has been the best... but now it's starting to freeze up.

Could there have been an update to Ubuntu's standard driver packages?  I'm running 8.10 and I have read several posts of people having excellent results with this device.

---

### Post by aaronhahn777 on 2009-03-28
I've been surfing around and I keep hearing a similar suggestion...

...first off, I'm also running a PIII and I imagine you don't have usb 2.0.  So, i think Xubuntu could be trying to use USB 2.0 and causes a problem.  Does a USB memory stick often slow down too? (mine would often slow to 5% of the usual rate).

I'm pretty sure it's a USB issue.  The attached is a clip from another site:

Quoting:
> "...Some users report randomly disconnecting USB devices, especially external hard drives. One solution is to start the system with the option "irqpoll" in grub, but this doesn't work for everybody, and is believed to make the whole system slower. The other solution is to disable USB 2.0. This will result in way slower read/write, but the connection remains stable.

To disable USB 2.0, type this in the terminal:

```
sudo modprobe -r ehci_hcd
```

Test if the copy/write process is stable, and if you want to disable USB 2.0 upon boot, type:

```
sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r`
```


I'm going to try temporarily disable USB 2.0 as a test...  I'll let you know how it goes.

---

### Post by aaronhahn777 on 2009-03-31
mmmm... not so good.  Didn't seem do do anything really.  Still searching for a solution to this.

---

