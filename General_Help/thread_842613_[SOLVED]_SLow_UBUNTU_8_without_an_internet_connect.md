---
title: "[SOLVED] SLow UBUNTU 8 without an internet connection"
date: 2008-06-27
forum: General Help
---

### Post by hc1501 on 2008-06-27
Hey,

My PC config are

AMD 4000+ X2
ASUS M2n MX SE
160 Sata
512 DDR2 Ram


I have installed UBUNTU 8 for the past 2 weeks. initially it worked perfectly. But as soon as I configured my broadband and started using it, it became very slow whenever I'm not connected to it. If I start UBUNTU without connecting to the internet then it starts in about 10 minutes and that too with most the applications not opening like Synaptic, Administration, etc. As soon as I start the broadband it gears up its speed. I have dual boot with WIN XP. Please help me out....

---

### Post by nikgare on 2008-06-27
can you please post your /etc/hosts file.

---

### Post by hc1501 on 2008-06-29
Sorry for the late reply didnt have internet working...here is the copy of the file...



127.0.0.1 harshit-deski.aaaa
127.0.1.1 harshit-deski.aaaa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by nikgare on 2008-06-29
I think that there may be a problem with both the first 2 lines.
In my hosts file I have only the 127.0.0.1 reference, so maybe you could try commenting out tis line:

127.0.1.1 harshit-deski.aaaa

and seeing if it helps.

You may need to restart networking for it to take effect:
sudo /etc/init.d/networking restart

---

### Post by plucky on 2008-06-29
> **nikgare said:**
> I think that there may be a problem with both the first 2 lines.
In my hosts file I have only the 127.0.0.1 reference, so maybe you could try commenting out tis line:

127.0.1.1 harshit-deski.aaaa

and seeing if it helps.

You may need to restart networking for it to take effect:
sudo /etc/init.d/networking restart



No That line is for Hostname,i.e. The name your computer is seen by on the network.

The problem is **127.0.0.1 harshit-deski.aaaa** should be **127.0.0.1 Localhost** and is probably why the system is running slowly without a network.

To change the name ```
gksudo gedit /etc/hosts
``` and edit the file so the line has Localhosts instead of harshit-deski.aaaa.

Or open **System > Administration > Network** and navigate to Hosts and change it there.


Also can you post output of ```
cat /etc/hostname
```

Good Luck

---

### Post by hc1501 on 2008-06-29
harshit-deski



this is the output you asked

---

### Post by plucky on 2008-06-29
> **hc1501 said:**
> harshit-deski



this is the output you asked

Ok You also need to change the line **127.0.1.1 harshit-deski.aaaa** to **127.0.1.1 harshit-deski** by editing the .aaaa out.


Good Luck

---

### Post by hc1501 on 2008-06-30
Bingo....problem solved. UBUNTU now working gr8. Hats off to you ppl and thnks..

---

