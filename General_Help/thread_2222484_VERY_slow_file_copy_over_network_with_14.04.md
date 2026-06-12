---
title: "VERY slow file copy over network with 14.04"
date: 2014-05-06
forum: General Help
---

### Post by xeddog on 2014-05-06
I have a computer that does practically nothing else but run SABnzbd+/SickBeard/CouchPotato.  It has been working great for a long time now, over a year for sure.   A couple of weeks ago I upgraded the os from 13.10 to 14.04.  That also seems to be working ok except for a couple of things, and one of those things is very losw copy times.  

When SABnzbd+ completes a download and unpacks it, it then invokes the SABtoSickBeard script.  This scripts basically copies the files to their final destination and does some clean up like renameing and deleting unused/unwanted files.  Up until I upgraded Ubuntu to 14.04, a typical 1GB file would take a few minutes to copy over a 100Mbps wired network to my PopcornHour A210.  After upgrading to 14.04, it takes a few TENS of minutes to copy a 1GB file.  Just today, a 987MB file was downloaded, unpacked, and SABtoSickBeard scripts started.  As soon as the file download was completed, another file of 1.4GB started downloading.   The second download completed, and was waiting for at least 20 minutes before the first copy finished.  It then took about 30-35 minutes for it to copy.

On this occassion, network traffic at the time was pretty minimal.  A couple of browser sessions and not much else to speak of.  Certainly nothing to account for the slow copy.        

What can I look into to resolve this??

Thanks,

X

---

### Post by varunendra on 2014-05-07
We may need to use 'ethtool' to try fixing the problem, so install it beforehand -
```
sudo apt-get install ethtool
```
Then, after finishing a file transfer, please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
sudo lshw -C network
ifconfig
route -n
sudo ethtool eth0
```
..assuming "eth0" is the name of your ethernet interface. If it is different (in "ifconfig"), please change it accordingly.

---

### Post by xeddog on 2014-05-08
Thanks Varun.  I'll see about doing all of this later this evening or I might have to wait until tomorrow.

X

---

### Post by xeddog on 2014-05-13
Sorry it took so long to respond, but you know how it is.  Crap haps.  The machine in question started giving me problems in that it just occassionally locks up tighter than ****'s hatband, and that is tight.  It becomes totally unresponsive and most often won't even bring the display alive after it goes off for power saving mode.  So I had to install SABnzbd+/ SickBeard/CouchPotato on another more powrful machine.  The old machine was upgraded from Ubuntu 13.10 to Ubuntu 14.04.  This new machine was a fresh install of Ubuntu 14.04, not an upgrade.  On this new machine, the problem of slow file transfer still exists.

For this response this is what I did on the new machine.  After a fresh boot, I launched Filezilla and started transfering a file from it to my Popcornhour A210.  I was getting a throughput rate of just over 9Mbps which is a little off from the 11Mpbs I was getting in the past (according to System Monitor).  After a short time I terminated the file transfer and ran the ifconfig command.  It all looked normal EXCEPT for 20704 dropped packets which is disturbing.  I then started SAB/SB/CP and ran a manual postprocess in SB to transfer the file the way they are normally transferred.  System monitor showed a throughput somewhere around 1Mbps which is about 1/4 of what it was before.  The transfer rate was all over the place between about .6Mbps to about 1.8Mbps.  The graph looked more like the trace of a soundwave you would see on an occilliscope.  Then I ran:

    
```
twoblues@Stealth:~$ uname -mr
3.13.0-24-generic x86_64
twoblues@Stealth:~$
```

```
twoblues@Stealth:~$ sudo lshw -C network
[sudo] password for twoblues: 
  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 74:d0:2b:c9:90:2a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 ip=10.1.1.35 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:44 memory:f7d00000-f7d1ffff memory:f7d3d000-f7d3dfff ioport:f080(size=32)
twoblues@Stealth:~$
```


```
twoblues@Stealth:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 74:d0:2b:c9:90:2a  
          inet addr:10.1.1.35  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d0:2bff:fec9:902a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1269624 errors:0 dropped:20704 overruns:0 frame:0
          TX packets:2041408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:497962317 (497.9 MB)  TX bytes:2841534343 (2.8 GB)
          Interrupt:20 Memory:f7d00000-f7d20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3405129 (3.4 MB)  TX bytes:3405129 (3.4 MB)

