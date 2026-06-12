---
title: "Hangs while booting (fsck)"
date: 2007-04-12
forum: General Help
---

### Post by psi36 on 2007-04-12
Lately, when I boot Ubuntu 6.10, the first time it hangs in about 50% of the tries.
Or the progress bar stops moving and nothing happens any more. Or I get the text screen where the last line is "fsck 1.39 (29-May-2006)". I do get an "[OK]" at the end of this line, but nothing else happens.
When I use the power button to shut down and try again, Ubuntu does boot.

I've been using Ubuntu for quite some time now, but still consider myself a noob, since I have absolutely no idea how to fix this...

---

### Post by kwaanens on 2007-04-12
I had a problem like this, but the computer did boot, it just hung for 1-2 minutes at the point you're describing. It turned out it was networking, and I had to comment out my lines in /etc/networking/interfaces

- Ketil

---

### Post by ububaba on 2007-04-12
> **kwaanens said:**
> I had a problem like this, but the computer did boot, it just hung for 1-2 minutes at the point you're describing. It turned out it was networking, and I had to comment out my lines in /etc/networking/interfaces

- Ketil

I am not sure what is the cause of problems, I am facing in booting but would you kindly
be more specific when you say about commenting out** some lines.** What are these lines
supposed to say?

---

### Post by Catsworth on 2007-04-12
I have exactly the same problem, except I get it every time I boot.

It appears to be a networking problem (I believe that my NIC is trying unsuccessfully to get an IP address through DHCP).  I haven't gotten around to solving it yet, or trying some of the suggestions I've received on how to do so.

---

### Post by kwaanens on 2007-04-12
> **ububaba said:**
> I am not sure what is the cause of problems, I am facing in booting but would you kindly
be more specific when you say about commenting out** some lines.** What are these lines
supposed to say?

Sorry I wasn't more specific. My lines are:

```

auto lo
iface lo inet loopback

# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp
```

It might help you, but I'm not sure, as I can't see your computer from here ;-)

Either way, I think your situation is like mine, it's hanging at "configuring network interfaces", even though those exact words have not been brought up on your screen.

- Ketil

---

### Post by Catsworth on 2007-04-12
Here's the thread with some solutions in it, like I say I haven't tried them yet (too much work, so little time.....):

[http://ubuntuforums.org/showthread.php?t=385880](http://ubuntuforums.org/showthread.php?t=385880)

---

### Post by ububaba on 2007-04-12
> **kwaanens said:**
> Sorry I wasn't more specific. My lines are:

```

auto lo
iface lo inet loopback

# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp
```

It might help you, but I'm not sure, as I can't see your computer from here ;-)

Either way, I think your situation is like mine, it's hanging at "configuring network interfaces", even though those exact words have not been brought up on your screen.

- Ketil

Unfortunately your advice was of no avail for me. /interfaces file was completely empty.:confused:

---

### Post by kwaanens on 2007-04-12
I'm sorry, I think I had a typo, it should be:
/etc/network/interfaces, not networking like I wrote earlier.

No wonder yours was empty :)

- ketil

---

### Post by ububaba on 2007-04-12
> **kwaanens said:**
> I'm sorry, I think I had a typo, it should be:
/etc/network/interfaces, not networking like I wrote earlier.

No wonder yours was empty :)

- ketil

I'll try soon. But as they say it happens even in the best of families.:D

> 

auto lo
iface lo inet loopback
HERE THERE WAS MY ADDRESS/NETMASK/GATEWAY
# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp

At first hand I retained my own IP number etc and then opted out everything. Nothing
helped!:confused:

---

