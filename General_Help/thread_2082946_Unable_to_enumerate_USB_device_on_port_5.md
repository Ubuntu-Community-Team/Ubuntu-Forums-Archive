---
title: "Unable to enumerate USB device on port 5"
date: 2012-11-11
forum: General Help
---

### Post by deadmantfa on 2012-11-11
HI Everyone,

I have a HP DV6 laptop and since i have installed 12.10 I am getting this error in my syslog and the file is growing exponentially

**unable to enumerate USB device on port 5**

I need help resolving this problem i searched almost everywhere but did not find a solution

This error is mentioned earlier by other users but non have been solved please

**While searching I came across that its got something to do with ehci_hcd**

---

### Post by 2F4U on 2012-11-11
What device is connected to this port? What kind of USB port is it (1.1, 2.0, 3.0)?

---

### Post by deadmantfa on 2012-12-09
Sorry for the delayed reply and thank you for helping me out

The only thing connected is my logitech M195 wireless mouse and it is a usb 2

---

### Post by jim_deadlock on 2012-12-09
I struggled with this kind of problem for many months with my external HDD, I tried the ehci_hcd route and all that kind of stuff without success, it was a very frustrating time.

Anyway, in the end I decided to hell with it and I cracked open the plastic casing and tried using it as a normal SATA drive connected directly to the motherboard and it worked flawlessly. The conclusion was that the USB connector had simply worn out and the computer could no longer detect it. So if you've been plugging and unplugging your USB port, either the connector on the cable or the USB port itself may be worn out.

---

### Post by thunderbird32 on 2012-12-10
I have the exact same problem, but I don't have anything connected to the USB ports at least to my knowledge. I'm guessing something internal is connected via USB (the webcam, touchpad, etc.) I don't think I've got a bad USB port though, I previously had Xubuntu installed and I never got this error. Nor did I get it on FreeBSD. I'm currently trying to install Ubuntu Server, so I can install just the software I want, and this is incredibly frustrating. I can't even really use the command prompt because this error just fills the screen within seconds.

---

### Post by thenoname on 2013-03-10
> **thunderbird32 said:**
> I have the exact same problem, but I don't have anything connected to the USB ports at least to my knowledge. I'm guessing something internal is connected via USB (the webcam, touchpad, etc.) I don't think I've got a bad USB port though, I previously had Xubuntu installed and I never got this error. Nor did I get it on FreeBSD. I'm currently trying to install Ubuntu Server, so I can install just the software I want, and this is incredibly frustrating. I can't even really use the command prompt because this error just fills the screen within seconds.
What kernel version was it with your Xubuntu, and what Xubuntu ver was that?? I am having same problem, with my webcam, I have search a lot and still no way to solve the problem. Frustrated!!!

---

### Post by kurt miller on 2013-04-02
FWIW: I was having this problem too.  I did a tail -f /var/kern.log and then started re-plugging usb devices until I found the culprit which ended up being the external hard drive.  After I cycled the power on the external hard drive it cleared. I think this may have started after I upgraded [COLOR=#000000][FONT=UbuntuBeta Mono]gvfs-mtp but I'm not certain.[/FONT][/COLOR]

---

