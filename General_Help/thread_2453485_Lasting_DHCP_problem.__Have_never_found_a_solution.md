---
title: "Lasting DHCP problem.  Have never found a solution. Help!"
date: 2020-11-11
forum: General Help
---

### Post by jimmys1 on 2020-11-11
I have a ton of stuff on my bionic 18.04 machine and rely on it a lot and for now just don't want to upgrade...   It has a very annoying problem. 

1. DHCP does not work on wired or wireless.  (My router's DHCP works with EVERY other computer and even this computer with a boot USB chip)
2. The networking works fine with static addresses on BOTH wired and wireless.
3. DHCP at one time worked on this 18.04.   I am not exactly sure what I did that messed it up.  It MAY have been many months ago when I attempted to install some intel drivers for video but not sure.
4. I have tirelessly googled solutions but nothing worked.

I can post any files/code you guys need to help. 

Thanks in advance!

---

### Post by SeijiSensei on 2020-11-11
Try running dhclient in verbose mode. You should see something like this:

```

$ sudo dhclient -v

dhclient -v
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eno1/38:2c:4a:c5:70:6c
Sending on   LPF/eno1/38:2c:4a:c5:70:6c
Sending on   Socket/fallback
DHCPDISCOVER on eno1 to 255.255.255.255 port 67 interval 3 (xid=0x9e61694c)
DHCPOFFER of 192.168.100.57 from 192.168.100.1
DHCPREQUEST for 192.168.100.57 on eno1 to 255.255.255.255 port 67 (xid=0x4c69619e)
DHCPACK of 192.168.100.57 from 192.168.100.1 (xid=0x9e61694c)

```
The client first sends a request to the broadcast address 255.255.255.255. My router at 192.168.100.1 sees the request and proposes 192.168.100.57. The client then sends a request for that address to the broadcast address, and the router confirms the assignment with DHCPACK.

---

### Post by jimmys1 on 2020-11-11
> **SeijiSensei said:**
> Try running dhclient in verbose mode. You should see something like this:

```

$ sudo dhclient -v

dhclient -v
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eno1/38:2c:4a:c5:70:6c
Sending on   LPF/eno1/38:2c:4a:c5:70:6c
Sending on   Socket/fallback
DHCPDISCOVER on eno1 to 255.255.255.255 port 67 interval 3 (xid=0x9e61694c)
DHCPOFFER of 192.168.100.57 from 192.168.100.1
DHCPREQUEST for 192.168.100.57 on eno1 to 255.255.255.255 port 67 (xid=0x4c69619e)
DHCPACK of 192.168.100.57 from 192.168.100.1 (xid=0x9e61694c)

```
The client first sends a request to the broadcast address 255.255.255.255. My router at 192.168.100.1 sees the request and proposes 192.168.100.57. The client then sends a request for that address to the broadcast address, and the router confirms the assignment with DHCPACK.


Wow, I got an interesting response.   Permissions denied with sudo? 

```

sudo dhclient -v

Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Error getting interfaces; Permission denied
Can't get list of interfaces.

If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at www.isc.org or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..

exiting.


```

---

### Post by SeijiSensei on 2020-11-11
I have no idea why you'd see that. I'd start by checking the /etc/dhcp tree and make sure root has ownership of, and write permissions to, every file and directory.

```

# cd /etc
# ls -lR dhcp
dhcp:
total 16
-rw-r--r-- 1 root root 1426 Feb 25  2020 debug
-rw-r--r-- 1 root root 1735 Feb 25  2020 dhclient.conf
drwxr-xr-x 2 root root 4096 Nov  3 06:48 dhclient-enter-hooks.d
drwxr-xr-x 2 root root 4096 Jul 23 12:01 dhclient-exit-hooks.d

dhcp/dhclient-enter-hooks.d:
total 12
-rwxr-xr-x 1 root root 1132 Dec 17  2019 avahi-autoipd
lrwxrwxrwx 1 root root    8 Apr 10  2020 debug -> ../debug
-rwxr-xr-x 1 root root 3502 Mar 24  2020 resolved
-rwxr-xr-x 1 root root 1910 Feb 26  2020 samba

dhcp/dhclient-exit-hooks.d:
total 12
lrwxrwxrwx 1 root root    8 Apr 10  2020 debug -> ../debug
-rw-r--r-- 1 root root 1756 Mar 11  2020 rfc3442-classless-routes
-rw-r--r-- 1 root root 1117 Apr 22  2020 timesyncd
-rwxr-xr-x 1 root root 1089 Dec 17  2019 zzz_avahi-autoipd

```

Also check the permissions on /var/lib/dhcp and /var/lib/dhcp/dhclient.leases.

I'm on Kubuntu 20.04, but I suspect these sorts of structures haven't changed much since 18.04.

---

### Post by jimmys1 on 2020-11-11
> **SeijiSensei said:**
> I have no idea why you'd see that. I'd start by checking the /etc/dhcp tree and make sure root has ownership of, and write permissions to, every file and directory.

```

# cd /etc
# ls -lR dhcp
dhcp:
total 16
-rw-r--r-- 1 root root 1426 Feb 25  2020 debug
-rw-r--r-- 1 root root 1735 Feb 25  2020 dhclient.conf
drwxr-xr-x 2 root root 4096 Nov  3 06:48 dhclient-enter-hooks.d
drwxr-xr-x 2 root root 4096 Jul 23 12:01 dhclient-exit-hooks.d

dhcp/dhclient-enter-hooks.d:
total 12
-rwxr-xr-x 1 root root 1132 Dec 17  2019 avahi-autoipd
lrwxrwxrwx 1 root root    8 Apr 10  2020 debug -> ../debug
-rwxr-xr-x 1 root root 3502 Mar 24  2020 resolved
-rwxr-xr-x 1 root root 1910 Feb 26  2020 samba

dhcp/dhclient-exit-hooks.d:
total 12
lrwxrwxrwx 1 root root    8 Apr 10  2020 debug -> ../debug
-rw-r--r-- 1 root root 1756 Mar 11  2020 rfc3442-classless-routes
-rw-r--r-- 1 root root 1117 Apr 22  2020 timesyncd
-rwxr-xr-x 1 root root 1089 Dec 17  2019 zzz_avahi-autoipd

```

Also check the permissions on /var/lib/dhcp and /var/lib/dhcp/dhclient.leases.

I'm on Kubuntu 20.04, but I suspect these sorts of structures haven't changed much since 18.04.

Okay, my /etc 
ls -lR dhcp looked exactly the same as the code you posted. 

My /var/lib/dhcp is empty.   Which also didn't have a dhclient.leases

EDIT: I just used catfish.  I don't have a dhclient.leases anywhere on my drive.   Dunno if it's on 18.04 or not.

---

### Post by HermanAB on 2020-11-12
Try running dhclient with the actual device name, for example:
$ sudo dhclient -v /dev/enxyzn

and look a the error messages again.

---

### Post by SeijiSensei on 2020-11-12
> **jimmys1 said:**
> My /var/lib/dhcp is empty.   Which also didn't have a dhclient.leases

EDIT: I just used catfish.  I don't have a dhclient.leases anywhere on my drive.   Dunno if it's on 18.04 or not.
That's probably because of the permission denied message.

/var/lib/dhcp should be owned by root with 755 permissions.

I'm pretty sure dhclient.leases has existed for as long as the ISC DHCP suite has been in existence.

---

### Post by jimmys1 on 2020-11-12
> **HermanAB said:**
> Try running dhclient with the actual device name, for example:
$ sudo dhclient -v /dev/enxyzn

and look a the error messages again.

sudo dhclient -v /dev/wlo1
and
sudo dhclient -v /dev/eno1
(my wifi and wired device names)

Very strange.  Same exact thing. 

```

Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Error getting interfaces; Permission denied
Can't get list of interfaces.

If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at www.isc.org or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..

exiting.

```

---

### Post by jimmys1 on 2020-11-12
> **SeijiSensei said:**
> That's probably because of the permission denied message.

/var/lib/dhcp should be owned by root with 755 permissions.

I'm pretty sure dhclient.leases has existed for as long as the ISC DHCP suite has been in existence.


Okay just to make sure.... I did this. 

```

sudo chmod 755 /var/lib/dhcp

```

For fun tried to connect with dhcp again, nothing.   Still static works fine!

---

### Post by SeijiSensei on 2020-11-12
deleted

---

### Post by SeijiSensei on 2020-11-12
Can't find any postings about not finding the interfaces list when I searched at Google.

According to the [man page for dhclient]("https://linux.die.net/man/8/dhclient"),
> The names of the network interfaces that dhclient should attempt to configure may be specified on the command line. If no interface names are specified on the command line dhclient will normally identify all network interfaces, eliminating non-broadcast interfaces if possible, and attempt to configure each interface.

It is also possible to specify interfaces by name in the [dhclient.conf]("https://linux.die.net/man/5/dhclient.conf")(5) file. If interfaces are specified in this way, then the client will only configure interfaces that are either specified in the configuration file or on the command line, and will ignore all other interfaces. 

Try this. Install the net-tools package, then run ifconfig. What interfaces does it show?
```

sudo apt install net-tools
ifconfig

```

---

### Post by HermanAB on 2020-11-12
Pardon, it should be:
$ sudo dhclient -v exyzn

You can see the device names with *ifconfig* or *ip addr show* and beware of *'o' Oh* vs *'0' zero*.

---

### Post by jimmys1 on 2020-11-12
> **SeijiSensei said:**
> Can't find any postings about not finding the interfaces list when I searched at Google.

According to the [man page for dhclient]("https://linux.die.net/man/8/dhclient"),


Try this. Install the net-tools package, then run ifconfig. What interfaces does it show?
```

sudo apt install net-tools
ifconfig

```

ifconfig 

```

eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 02:0e:ce:3c:b9:2f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 275115  bytes 138665499 (138.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 275115  bytes 138665499 (138.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vboxnet1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.57.1  netmask 255.255.255.0  broadcast 192.168.57.255
        inet6 fe80::800:27ff:fe00:1  prefixlen 64  scopeid 0x20<link>
        ether 0a:00:27:00:00:01  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4413  bytes 906392 (906.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.10  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 ee80::90b:b04a:c84d:4eff  prefixlen 64  scopeid 0x20<link>
        ether b2:18:b3:c1:69:35  txqueuelen 1000  (Ethernet)
        RX packets 2580184  bytes 2144831025 (2.1 GB)
        RX errors 0  dropped 14  overruns 0  frame 0
        TX packets 2120282  bytes 1192001187 (1.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by jimmys1 on 2020-11-12
> **HermanAB said:**
> Pardon, it should be:
$ sudo dhclient -v exyzn

You can see the device names with *ifconfig* or *ip addr show* and beware of *'o' Oh* vs *'0' zero*.

Yeah I'm fairly baffled on what's up with this. LOL

```

$ sudo dhclient -v wlo1


Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Error getting interfaces; Permission denied
Can't get list of interfaces.

If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at www.isc.org or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..

exiting.

```

---

### Post by HermanAB on 2020-11-13
My guess is that your ethernet device name is spelled wrong.  Don’t type it.  Copy and paste it from the ip or ifconfig results.

---

### Post by jimmys1 on 2020-11-13
> **HermanAB said:**
> My guess is that your ethernet device name is spelled wrong.  Don’t type it.  Copy and paste it from the ip or ifconfig results.

Okay what I did was an ifconfig and I copied wlo1 from the list of devices.

Then I typed in:

sudo dhclient -v 

and pasted

wlo1

So in total it looked like

sudo dhclient -v wlo1

It still have me the permission error. 

It's crazy!

---

### Post by TheFu on 2020-11-13
Are you using any ACLs or is the DHCP stuff using a snap package?
Ubuntu people tend not to use ACLs, but some how-to guides use them.  **getfacl** is the command to see ACLs, but it isn't very user friendly. You'll need to check all the related files and directories, recursively. It will be a pain.  And in the end, it might not actually have anything at all to do with the problem.

Failing HDDs sometimes get confused permissions. Those usually show up with ```
?????????   root  root
```  in the **ls -l** listings.

I'm just throwing out some other ideas. No clue, as I don't use DHCP except for portable devices.

---

### Post by jimmys1 on 2020-11-13
This problem has been so odd it's almost a mission to me to find out what it is!  :)   I can't imagine why it would ask me for permission when I use sudo.

sudo dhclient -v wlo1 

I mean isn't that always "super user" (root) the buck stops there?

---

### Post by TheFu on 2020-11-13
> **jimmys1 said:**
> I mean isn't that always "super user" (root) the buck stops there?

Uh, no. There are ways to prevent root access to stuff. There are systems that implement 'role-based' access where root isn't godly. Those are seldom seen on Ubuntu systems, but you never know.

I once lost 3 days dealing with funky ACLs.

---

### Post by HermanAB on 2020-11-13
This really is turning into quite a mental exercise.  TheFu is correct about ACLs and there is also Mandatory Access Control such as Tomoyo, SELinux and AppArmor which are like ACLs on steroids. AppArmor is the Ubuntu favourite and it may be preventing dhclient from accessing the devices.

Other things that can trip you up are chroot and various types of containers.

Maybe you should re-install dhclient and you can also try a different one, such as dhcpcd.

---

