---
title: "Wireless internet, turn on PC via  wifi"
date: 2024-06-28
forum: General Help
---

### Post by hakelm on 2024-06-28
I have a rather power hungry PC connected to the internet via wifi. 
Being far away I would like to remotely turn it on via wifi like I could when I had a wired connection.
Part of the solution could be a little Raspberry Pi Zero W I have constantly running nearby. It could be connected to the PC via USB.
But how do I do it?
Thanks in advance for any tip.
H

---

### Post by TheFu on 2024-06-28
I don't think a Pi0 can do what you seek.

I've seen designs for remote KVM devices based on a Pi4 that can power off and on a computer and basically behave like an IPMI connection.  This solution provides a remote keyboard, mouse and video capability, so a Pi that can do those things is required. The video part requires a video capture device, usually HDMI that is supported by PI hardware.  I can't find the design now. Sorry.  A PI-KVM was about $250 when I looked a few years ago - but that was when Pi4 hardware was very difficult to get and was being sold at 2x MSRP.

Ever heard of "the clapper" [https://www.amazon.com/Clapper-Activated-Detection-Appliances-Technology/dp/B0000CGKLR](https://www.amazon.com/Clapper-Activated-Detection-Appliances-Technology/dp/B0000CGKLR) from late night TV?  Perhaps that could work? IDK, but a little speaker and a short audio file could make it work.

Or perhaps a $20 IoT switch port typically used for home automation? [https://www.amazon.com/Smart-Plug-Aoycocr-Control-Function/dp/B07N1JPPXK](https://www.amazon.com/Smart-Plug-Aoycocr-Control-Function/dp/B07N1JPPXK)

To be very, very, clear, I've never used either.  Many PCs won't power on just because the power plug gets electricity. A soft-switch still needs to be pressed.

WoL is something that is built-into most desktop PCs.  This is connected to the eithernet port, so if your Pi-0 has an ethernet port, you can connect that to the "server" and have it send the WoL command over that connection.  I'm sure it isn't THAT easy, since you don't want to use the ethernet for normal networking.  Just put the wired and wireless networks on different private LAN subnets.  If your Pi-0 is wifi only, I don't think that can work.  WoL works over wired ethernet only.  Google found this: [https://www.instructables.com/Raspberry-Pi-As-Wake-on-LAN-Server/](https://www.instructables.com/Raspberry-Pi-As-Wake-on-LAN-Server/)

---

