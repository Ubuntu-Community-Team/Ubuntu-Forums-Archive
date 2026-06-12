---
title: "[SOLVED] Saned and Xubuntu; how to do it?"
date: 2008-01-01
forum: General Help
---

### Post by JKyleOKC on 2008-01-01
I've installed Sane and Xsane on one of my Xubuntu boxes, and they work fine (after replacing the standard kernel with the modified one that does not have USB_SUSPEND in it). I've also followed the steps found in the forum here for making Saned work, and have changed the port_sane file in xinet.d to have my own user name and "scanner" as the group. Netstat shows that the port is listening. However none of the Win98SE machines on my LAN can access the scanner. One of them has Xsane for Win32 installed and the other has SaneTwain, and both are configured per instructions.

My question, first, is "How do I go about troubleshooting this?" since telnet makes a connection but nothing comes back.

I've read all five of the "similar threads" but none seem to quite fit the situation here...

If it's pertinent, the scanner is a Umax Astra 3450 and it uses the plustek backend. It connects via USB. As I said, it works perfectly with the local Xsane and Gimp plug-in; it's just Saned that is driving me bonkers.

Solution: I feel quite stupid. I hadn't installed xinetd on the Xubuntu box, so of course nothing could connect. Once I added xinetd, it began working properly with SaneTwain. However, Xsane for Windows still does not work and locks up the system it's on, complaining that a needed file for Pango (whatever that may be) is missing. Now that SaneTwain is working, though, that's no major problem...

---

### Post by Waylan on 2008-03-01
> **JKyleOKC said:**
> If it's pertinent, the scanner is a Umax Astra 3450 and it uses the plustek backend. It connects via USB. As I said, it works perfectly with the local Xsane and Gimp plug-in...

I have a Umax Astra 3400 which uses the same backend. However I can't seem to get mine working at all. What was the trick?

'sane-find-scanner' correctly reports:

```
found USB scanner (vendor=0x1606, product=0x0050) at libusb:002:002
``` 

But xsane and scanimage report no scanners found.

I tried editing "/etc/sane.d/plustek.conf" and added the following:

```
[usb] 0x1606 0x0050
device libusb:002:002
```

But that made no difference. I belong to the 'scanner' group as well. I even checked that "plustek" was listed in "/etc/sane.d/dll.conf" and that 'man sane-plustek' does in fact list my scanner with the correct vendor and product ids. What am I missing?

---

### Post by JKyleOKC on 2008-03-06
Have you tried re-booting with the scanner plugged in and powered up? I've found that this is the only way I can get the remote connection to find the scanner, although the local Xsane has no problem with it being fired up later. The USB area seems to be more than slightly flaky, still...

I also found it necessary to change the sane-port entry in xinetd's configuration to be user root and group root, rather than the default values. While this is a bit of a security risk, it was the only way to get the system working -- and xinetd is restricted to the local network addresses so it's not available to intruders.

---

