---
title: "cant connect to the internet"
date: 2007-01-06
forum: General Help
---

### Post by STREETURCHINE on 2007-01-06
hi i am having trouble with getting the internet back it seems i dont have permission

ex@rex-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: Permission denied
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: Permission denied
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: Permission denied
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: Permission denied
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
rex@rex-desktop:~$ ping google .com
ping: unknown host google
rex@rex-desktop:~$ dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
rex@rex-desktop:~$

---

### Post by quartzy on 2007-01-06
Most of that is junk you don't need.

I would assume its a ethernet port your trying to setup? And you only have one of them?

If so edit your /etc/network/interfaces and remove the 'auto' for all of them but the eth0 one.

Then could you post what you get when you run sudo /etc/init.d/networking restart?

And prehaps post your /etc/net/interfaces file.

---

### Post by STREETURCHINE on 2007-01-06
hi sorry i took so long ,
i have to boot between hard drives to do the thins you told me to do then back so i can post

rex@rex-desktop:~$ gksudo gedit /etc/network/interfaces
(gedit:5399): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rex@rex-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]
rex@rex-desktop:~$

the  /etc/net/interfaces file. was empty

---

### Post by quartzy on 2007-01-06
I meant network rather than net sorry, I have no idea what you did when you tried to open interfaces but it seems abit screwed, sorry bout that ](*,) 

This is my /etc/network/interfaces 

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

```

You could try and see if that works.

Maybe before that you are trying to use the ethernet port connecting to a modem / router of some kind arn't you?

---

### Post by STREETURCHINE on 2007-01-06
yes i go through a dlink router  to a sky edge modem

thanks i will see how i go

---

### Post by STREETURCHINE on 2007-01-06
still no joy 

rex@rex-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0b:6a:e3:51:74
Sending on   LPF/eth0/00:0b:6a:e3:51:74
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth0/00:0b:6a:e3:51:74
Sending on   LPF/eth0/00:0b:6a:e3:51:74
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down


hope some one can work this out

---

### Post by quartzy on 2007-01-06
Maybe the same problem these people were having? (Kinda old though)

[http://ubuntuforums.org/showthread.php?t=149590](http://ubuntuforums.org/showthread.php?t=149590)

---

### Post by quartzy on 2007-01-06
I'm off for now, but I would suggest you try manually setting the ip address etc (as described in that other thread) and seeing if that works. 

Note dns may stuff up so if you are seeing if you on the internet ping ip addr's, only one I know off the top of my head is 60.234.1.1

Good Luck and sorry I couldn't figure it out :(

---

### Post by STREETURCHINE on 2007-01-06
no worries thanks for all your help,that didnot work for me, but maybe some one will have a solution

---

### Post by quartzy on 2007-01-06
Could you provide more information?

Ethernet card type (mobo type if it's integrated).

Was it working before?  
When did it stop working?  
What did you change for it to stop working?

---

### Post by STREETURCHINE on 2007-01-06
router 704up dlink

eth0 card i dont know,but it is still working beause i can use it on this harddrive

it stopped working after i mounted hda1 to hdb1 on media/shared so i could see the outher hard drive.

as soon as they were mounted and i could see both from one anouther i lost permissions on hda1
so i had to unmount it and go from there .

so i serched through the forums got some how to's and with the help of a couple of people we got my permissions back

so now i am left with no internet .it has to be in te settings,i did what the link you posted did
uninstalled dhcp3 -client and dhcp-common

but with no internet could not reinstall them(blonde moment)so i think i am shot .i have a feeling it is a complete reinstall.

thanks for all you'r help

---

### Post by quartzy on 2007-01-06
Very weird.. 

As for dhcp client you can download [dhcp3-common]("http://packages.ubuntulinux.org/hoary/net/dhcp3-common") and [dhcp3-client]("http://packages.ubuntulinux.org/hoary/net/dhcp3-client") and try to manually install them.

---

### Post by STREETURCHINE on 2007-01-06
yes this is the third time i have done this ,i dont see how mounting drives can upset my permissions.
i am in the process of moving all that i can across to hdb1 so if i cant find a soluton soon i will reinstall,
a pain in the preverbial,
 but it is all about learning ,i learn something new every time.

but i do wish it was as easy to fix as it is to break..lol

---

