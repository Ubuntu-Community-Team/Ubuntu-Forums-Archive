---
title: "Need to activate/deactivate eth0 every session?!"
date: 2006-07-01
forum: General Help
---

### Post by ezphilosophy on 2006-07-01
Everytime I log in, I cannot connect to the internet until I go into "networking" and deactivate and then reactivate eth0.  Then, the internet works no problem.  I'm not sure how to fix it.

I'm using a router that connects to a modem using pppoe (name and password).

My /etc/network/interfaces looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```  

Any ideas?

---

### Post by scxtt on 2006-07-01
try commenting out everything but:
[indent]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp[/indent]

---

### Post by static chaser on 2006-07-01
i have a similar problem to yours. both my email and web browser quit working after a period of time. I cant find any one thing that i do to cause it to quit. i have to power off my modem then power it back on, wait until it locks on and then try it. im using firefox/thunderbird. my modem is a us robotics 9003 adsl connecte directly to pppoe like yours. it is the modem given to me by my dsl provider. my etc/network/interfaces looks like the one recommended by scxtt. anybody got any ideas?

---

### Post by scxtt on 2006-07-01
do you have to use DHCP? -- maybe setting static IPs would help ...

---

### Post by ezphilosophy on 2006-07-02
Yes, I do use DHCP.
I really feel like I should know the answer to this, but what is the method used to give myself a static IP?  I mean, I know "where", but how do I determine what it should be?  What are the advantages/disadvantages of having a static IP?

---

### Post by scxtt on 2006-07-02
it all depends on what address your router uses ... for instance, the IP for my router is 192.168.1.1 - so when i assign static IPs to boxes on my LAN i start w/ 192.168.1.100 - tho i could probably use 192.168.1.2 and so on (not sure :p) ...

the main advantage of using static is that you'll always know what your IP will be, whereas w/ multiple boxes on a LAN, if one is rebooted it gives up it's IP and can be assigned something else @ a later time depending on what's available - which can get annoying for apps that refer to specific IPs ...

---

### Post by ezphilosophy on 2006-07-02
[QUOTE=scxtt]try commenting out everything but:
[indent]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp[/indent][/QUOTE]

I did so and no change.

Argh....

---

### Post by ezphilosophy on 2006-07-03
Interesting.....  I just logged in and the internet worked right away.  Hmm....  I don't know if that is a good thing or a bad thing.  It seems that an inconsistent problem is worse.

EDIT: nope, not working again.  Would really appreciate any help.  Someone must know!

---

### Post by ezphilosophy on 2006-08-06
Well, I just want to give this thread a *bump*. I still haven't found a fix and the problem is really irritating. Why should I have to go into network settings each time I turn on my computer, then disable then enable the eth0 just to get on the internet?!

Why was there no problem in Breezy but now there is in Dapper? What could the big change be?

What more, is that out of all the threads with this problem (there are [many]("http://ubuntuforums.org/showthread.php?p=1344330")), no one has a solution other than giving yourself a static IP.

Please, Ubuntu Gurus, help us solve this problem!
Edit/Delete Message

---

### Post by Sisyphe on 2006-08-06
I have the same problem here with a US Robotics 9105 when I use DHCP (not with fixed IPs).  I've had it with Ubuntu Dapper and Breezy but also with Debian Sarge.

I never found a proper solution so I made a script to restart the eth0 interface automatically at the end of the boot.

So I created (with sudo) the file 
/etc/init.d/redemande_adresse_dhcp.sh

containing
```

#! /bin/bash
# Petit script pour redemander une adresse DHCP 
sudo ifdown eth0
sudo ifup eth0

```

and made it start at the end of every boot by typing once in a terminal

```
sudo update-rc.d redemande_adresse_dhcp.sh start 99 2 
```

---

### Post by jotagab on 2006-08-08
Do you have a proper IP address after boot? You can check this by executing 'ifconfig eth0' and looking for the 'inet addr:' part.
If you don't have one assigned try running the DHCP client on a terminal (the command is 'dhclient') and look for errors.
Of course it can also be a problem with the router...

---

### Post by Paulr-55 on 2006-08-08
There is a bug report concerning this issue (me got it too) [here]("https://launchpad.net/distros/ubuntu/+bug/42608").

---

### Post by jotagab on 2006-08-08
Ok, you might try to add 'gateway 192.168.1.1' to /etc/network/interfaces, after the eth0 line, as the bug report says.

I also remembered that in some routers the DHCP server doesn't work very well if you have ipv6 enabled. Try adding the following line to /etc/modprobe.d/blacklist:
blacklist ipv6

After rebooting the command 'lsmod | grep ipv6' should give an empty result.

Good luck!

---

### Post by ezphilosophy on 2006-08-09
Ok, well, I added the gateway address to my interfaces file.  I restarted and  the internet worked.  I thought I fixed the problem. When I restarted again later, the internet didn't work.  Now, I'm trying for the 3rd time, and it worked.  

This problem keeps getting stronger.  Why would that entry affect *how often* it works?

---

