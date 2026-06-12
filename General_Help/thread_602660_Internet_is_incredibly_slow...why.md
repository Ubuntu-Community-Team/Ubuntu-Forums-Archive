---
title: "Internet is incredibly slow...why?"
date: 2007-11-04
forum: General Help
---

### Post by kschmitt289 on 2007-11-04
Hello,
I'm new to Ubuntu, and I have been having trouble with my internet. It is incredibly slow. It was fast when I was running Vista, and the same internet connection is fast on my PC, which is running XP. Is there a way to get it running faster? Any help is greatly appreciated.
Thank you,
Kevin

---

### Post by agurk on 2007-11-04
Hi, we need more info, could you please tell us a bit about your hardware?
Posting the output of the 'lspci' command would likely be helpful.

---

### Post by kschmitt289 on 2007-11-04
Here is the output to the 'lspci' command:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Hope this is helpful to help me. If any other information is needed to try and help me, just let me know.

Thanks in advance,
Kevin

---

### Post by minus198 on 2007-11-04
If you are using the wireless its possible that its connected to someone else's Wireless...

---

### Post by kschmitt289 on 2007-11-04
I'm running a wired connection right now, and it is very slow. When I try to run wireless, it locates my network and connects, but it won't allow me to connect to the internet.

---

### Post by agurk on 2007-11-04
Have you applied any updates since installing Gutsy? There was a glibc update released recently that dealed with an IPv6 regression. I know your Internet access is very slow, but it's still worth a try. Go to System --> Administration --> Update Manager and grab the 'glibc' update if you haven't already.

---

### Post by kschmitt289 on 2007-11-04
I have all of the updates available at this time.

---

### Post by mpokrywka on 2007-11-04
Does this:
```
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/tcp_window_scaling'
```
help?

---

### Post by agurk on 2007-11-04
It seems to be a common problem, all sorts of fixes are being suggested, try these two:

[http://ubuntuforums.org/showpost.php?p=3692346&postcount=162](http://ubuntuforums.org/showpost.php?p=3692346&postcount=162)
[http://ubuntuforums.org/showpost.php?p=3688851&postcount=15](http://ubuntuforums.org/showpost.php?p=3688851&postcount=15) (it's what mpokrywka is suggesting above. the ikus060 guy later upgraded his router firmware, which solved the problem)

---

### Post by kschmitt289 on 2007-11-04
I tried all three of the suggestions, and none of them seemed to have worked. I could not change the items to 0 in the sudo gedit /etc/sysctl.conf document, because they were not in the document.

---

### Post by agurk on 2007-11-04
Sorry, yeah, you're right, you need to add them to the file and reboot.

run:
```
sudo gedit /etc/sysctl.conf
```

add:
```
net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 0
```

reboot.

---

### Post by kschmitt289 on 2007-11-04
Where exactly should I be adding these codes? To the bottom or somewhere else in the document? The document looks like this, and I don't know if I should just put it at the bottom or what.

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

---

### Post by agurk on 2007-11-04
Yes, add the new rows to the end of the file.

---

### Post by kschmitt289 on 2007-11-04
Unfortunately that did not work either.

---

### Post by agurk on 2007-11-05
Alright, time for some lateral thinking.

Let's forget about the wired connection for a moment (Broadcom gear can be dodgy stuff) and instead focus a bit on your wireless Intel 3945ABG rev 2. It's a well supported wifi chipset that I'm using myself.

1. Go to System --> Administration --> Restricted Drivers Manager, and make sure the driver is enabled and in use. If not, enable it or manually install linux-restricted-modules (which is what I had to do after upgrading from 7.04).
2. Disconnect your wired adapter and instead connect using your wifi. Use 'ifconfig' to check that you have an IP address assigned to the interface.
3. Use 'iwconfig' to see what network you have connected to, if any.
4. Try 'ping google.com' to see if the address resolves. If not, try 'ping 72.14.207.99' to check for connectivity.

Depending on the outcome of the above, I have a couple of ideas on how to proceed.

---

### Post by volksman on 2007-11-05
what does ethtool report for speed duplex on the card:

```
 ethtool eth0
```

Sub in the ethX of your device....

---

