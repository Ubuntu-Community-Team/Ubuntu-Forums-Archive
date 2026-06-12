---
title: "network manager issue.. /etc/network/interfaces.."
date: 2006-11-11
forum: General Help
---

### Post by a.d.gardiner on 2006-11-11
hey guys.

been looking about, and in the wiki.. but im stuck.

Im kinda new, and struggling to get network manager to remember that eth0 is my default network connection. I only have one NIC.

So far I select the card, activate it and then apply the changes. Then I reboot and still fail to connect to my network or the internet. Back in Network manager it no longer remembers that i applied eth0 as my default gateway.

Its kind of infuriating because sometimes it works.

I have tried looking at interfaces... 'sudo gedit interfaces' in /etc/network/.. but im not entierly sure what to modify to set eth0 as my default network card/connection/gateway.

There are a lot of posts on the forum about this.. but Im stuggling to understand even after a lot of experiementation.

cheers,

:)

---

### Post by a.d.gardiner on 2006-11-11
okay.. just been researching a little bit more..

It appears that to get everything up and working you have to

1) disable all network adaptors in network manager.

2)remove all but "auto lo" and "iface lo inet loopback" from the interfaces file in /etc/network/.

3)add "nm-applet --sm-disable" in sessions, startup.

4)reboot

This apparantly will prevoke network manager into managing the network automatically.

Thing is that ain't working either.

And I just want my wired internet to work lol. ](*,)

anybody?

---

### Post by lloyd_b on 2006-11-11
It depends on whether you're using static IP's or DHCP.

Could you post your "/etc/network/interfaces" file?  This would give us a good starting point....

If you're using static IP's: Here's a copy of my "/etc/network/interfaces".  Just tweak the IP addresses as required:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.25
        netmask 255.255.255.0
        gateway 192.168.0.1 

```

Lloyd B.

---

### Post by a.d.gardiner on 2006-11-11
Im using DHCP.

..well at least I believe so. My understanding is that my router supplies each machine an IP.. it is the DHCP server.. that sounds about right? :-|

Just running a reinstall of dapper and i'll post the relevant information you mentioned in a few.

;)

---

### Post by a.d.gardiner on 2006-11-11
Okay i just went through with a fresh install of dapper.. changed nothing.. disabled nothing in networking. The only thing i changed was my interfaces file to now read:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 dhcp

```

but still nothing. I definately know the card works and has worked in ubuntu like earlier today :neutral:

---

### Post by lloyd_b on 2006-11-11
First:

```
iface eth0 dhcp
```

should be (I think)

```
iface eth0 inet dhcp
```

Make that change, reboot, and if you still have problems, please post the following:

The output of the "route" command.
The output of the "ifconfig" command.
The contents of the file "/etc/dhcp3/dhclient.conf"

The route command will show what routes (if any) your system is creating.
The ifconfig command will show exactly how your interfaces are being configured, including the info from DHCP.
The "dhclient.conf" file is the main configuration file for DHCP clients (duh).

Lloyd B.

---

### Post by a.d.gardiner on 2006-11-12
All working now.. i just had the interfaces code slightly wrong! duh!

Thanks for your help ;)

---

### Post by ivanyshka7 on 2006-11-18
so what is your interface look like.

I have the same problems

---

