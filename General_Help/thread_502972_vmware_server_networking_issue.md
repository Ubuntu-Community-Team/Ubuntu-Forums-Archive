---
title: "vmware server networking issue"
date: 2007-07-17
forum: General Help
---

### Post by pmgeahan on 2007-07-17
Folks -

Having a minor issue here with VMWare Server.  My Ubuntu Feisty machine runs VMware Server 1.0.2 build-39867.  My Feisty system is running 2.6.20-16-generic.  

I have two virtual machines, one running another install of Ubuntu and another running Windows XP.  I want to be able to move data back and forth between the virtual machines and the physical machine.  Here's the problem: I cannot create any persistent connections between the VMs and the server.  Samba doesn't work, SSH doesn't work, NFS doesn't work.  All connections timeout or fall over.

The physical machine is reachable from other points on the network, and the virtual machines are not reachable from other machines on the physical network.  Both VMWare machines can route out to the Internet just fine.

I'm having trouble figuring out where the problem could be.  I suspect it's got to be in a VMWare configuration somewhere, as everything else seems to work as anticipated.  

Anyone have any ideas?

---

### Post by useResa on 2007-07-17
I also use VMware Server in Feisty and I have got samba working.
It did however take some effort to get it running the way I wanted.

AFAIK you have to make sure you are registered as user (because of [this bug]("https://launchpad.net/ubuntu/+source/samba/+bug/32067"))
You can do so by issuing the command
```
sudo smbpasswd -L -a your_username
```

Additionally you may need to edit your /ect/samba/smb.conf file, but try the above suggestion first.

---

### Post by pmgeahan on 2007-07-17
Thanks for the reply; but I already have that in place.  Samba on the physical machine works for the rest of the network.  In this case, I can't get a connection either way(physical->virtual or virtual->physical) even long enough to get a password prompt.

---

### Post by useResa on 2007-07-17
I also have modified my /etc/samba/smb.conf file. You can do this by using a terminal and issue the command ```
gksudo gedit /etc/samba/smb.conf
```

Please find below a sample of how a shared directory on my machine is defined
> [[COLOR=Blue]directory_name[/COLOR]]
path = [COLOR=Blue]/full/path/to/directory_name[/COLOR]
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = [COLOR=Blue]my_user_name[/COLOR]
force group = [COLOR=Blue]my_user_name[/COLOR]
available = yes
public = yes
writable = yes
comment = [COLOR=Blue]my_comment[/COLOR]
browsable = yes
I think it goes without saying that the [COLOR=Blue]blue text[/COLOR] has to be altered to match your situation  ;)

---

### Post by veloce on 2007-07-18
Is it samba causing the issue, or the underlying networking?

I had difficulty with vmware's networking, in particular the dhcp server on the host only network seems to work erratically and connections to the host across the bridged network would time out (they did actually work but were incredibly slow).

What I did was set up all vms with only host only networking, then added a tiny firewall (IPCop) to manage access to the rest of the network and act as a dhcp server. The only trick was turning off vmware's dhcp server.

---

### Post by scxtt on 2007-07-18
what type of networking did you set up for the VMs?  i use "host only" for each one and then i can assign them IPs as if they were plugged right into my router ... pings work, smb works, nfs works, internet works ... might be possible w/ the other connection types, but i have no need for virtual adapters that add another layer of "complexity" to my network - a quasi-random 172.x.x.x virtual network ... i'm sure there's cool uses for it, but not for me :)

---

### Post by pmgeahan on 2007-07-18
Veloce and scxtt - 

Thanks for your responses.

To answer both questions, samba is not the problem(at least not all of it) as SSH does not work either.  In my experience, SSH is pretty darn simple as protocols go.  My guess is that the networking is an issue.  

It feels like a firewall is in place, silently dropping traffic.  I've verified that neither the Ubuntu physical machine nor the XP virtual machine have a firewall in place.  

As for networking options, I have tried bridged networking, NAT, private shared with host, and use of specific virtual networks.  All respond the same; connection-oriented protocols can't get from virtual to physical.

---

### Post by useResa on 2007-07-18
I always use a specific virtual network (vmnet8 in my case) since every other way causes issues. Some of them similar to what you describe.

---

### Post by scxtt on 2007-07-19
what's the output of **ifconfig** on your ubuntu host and ubuntu vm? do you have a static (physical) network or do you use DHCP?

---

### Post by pmgeahan on 2007-07-19
> **scxtt said:**
> what's the output of **ifconfig** on your ubuntu host and ubuntu vm? do you have a static (physical) network or do you use DHCP?

This machine physically connects to three networks.  They sit on eth0/1/2.  Two of the three use DHCP, the third is statically assigned.  


ifconfig(physical):

```

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:58:CF:D3  
          inet addr:192.168.8.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe58:cfd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5336334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3625114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:193474 txqueuelen:100 
          RX bytes:3292553226 (3.0 GiB)  TX bytes:911366726 (869.1 MiB)
          Base address:0xdcc0 Memory:ff6e0000-ff700000 

eth1      Link encap:Ethernet  HWaddr 00:30:BD:04:E4:D2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2198227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:156846263 (149.5 MiB)  TX bytes:13019458 (12.4 MiB)
          Interrupt:22 Base address:0x400 

eth2      Link encap:Ethernet  HWaddr 00:30:BD:06:01:BA  
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe06:1ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3887622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:613369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:592914059 (565.4 MiB)  TX bytes:126143644 (120.2 MiB)
          Interrupt:23 Base address:0xa000 

eth1:avah Link encap:Ethernet  HWaddr 00:30:BD:04:E4:D2  
          inet addr:169.254.9.97  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1362160 (1.2 MiB)  TX bytes:1362160 (1.2 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.237.1  Bcast:172.16.237.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



```

And on the Ubuntu vm:

```

eth0      Link encap:Ethernet  HWaddr 00:0C:29:25:1A:5F
          inet addr:192.168.1.40  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe25:1a5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3304090 (3.1 MiB)  TX bytes:26723 (26.0 KiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10072 (9.8 KiB)  TX bytes:10072 (9.8 KiB)


```

The Ubuntu VM is currently set to use /dev/vmnet2, which corresponds to the host eth2.

---

### Post by scxtt on 2007-07-19
i don't see a /dev/vmnet2 on your physical host ... just vmnet1 (192.168.10.1) and vmnet8 (172.16.237.1).

---

### Post by pmgeahan on 2007-07-19
> **scxtt said:**
> i don't see a /dev/vmnet2 on your physical host ... just vmnet1 (192.168.10.1) and vmnet8 (172.16.237.1).

vmnet2 is bridged directly to eth2.  It appears that the interfaces that request via DHCP(vmnet0 and vmnet2) don't show up.  Perhaps I wasn't using them at the time.

---

### Post by scxtt on 2007-07-20
what's your routing table look like on the physical box?

i only started having "problems" w. my vmware network after i added gigabit cards to my 2 boxes - so i had eth0 and eth1 ... as soon as i made sure i had just 1 default gateway device and that the VMs were bridged to it, my issues went away ...
```
:> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.20.1.0       *               255.255.255.0   U     0      0        0 eth0
10.20.1.0       *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.20.1.1       0.0.0.0         UG    0      0        0 eth0
```

---

