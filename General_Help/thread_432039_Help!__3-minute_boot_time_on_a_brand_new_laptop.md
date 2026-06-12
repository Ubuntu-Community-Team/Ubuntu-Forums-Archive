---
title: "Help!  3-minute boot time on a brand new laptop"
date: 2007-05-03
forum: General Help
---

### Post by stevo123 on 2007-05-03
I've got a Sony VGN-FE880E  2gbmem, 1.66 ghz proc Duo Core.  120 gig hard drive.  Dual booting Vista and Feisty (64 bit).  Boot time for ubuntu takes longer than vista.  This can't be right, can it?  Any suggestions?

---

### Post by rich.bradshaw on 2007-05-03
sudo apt-get install bootchart

restart

in nautilus go to /var/log/bootchart

there will be a diagram of how it booted, and what opened when. Have a look or post that file here and we can tell you how to fix it.

Bet it's dhcp... post the file and we can tell you for sure...

---

### Post by stevo123 on 2007-05-03
Thanks for the quick reply.  I installed bootchart, and have attached the image file.  Let me know what you think.
Thanks,
Steve

---

### Post by ashz on 2007-05-03
looks like it took 1:42 to boot..lol

but i cant see whats wrong sorry

---

### Post by qpwoeiruty on 2007-05-03
There´s one big thing there. Networking takes about 1:07 to start. If you set a static IP (no DHCP) and remove ipv6 support (if you don´t need it), you should see the boot time dramatically decrease.

System/Administration/Network is where you can change to a static IP

IPv6 can be disabled by:

```
sudo gedit /etc/modprobe.d/aliases
```
Find *alias net-pf-10 ipv6* and change it to *alias net-pf-10 off*
Save and reboot!

PS: Also check to make sure that Firefox has ipv6 disabled also: enter ¨about:config¨ into the address bar and search for ipv6 and make sure that network.dns.disableIPv6 is set to true

Good luck!

---

### Post by stevo123 on 2007-05-03
OK, i disabled ipv6 via cli. as well as in firefox.  
Saved, Rebooted.  Long boottime.
Tried to change to static IP address, and wpa2 is not listed as a protocol.  The only 2 available on static addresses is WEP ascii, and WEP hexadecimal.  Is there another way to enable static ip addresses that would utilize wpa2 (which is recognized as a protocol when in dhcp mode)?
Again, thanks for all your help.

---

### Post by qpwoeiruty on 2007-05-03
IPv6 isn´t directly related to the long boot time, but it helps with name resolution - eg. type a name of a website into FireFox (without the .com,.org, etc). With IPv6, it takes **forever**. Without, it goes straight to the right page!

A static IP is where you should see a drop to ~30-40s boot.

It seems the Network Manager in Feisty has a bug setting up static IPs with WPA. I´ll look into it some more and post back. So far, downgrading the NM to Edgy´s version seems to be an answer...

Ed: Here we go. wpasupplicant and [this howto](http://ubuntuforums.org/showthread.php?t=202834) should work.

---

### Post by stevo123 on 2007-05-04
Thanks so much.  I'll try it when I get home and post the results.
Steve

---

