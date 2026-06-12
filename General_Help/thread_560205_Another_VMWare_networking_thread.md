---
title: "Another VMWare networking thread"
date: 2007-09-26
forum: General Help
---

### Post by munwin on 2007-09-26
Hi Everybody,

 I am running 7.04 AMD64. I have installed VMWare Server. I have networking setup such:
```
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
   Starting VMware virtual machines...                                 done
```

My host "ifconfig -a" looks like this.

```
eth0      Link encap:Ethernet  HWaddr B2:91:D2:B2:AA:BF  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b091:d2ff:feb2:aabf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1580622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1144077 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1755703359 (1.6 GiB)  TX bytes:199150532 (189.9 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:468949 (457.9 KiB)  TX bytes:468949 (457.9 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.94.1  Bcast:192.168.94.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.251.1  Bcast:172.16.251.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

My guests "ifconfig -a" looks normal, but I can't ssh(see below), so I can't easily post it here...

I have installed Ubuntu 7.04 32 bit server as a guest. All good so far.....
I can ping from the guest to my dhcp server (my gateway).
I can ping the vmware guest from another PC on my network.
I can see Apache on the vmware guest (using Firefox) from the other PC.
My problem(s) is the host to guest networking.
From the host I can ping the guest, and visa-versa.
From the host I can run nmap against the guest, and see apache and ssh open. Great.
On the guest, I can ssh into itself.
Form the guest I cannot ssh into the host.
From the host, I cannot see apache using Firefox, nor can I connect to the guest using SSH, nor can I use Nautilus and sftp:// to the guest - WTF ?!?!?!

Ping and Nmap work, but SSH/SFTP and Firefox do not (host <-> guest) - weird.

Any help much appreciated.

---

### Post by veloce on 2007-09-26
From my experience, the issue is to do with there being multiple routes between the guest and host.  I don't know how to do it, but I think the routing table needs to be altered to make sure communication works correctly.

My solution was to eliminate the bridged and nat networks and install a virtual firewall (IP Cop) with bridged and host only networking.  All communications with the host are then on the host only network (very fast).

Veloce

---

### Post by arunpc on 2007-10-04
I think i have seen this before. The solution is given in my blog.

[http://arunpc.wordpress.com/2007/10/04/cannot-ssh-into-a-vmware-guest/](http://arunpc.wordpress.com/2007/10/04/cannot-ssh-into-a-vmware-guest/)

Thanks,
Arun.PC

---

