---
title: "So close..."
date: 2006-09-04
forum: General Help
---

### Post by Mazza558 on 2006-09-04
Right, here's the situation. I have set up my Broadcom 4306 wireless card with Ndiswrapper. All working. In the network connections, I had set up wlan0 connection with a static IP and WEP encryption.  The interface was active with no errors. The wireless card's "LINK" light was on. I installed network-manager-gnome manually (not from apt-get) and now the wlan0 setting has disappeared. Also, there is no icon in any part of the "system" section at the top, meaning I can't access the newly installed network manager.

An interesting side note is that the network monitor loads at startup but reports that there is no network device found.

As you can see, I'm so close to finally getting wireless working, but there are a few problems to fix first. Can anyone help me with this?

Oh yeah, and Other than this, I'm really enjoying Linux, the whole concept of community-based software with no legal restrictions or enforcements of any kind is my kind of thing. On my XP machine, i've converted quite a lot of my programs to OS. Keep up the good work! If I can get this fixed by someone, I will be switching 100%! It's just that awesome!

---

### Post by orb9220 on 2006-09-04
Well for me the icon would show up put wouldn't show any access points I had to edit the and coment out everthing but Lo entry in /etc/network/interfaces

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
#wireless-essid [www.personaltelco.net](www.personaltelco.net)

#auto wlan0
#iface wlan0 inet dhcp


#iface ath0 inet dhcp
#wireless-essid [www.personaltelco.net](www.personaltelco.net)

#auto ath0

don't know if this is related.

---

### Post by peabody on 2006-09-04
This howto seems very good:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+howto](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+howto)

Shows how to setup broadcom cards and network manager.  I did this while booted into the Live CD on my iBook and got the Airport extreme working with network manager.

---

### Post by Mazza558 on 2006-09-05
> **orb9220 said:**
> Well for me the icon would show up put wouldn't show any access points I had to edit the and coment out everthing but Lo entry in /etc/network/interfaces

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
#wireless-essid [www.personaltelco.net](www.personaltelco.net)

#auto wlan0
#iface wlan0 inet dhcp


#iface ath0 inet dhcp
#wireless-essid [www.personaltelco.net](www.personaltelco.net)

#auto ath0

don't know if this is related.

Does that mean inlcuding my wlan0 settings with WEP? Because surely that wouldn't work?

---

### Post by orb9220 on 2006-09-05
Try it with and without just put a # in front. You can always go back and  put it back the way it was.

---

### Post by Mazza558 on 2006-09-05
I'm going to try what you said, but bear in mind that the problem is to do with "no network device found".

---

### Post by Mazza558 on 2006-09-05
It's OK, I finally figured out how to get it working, posting from ubuntu right now!

As a side note, are there any ATI drivers I can get to improve performance?

---

