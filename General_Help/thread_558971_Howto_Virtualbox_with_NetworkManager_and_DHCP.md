---
title: "Howto: Virtualbox with NetworkManager and DHCP"
date: 2007-09-24
forum: General Help
---

### Post by jsully1 on 2007-09-24
Hi all,

I read through [ipguru99's excellent FAQ](http://ubuntuforums.org/showthread.php?t=346185) about setting up VirtualBox Host Networking and decided to add my own solution that builds on his, and decided to start my own thread because my solution would just get buried on page 8 of a thread that's surely going to get bigger.  So here it is!

First - what will this guide do?  Well, it's going to setup your networking such that as soon as your computer boots you'll be ready to start Windows in a VM and have it immediately work with DHCP.  It will also give your Windows VM a unique IP address on the network, so you'll be able to access the Windows machine from external computers by its IP or even by its name.

First step - you'll want to edit rc.local (sudo nano /etc/rc.local) - by default there shouldn't be much of anything in there.  Here is mine after editing:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/sbin/tunctl -t tap0 -u **username**
/bin/chmod 666 /dev/net/tun
/sbin/ifconfig eth0:0 192.168.0.1 netmask 255.255.255.0
/usr/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/usr/sbin/brctl addif br0 eth0:0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
/sbin/ifconfig tap0 192.168.0.2 up
/bin/bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
/sbin/route add -host 192.168.0.1 dev tap0
/usr/sbin/arp -Ds 192.168.0.1 eth0:0 pub
exit 0
```

My office gives out 10.248.xxx.xxx IP addresses, so I went with 192.168.0.xxx IP addresses for my virtual network between my computer and the virtual machine on it - there is flexibility here, for example ipguru99 used 192.168.0.45 for his computer and 192.168.0.94 for his.  (again definitely check out his excellent thread here [http://ubuntuforums.org/showthread.php?t=346185](http://ubuntuforums.org/showthread.php?t=346185)

Also make sure you replace username with your actual username!

After you've done this you'll want to reboot or run /etc/rc.local.  

To verify that things are setup properly you'll now want to do an ifconfig - your output should look something like this:
```
sully:$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:16:41:99:99:99  
          inet addr:10.248.101.241  Bcast:10.248.101.255  Mask:255.255.254.0
          inet6 addr: fe80::216:41ff:fe56:7835/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1788828 (1.7 MiB)  TX bytes:614007 (599.6 KiB)

eth0      Link encap:Ethernet  HWaddr 00:16:41:99:99:99  
          inet6 addr: fe80::216:41ff:fe56:7835/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1940345 (1.8 MiB)  TX bytes:480313 (469.0 KiB)
          Base address:0x3000 Memory:ee000000-ee020000 

eth0:0    Link encap:Ethernet  HWaddr 00:16:41:99:99:99  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          Base address:0x3000 Memory:ee000000-ee020000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:99:99:99 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:457 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xc000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6431 (6.2 KiB)  TX bytes:6431 (6.2 KiB)

tap0      Link encap:Ethernet  HWaddr 46:F8:94:14:84:C7  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::44f8:94ff:fe14:84c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1381 errors:0 dropped:302 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:104339 (101.8 KiB)  TX bytes:408202 (398.6 KiB)
```

Also useful to check will be your routing table.  Run the command "route" from a terminal - here is my output:
```
sully$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
sullyslaptop.lo *               255.255.255.255 UH    0      0        0 tap0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 tap0
10.248.100.0    *               255.255.254.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.248.100.1    0.0.0.0         UG    0      0        0 br0
default         10.248.100.1    0.0.0.0         UG    0      0        0 eth0
```
Once you've completed this step, the next step is to configure VirtualBox.  In the Virtualbox window go to Settings > Network and select "Host Interface" for the "attached to option", and set Interface Name to tap0.  Now fire up the Windows virtual machine and you should be all set!

A word of caution, after a reboot when trying to start the Windows VM you may get this error:
```
Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).
```

The fix is simple - you need to manually run "sudo chmod 666 /dev/net/tun" manually - it doesn't seem to work automatically from the rc.local file.  If anyone has a solution to this please let me know!

This setup should also work for wireless by replacing all eth0 references with eth1 (if that's the name of your wireless interface) though I have not yet attempted this.

As I'm still relatively new to linux (~2 years) this is the best I can come up with - please let me know if anyone has anything to add!  I'm confident there is a better way of doing this - perhaps with a script that's called whenever network manager gets a new IP or connects to a new network?  I'm also hoping for a solution to the chmod 666 /dev/net/tun issue.

Best of luck - let me know how it works out!

---

### Post by mondalaci on 2007-11-02
Thank you for the kickass description!  Works like a charm.  Hell, it was too easy this way!  ;)

---

### Post by okdok on 2007-11-09
Can anyone who has used the how-to above post what they put in /etc/network/interfaces?

---

### Post by hamsandwich on 2008-04-14
I realize I am stumbling across this long after you've written it but it doesn't reduce the usefulness one bit. After reading thru posts on Vbox networking 'till my eyes bled, this is the first one that made it clear to me that the IP of your eth0 and tap0 are completely unrelated to the LAN IP that you bridge will use, and the IP that your virtual machine will end up with. You are basically creating a private tunnel between the host and the guest OS via the private "eth0 to tap0" route.

Thanks for ending my misery! This absolutely does work, and it works for DHCP which I could not get to function as most of the tutorials were based on fixed IP's. My guest boots up, and gets an address via DHCP and I have full connectivity to it from anything on the LAN. I'm using a simple script to do this.

Thanks thanks thanks! This post should be a sticky somewhere.

---

### Post by coloured on 2008-04-28
Just a question maybe someone could help me with;
I have multiple network cards in my laptop, one wired and one wireless.
for some reason in virtual box my wireless shows as intel pro/1000 MT desktop (its actually a intel pro/wireless 3945ABG)
anyway, I installed the intel pro/1000 MT desktop drivers on the XP guest.
Am I able to create another bridge interface within the host? one for the eth0 (wired) and one for eth1 (wireless)

cheers
Jurgen

---

### Post by hamsandwich on 2008-04-29
I'm not an expert but the reason the intel pro/1000 shows up on your virtual machine is that the virtual machine maps its own adapter on top of your laptop's adapter. Your VM will not see your actual adapter, that's why it's not seeing your pro wireless card. You get a choice of three different "cards" that the VM will see instead, the intel pro/1000 is one of those.

So when you open the virtual machine settings and select "network", you will see your first default virtual adapter. Under "adapter type" you select which of the three adapters your VM "thinks" it has.

I haven't done it but to allow your VM to use more than one card, just enable add'l adapters on the network screen (see the tabs across the top that say adapter 0, adapter 1, etc?).

---

### Post by mc-rpg on 2008-05-08
Your post doesn't work for me. I'm on ubuntu 8.04. I don't know why but ifconfig just give me the same interfaces that I already had before editing the rc.local file.. on top of changing the username, should I change the IPs according to the ones in my interfaces or something like that?

---

### Post by mc-rpg on 2008-05-08
Ok, now everything is showed with the route command :)
You should've said that we need to install bridge-utils in order for it to work.

UPDATE: Until now it seems that everything is working and I don't need to do the 'sudo chmod 666 /dev/net/tun' thing. Using so many tutorials to do this must have had that effect :D

---

### Post by mc-rpg on 2008-05-09
Ok, I think that now I know how I solved the:
> Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

In my /etc/udev/rules.d directory, I added a file named 95-tun.rules (the 95 is important so you know it is one of the last the system loads), for automatically setting the tun module permissions when it gets modprobe‘d, the file must contain this line:
> KERNEL=="tun", MODE="0666"

I think that was what solved my problem, I got it from this tutorial: [http://mychael.gotdns.com/blog/2007/05/31/virtualbox-bridging/](http://mychael.gotdns.com/blog/2007/05/31/virtualbox-bridging/) remember to restart your machine after the addition of that rule.

---

