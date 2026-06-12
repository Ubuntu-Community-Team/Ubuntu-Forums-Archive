---
title: "IBM T30, 7.04, hangs after Gnome login, no DHCP"
date: 2007-09-16
forum: General Help
---

### Post by kevinfishburne on 2007-09-16
These two problems are probably related since the machine is a clean install with updates installed and nothing else. After installing updates I rebooted and logged in with the default user account. The system hangs with a gray box in the upper-left corner. The attached optical USB mouse moves very slowly, maybe 3-5 frames/second. Interestingly the touchpad moves the cursor normally. I was able to log in once using failsafe Gnome but after that it hangs regardless. I went to console to poke around and noticed it's not getting an IP address. I can ping localhost but nothing else. This is odd because it had an IP address and Internet access when it downloaded the updates, so some update broke that.

Some things I've tried:

*dpkg-reconfigure dhcp3-client*
*ifconfig lo 127.0.0.1*
*dpkg-reconfigure xserver-xorg* and using the vesa driver
logging in to gdm with the root account
logging in to gdm using failsafe gnome
disabling startup scripts using rcconf

I can't reinstall anything because it doesn't have Internet access. I've read several posts that sound like they're the same issue, although none of them mentioned DHCP failure. They all seem to point to lo not being configured properly. One suggested running *ifconfig lo 127.0.0.1* but that didn't do anything.

Any ideas? I sold this on eBay and need to ship it soon so my @$$ is on the line here. I'd installed 7.04 on it before and it had the same problem initially but I can't remember how I solved it. Pretty aggravating...

---

### Post by kevinfishburne on 2007-09-16
Update:

After rebooting with the 7.04 LiveCD in the drive it is hanging in the same way, despite the fact that it worked previously up until installing the updates. I unplugged the wired NIC, rebooted without the LiveCD, and was able to log in. I then plugged the NIC back in and was able to access the Internet after it grabbed an IP address. In network-admin it shows two wireless NICs when there is only one though. It lists them as wlan1 and wifi0. As I understand it from other posts this means two drivers are in use, but for the same device?? Where can I edit the config so that it only uses one driver or the other?

---

### Post by kevinfishburne on 2007-09-16
Praise the invisible man in the sky, I think I figured it out. All I had to do was unplug the NIC prior to rebooting after installing all the updates. For some reason when it woke up with network connectivity after installing the hordes of updates it was unhappy. Strange bug...

---

