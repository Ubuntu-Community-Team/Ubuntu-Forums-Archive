---
title: "Massive delay loading Gnome on BOTH my dapper machines?!?"
date: 2006-07-09
forum: General Help
---

### Post by speedsix on 2006-07-09
Very strange problem and it seems to happen on both my ubuntu machines, not sure what I have done.

Basically it boots up, logs in and sits on a blank screen with a cursor for about 4-5mins before showing the gnome splash screen and booting up fully into Gnome??

This happens regardless of which user I log in as, I even created a test user  with no joy.

Any idea what's causing this massive delay?


Many thanks

Dom

---

### Post by PBK on 2006-07-09
Are you loading any samba shares from your /etc/fstab file? That problem took my system awhile to boot. Now they are not set on auto and I load them from the /etc/rc.local file.

PK

---

### Post by speedsix on 2006-07-09
No, no samba shares. It just seems to have come from nowhere and on both my machines. Very odd. It takes ages before the actual gnome splash screen comes up after logging in.


Dom

---

### Post by Bagnaj97 on 2006-07-09
I had a similar problem, I can't remember exactly what it was, but it was something to do with /etc/hosts in my case. What is the contents of that file on your systems?

---

### Post by speedsix on 2006-07-11
I noticed when I went into the Networking section in Ubuntu I had the same 3-4 minute delay loading it up. When it does finally come up, if I disable the eth0 network and reboot it boots fine (obviously with no network)


/etc/network/interfaces
```

iface eth0 inet static
address 10.0.0.1
netmask 255.255.255.0
gateway 10.0.0.138

iface lo inet loopback

auto eth0

```

/etc/hosts
```

127.0.0.1 localhost desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


Thanks

Dom

---

### Post by Bagnaj97 on 2006-07-11
what happens if you change /etc/hosts to 
```

127.0.0.1 localhost
your.ip.address.here your_hostname_here

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by speedsix on 2006-07-11
I'll give it a go when I can get to the machine, will let you know.

Thanks.

Dom.

---

### Post by speedsix on 2006-07-11
That didn't work.


Also I cannot ping myself 10.0.0.1. Internet works fine and I can ping other machines ok.

If when the machine boots I go into System>Admin>Netowork and deactivate/reactive eth0 and click ok everything starts working again, can ping myself until I reboot??


Dom

---

### Post by Bagnaj97 on 2006-07-11
If it doesn't work with the line "10.0.0.1 desktop" (I think desktop is your hostname) then I'm out of ideas, sorry. I remember when I had the problem I couldnt ping myself either. I'm fairly sure the problem is something network related. Have you tried switching your network device between dhcp and a static address in the network configuration?

---

### Post by speedsix on 2006-07-12
Sussed it out, I didn't have the loopback enabled, the line 'auto lo' was missing from /etc/network/interfaces. No idea how mind.

Thanks for the help

Dom

---

