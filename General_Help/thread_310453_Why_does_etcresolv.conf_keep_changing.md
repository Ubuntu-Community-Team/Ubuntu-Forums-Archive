---
title: "Why does /etc/resolv.conf keep changing?"
date: 2006-12-01
forum: General Help
---

### Post by Steve Pullman on 2006-12-01
I was trying the desktop amd64 version of edgy.
First of all I couldnt access any repo's, so (as root)
echo "blacklist ipv6" >> /etc/modprobe.d/blacklist
then 
vi /etc/resolv.conf
to change the nameservers (I'm behind an ADSL router).
Then a reboot.
But lo! /etc/resolv.conf had changed back to what it was.
OK, perhaps I messed up.
sudo su
cd /etc
vi resolv.conf
edit as needed.
Good :) now I can apt-get update, etc.
Then I had to go back to XP for something.
On my return to ubuntu I find, to my horror, that /etc/resolv.conf has changed again! Changed back to its original and incorrect form.
<minor rant on>
So what is doing this? How can root files be changed like this?
It makes a mockery of the concept of file permissions and security.
Suffice to say that I'm not impressed.
So <minor rant off> is this just an edgy problem?

---

### Post by halfvolle melk on 2006-12-01
I don't know why, but it explicitly warns for this in the file itself. Solution that worked for me:
[http://ubuntuforums.org/showthread.php?t=306308](http://ubuntuforums.org/showthread.php?t=306308)
Solutions that didn't work for me but reportedly did for others:
[http://ubuntuforums.org/showthread.php?t=305275](http://ubuntuforums.org/showthread.php?t=305275)

---

### Post by der_joachim on 2006-12-01
Does your router have DHCP? Then that is probably the culprit. Try configuring the right name servers in your router, or try getting a static IP address by using the following lines in /etc/network/interfaces:

```

auto eth0
iface eth0 inet static
     address 192.168.X.Y
     netmask 255.255.255.0

```
Do not forget to give X and Y a meaningful number. ;)

---

