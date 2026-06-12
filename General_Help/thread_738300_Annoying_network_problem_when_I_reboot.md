---
title: "Annoying network problem when I reboot"
date: 2008-03-28
forum: General Help
---

### Post by jakupl on 2008-03-28
Hi :) I have ubuntu studio on a computer, everytime I turn it on, i have to set the network

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/net1.png[/IMG]

I have to click "wired connection" and click "Properties"

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/net2.png[/IMG]

then click "enable this connection" and set "Automatic configuration (DHCP)" and click ok.

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/net3.png[/IMG]

and mark "wired connection" again, and press "close"

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/net4.png[/IMG]


I have to do this everytime I reboot. Is there anyway of doing this in a script??... It's getting quite annoying:KS

---

### Post by Iowan on 2008-03-28
Check the **/etc/network/interfaces** file to verify that it contains an **auto eth0** line.

---

### Post by jakupl on 2008-03-28
no there is no auto eth0.



```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

iface eth2 inet dhcp

auto eth2

iface eth3 inet dhcp

auto eth3

iface eth4 inet dhcp

auto eth4


iface eth5 inet dhcp

auto eth5

iface eth6 inet dhcp

auto eth6

iface eth7 inet dhcp

auto eth7

iface eth8 inet dhcp

auto eth8

iface eth9 inet dhcp

auto eth9

iface eth10 inet dhcp

auto eth10

iface eth11 inet dhcp



iface eth12 inet dhcp

auto eth12
```

what should I do then? should I just add one? how would i do that? :popcorn:

thanks dude :KS

---

### Post by jakupl on 2008-03-28
bump :popcorn::guitar::KS:lolflag:

---

### Post by danwood76 on 2008-03-28
```

sudo gedit /etc/network/interfaces

```

and add

```

auto eth0
iface eth0 inet dhcp

```
before the eth1 section save and reboot.

---

### Post by drachenstern on 2008-03-28
I'm a little sorry to just inject this, as all the useful information has been given in this thread to ensure that the required functionality will be achieved, however:

why do you have so many network adapters?  I don't have whole lines of network adapters in my /etc... file, and I've been messing with linux since Redhat 4.  I also haven't made any manual changes to my /etc... file, so I'm really curious how yours has so many entries but no auto eth0

---

### Post by jakupl on 2008-03-28
[QUOTE="drachenstern"]why do you have so many network adapters? I don't have whole lines of network adapters in my /etc... file, and I've been messing with linux since Redhat 4. I also haven't made any manual changes to my /etc... file, so I'm really curious how yours has so many entries but no auto eth0[/QUOTE]

also, on my other computer with Ubuntu, "witch" I have been using alot longer, my etc/network/interfaces only says:

```
auto lo
iface lo inet loopback
```

... WTF?? hehehe.


but well.. back to this computer. it didn't work, but remember. This computer has ubuntu studios... that could maybe.... no... I don't think that has anything to do with it.
ANYWAYS I changed the "interfaces" file to:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth1

iface eth2 inet dhcp

auto eth2

iface eth3 inet dhcp

auto eth3

iface eth4 inet dhcp

auto eth4


iface eth5 inet dhcp

auto eth5

iface eth6 inet dhcp

auto eth6

iface eth7 inet dhcp

auto eth7

iface eth8 inet dhcp

auto eth8

iface eth9 inet dhcp

auto eth9

iface eth10 inet dhcp

auto eth10

iface eth11 inet dhcp



iface eth12 inet dhcp

auto eth12

iface eth14 inet dhcp

auto eth14

iface eth17 inet dhcp

auto eth17
```

but no succes... still exactly the same problem. I still need to do what I wrote on my first post.:confused:

---

### Post by danwood76 on 2008-03-28
well back it up and delete it all except the loopback.
restart and see, it might be getting confused.

---

### Post by jakupl on 2008-03-28
I tried it... didn't work  :x

I don't think this file has anything to do with it... must lie deeper then that... maybe??? hehe well I don't know

---

### Post by jimv on 2008-03-28
System > Network > Click Wired Connection > Click Properties > Make sure "Roaming Mode" is checked

---

### Post by jakupl on 2008-03-28
can't do this. see my picture nr.3 on 1st. post.

This is ubuntu studio,.. don't really see the difference but oh well ;)

---

### Post by jakupl on 2008-04-01
bump ? :KS

---

### Post by drachenstern on 2008-05-28
Bump - did you ever get this resolved?  If not, reply back because it doesn't look like you actually figured out what you needed to.  If another person is having the same or a similar problem, re-bump this thread...

Thanks - Drach

---

### Post by jakupl on 2008-05-28
Yes I got it resolved at the irc forum. I dont have the time to post the answer right now, but I will do it within a week... maybe less. :)
Thanks for reminding me.

(This is really _not_ a common problem. jdong helped me but he had never seen it before.)

---

### Post by drachenstern on 2008-05-28
Thanks for letting everyone know you got it fixed.  I really didn't mind helping, but I've been so swamped between uni and work and life, that it's been months since I've been on the forums to actually try and participate.  Today I was looking at back logs where I had posted previously, and saw yours, and was curious if you had had a chance...

I think I know what the problem was, but I'll just let you post your redux on the solution.  Congrats that it's working btw.

---

