---
title: "PC keeps resetting after Ubuntu server install"
date: 2007-07-04
forum: General Help
---

### Post by the music man on 2007-07-04
Hi, I have just installed Ubuntu Server 7.04 on an old Pentium 200Mhz, 96MB of RAM. I know that Gnome is too heavy for such old machines, but i want to install the FVWM-Crystal environment. I used Xubuntu before, so i know that the PC can handle the Ubuntu system. When my machine boots, it shows the message that GRUB is loading, followed by "Starting up..." but then my monitor turns black and then the PC reboots again. This keeps going on, even the recovery mode through the GRUB menu doesn't work. Occasionally, i see my monitor showing an "Out of range" message very fast between the starting up message and the reboot (about half a second). What's going on? :confused:

---

### Post by Wiebelhaus on 2007-07-04
sounds like a hardware issue , run full diagnostics.

---

### Post by the music man on 2007-07-04
What diagnostics should i use? I only know memtest, but that's only RAM. What full diagnostics programs (which can boot) do you recommend?

---

### Post by confused57 on 2007-07-04
Maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=490282](http://ubuntuforums.org/showthread.php?t=490282)

---

### Post by the music man on 2007-07-05
I'm trying these steps (from that thread): [http://ubuntuforums.org/showpost.php?p=2371357&postcount=5](http://ubuntuforums.org/showpost.php?p=2371357&postcount=5) but the computer doesn't seem to have an internet connection in the chrooted environment. I'm trying to ```
apt-get update
``` but i get 'can't resolve' errors when it tries to reach the download mirrors. I rebooted and did the steps again, but now at the autmoatic DHCP configuration i hitted cancel and entered my network and ISP information (including DNS servers) by hand, but it still doesn't work. I also entered my proxy through ```
export http_proxy="..."
```. I know that my connection works, by checking ifconfig. Is there some kind of firewall active in the rescue mode of the ubuntu server disc? And how do i disable it?

---

### Post by southernman on 2007-07-05
> **the music man said:**
> What diagnostics should i use? I only know memtest, but that's only RAM. What full diagnostics programs (which can boot) do you recommend?MEMTEST would be best ran overnight (or while your sleeping), to get a good thorough test.

Have you installed any cards in this box recently? Either way, try reseating all addon cards... including RAM.

The next thing to try is a known working PSU. Sounds as if that is your issue from what you describe. You wouldn't have to swap out the PSU, just unplug the old one and plug in the test unit.

Faulty RAM and / or Motherboard can also cause the problem you describe, as well as loose power connectors.

---

### Post by az on 2007-07-05
The server kernel is 686 or better.  A pentium one cannot handle the server kernel.  That's why it keeps rebooting.  It is trying to run instructions that don't exist.

You need to install the generic kernel.  Either boot the installer again and chroot into your newly installed system and run

sudo apt-get install linux-image-generic linux-server-

(linux-server- with the minus at the end will remove that package)

or just reinstall using the alternate cd.  The alternate cd installs the generic kernel instead of the server kernel.

---

### Post by the music man on 2007-07-05
> **az said:**
> Either boot the installer again and chroot into your newly installed system and run

sudo apt-get install linux-image-generic linux-server-

(linux-server- with the minus at the end will remove that package)


That's what i'm trying to do, but my internet connection fails... see my 3rd message in this thread

---

### Post by az on 2007-07-05
> **the music man said:**
> I know that my connection works, by checking ifconfig. Is there some kind of firewall active in the rescue mode of the ubuntu server disc? And how do i disable it?

If your connection is up, then you may have misconfigured your proxy.  There is no firewall preventing you from connecting.

> **the music man said:**
> That's what i'm trying to do, but my internet connection fails... see my 3rd message in this thread

Maybe try reinstalling using the alternate cd?  Or can you download the linux-image-2.6.20-16-generic package from the net and transfer it over using a usb drive?

---

### Post by the music man on 2007-07-06
> **az said:**
> If your connection is up, then you may have misconfigured your proxy.  There is no firewall preventing you from connecting.
I have tried it with and without my proxy, (internet should work in both cases) but i'll try it again today, because my internet acted totally strange yesterday, including on my other PCs.

> Or can you download the linux-image-2.6.20-16-generic package from the net and transfer it over using a usb drive?
That's a good idea, i'll try that with my system rescue cd (has usb support i think).

---

### Post by the music man on 2007-07-06
My system works now, i downloaded the image package, but my usb stick didn't work so i used a share on my windows machine and smbclient. Now i want to install FVWM-Crystal, but my internet connection doesn't work yet. I read that all ports are closed on a standard Ubuntu server install, so how do i open them, or disable the firewall temporarily? (with commands, because the GUI didn't boot, or is there no GUI on Server?)

---

### Post by az on 2007-07-06
> **the music man said:**
> My system works now, i downloaded the image package, but my usb stick didn't work so i used a share on my windows machine and smbclient. Now i want to install FVWM-Crystal, but my internet connection doesn't work yet. I read that all ports are closed on a standard Ubuntu server install, so how do i open them, or disable the firewall temporarily? (with commands, because the GUI didn't boot, or is there no GUI on Server?)

There is no firewall.  The linux kernel routes packets accoding to iptables, but the default rules will not prevent anything.  The "ports closed" saying refers to the fact that there is nothing listening by default.  For example, if you install ssh, then the ssh server will be listening on port 22 and that port will respond.  But ssh is not installed by default.

What kind of network hardware do you have?

---

### Post by the music man on 2007-07-06
I have an ADSL modem on 10.10.10.1 connected to my router on 192.168.2.1 (LAN address, the WAN address of the router is 10.10.10.2) and the server PC is connected with a wire to the router and i have set up the connection with ifconfig on static IP 192.168.2.101 (outside the DHCP range). I'm able to ping to the router, but when i try to ping the modem i get 'network unreachable'. I can ping the modem and anything else on the internet from all my other PCs. The modem is a Copperjet 810, the router is a Belkin F5D7230-4 v1 Wireless 54G. Network card in the PC is a Trust card with Realtek chip. I have placed the server PC in the DMZ of the router but that doesn't help anything.

There were no rules by default in my iptables, i have added ACCEPT rules from source 0.0.0.0 to destination 0.0.0.0 on all protocols both in the INPUT and OUTPUT chain, but that doesn't seem to help.

What else can i do to get access to the net and let apt-get work?

---

### Post by az on 2007-07-06
> **the music man said:**
> I have an ADSL modem on 10.10.10.1 connected to my router on 192.168.2.1 (LAN address, the WAN address of the router is 10.10.10.2) and the server PC is connected with a wire to the router and i have set up the connection with ifconfig on static IP 192.168.2.101 (outside the DHCP range). I'm able to ping to the router, but when i try to ping the modem i get 'network unreachable'. I can ping the modem and anything else on the internet from all my other PCs. The modem is a Copperjet 810, the router is a Belkin F5D7230-4 v1 Wireless 54G. Network card in the PC is a Trust card with Realtek chip. I have placed the server PC in the DMZ of the router but that doesn't help anything.

There were no rules by default in my iptables, i have added ACCEPT rules from source 0.0.0.0 to destination 0.0.0.0 on all protocols both in the INPUT and OUTPUT chain, but that doesn't seem to help.

What else can i do to get access to the net and let apt-get work?

Did you edit /etc/network/interfaces?  Or did you set up a static address using the installer?

You usually connect using 

sudo ifup eth0

and disconnect with

sudo ifdown eth0

I can't be any more help than that, at this point...

---

### Post by the music man on 2007-07-06
I have set this in interfaces:
```
iface eth0 inet static
 address 192.168.2.101
 netmask 255.255.255.0
 gateway 192.168.2.1
```
I am able to ping the modem now. But when i check connection to the internet with 'tracepath www.ubuntu.com' i get: 'Host name lookup failure'. It seems that there is no DNS server configured. Where (in what configuration file) can i do this?

I also tried dhcp:
```
iface eth0 inet dhcp
 hostname server
```
When i now do 'tracepath www.ubuntu.com' it gets to the modem but not further:
1 192.168.2.101
2 192.168.2.1
3 10.10.10.1
4 No reply
5 No reply
...
What does this mean?

I also discovered that at the time i'm pinging and trying, log entries appear in my router that say that various IP addresses are being blocked by DoS, like this (i'm hiding the ip):
```
Fri Jul 6 14:50:33 2007 1 Blocked by DoS protection ***.***.***.***
```
Does this mean anything for the problems with the pc?

---