twoblues@Stealth:~$
```

```
twoblues@Stealth:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0
10.1.1.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
twoblues@Stealth:~$
```

```
twoblues@Stealth:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off (auto)
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes
twoblues@Stealth:~$
```


The things I noticed are
1.  The number of dropped packets did not increase at all during the 1.5 hours it took to copy a 2.3GB file.
2.  The linkspeed on this machine shows 1000Gbps negotiated speed, but it should be noted that this is over the older CAT V cable.  
3.  Even though this machine says it is running at 1000Mbps, the original machine is not GigE capable and was running at only 100Mbps.

One more thing I am going to try this afternoon is to see if if I can narrow this down a little.  I have a third machine running Linux Mint 16 so I will see if Mint has the same problem with file transfers.  

Thanks,

X

---

### Post by HiImTye on 2014-05-13
are both systems you're copying to/from Linux based? if so try iperf in both directions to see actual network speeds
```
sudo apt-get install iperf
```
on one:```
iperf -s
```
on the other:```
iperf -c <ip address of other computer>
```
and then run it the other way. this will determine whether it is a network issue, or an issue with something else (such as SMB, or whatever other protocol you are using)

---

### Post by xeddog on 2014-05-13
HiImTye - The originating end were both Ubuntu 14.04, but the receiving end was a PopcornHour A-210 which is based on linux, but an older kernel.  It is a very stripped down version and is missing most of the tools necessary for dianosis.  There is no apt-get or anything like it as far as I know.

But.  I think all of this is now moot because I just ran the same test on a Mint 16 machine and it suffers from the slow transfer too.  So the problem is either the PopcornHour, or some component (switch, cable, etc.,) in between.  I don't generally believe in coincidences, but this might just be one.  The very day that I implement Ubuntu 14.04 on 2 different systems, the transfer rate goes to heck on all three machines. Nothing else was touched.  No cabling, neither of the two switches, Not the PCH, not even any power issues that I am aware of.  Just weird.


Thanks anyway,

X

---

### Post by HiImTye on 2014-05-13
what's the output of```
sudo iptables -L
```

---

### Post by varunendra on 2014-05-14
> **xeddog said:**
> 3.  Even though this machine says it is running at 1000Mbps, the original machine is not GigE capable and was running at only 100Mbps.

Is the router/switch in-between the two computers is GbE capable? If not, this is indeed weird and surprising, since Linux kernel usually doesn't make mistakes in such reportings.

To try forcing 100 Mbps - full duplex, try the following command (will be temporary, the changed mode will persist only till next boot) -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

If this doesn't seem to help, try changing the MTU value to 1492 or 1392 in Network Manager settings.

**PS:**
For my own reference, and those who may be interested in the case and wish to dig deeper, if required - There are some interesting parameters available with the driver, and hopefully sufficient hints may be found here : [http://lxr.free-electrons.com/source/drivers/net/ethernet/intel/e1000e/param.c](http://lxr.free-electrons.com/source/drivers/net/ethernet/intel/e1000e/param.c)

---

### Post by HermanAB on 2014-05-14
You could have a cable with one broken wire.

---

### Post by xeddog on 2014-05-14
HiImTye -
```
twoblues@Stealth:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
twoblues@Stealth:~$ 
```


varunendra - 
There are two Ethernet switches between the linux computers and the PopcornHour.  All three of the linux computers are connected to a switch that is indeed GigE capable.  That switch is then connected via one cat5 cable to a smaller workgroup switch that is not GigE capable.  Attached to the workgroup switch are my tv, blu-ray player, a wireless ethernet bridge, and of course the PopcornHour.

Also, I don't think changing the ethernet adapter settings is going to help because the other two machines that are 100Mbps only also have the slow transfer issue.  If I did want to change some Ethernet settings I would investigate jumbo frames first.


HermanAB - 
I certainly do need to look into cabling.   My cabling is a mess and that is kinda embarrassing since I was a network installer in a past life.  But even though it is a mess it has worked flawlessly for many years (which could be a problem in itself), and it has not been molested in any way recently so I am inclined to look for other solutions first.  I think my next step is to bring the PCH into this room and connect it to the same switch as the computers.  Then if I still have slow transfer speeds I need to look into the PCH itself.  If the speeds are good again, then I think I need to look into the old workgroup switch and possibly replace it.  If that doesn't fix it then . . . crap!  Cabling.  Btw,  I have already switched out one of the patch cords and changed the switch ports for the PCH and one of the computers on their respective switches.  No help there.

Thanks,

X

---

### Post by xeddog on 2014-05-14
Well crapiola pudding.   I have isolated the failing component to the newest piece of equipment in my entire network.  My Netgear gigabit switch.  I isolated the old computer and the PCH onto a 4-port switch I found in a closet.  A file copy using the exact same scenario (and cables I might add) as normal yielded about 5MBps transfer rates.  That's over 4 times what I was getting with the gigabit switch, and I think that is about all the PCH can handle when using nfs copy.  At least that is all I was getting before the trouble began.  


(long sigh) I guess that means a trip to Best Buy in the near future.


X

---

### Post by xeddog on 2014-05-17
OK, so I HAVEN'T isolated this.  I bought a new gigabit switch and it did nothing at all to help the problem.  Now I'm at a loss.

X

---

