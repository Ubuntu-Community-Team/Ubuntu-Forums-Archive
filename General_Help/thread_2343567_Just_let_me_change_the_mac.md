---
title: "Just let me change the mac"
date: 2016-11-17
forum: General Help
---

### Post by philomathus206 on 2016-11-17
I have two laptops: one containing Ubuntu 16.10 and the other containing Xubuntu 16.04. I tried spoofing both of their MAC addresses, but it won't work. 

Here's what I did:

```

root@cerebro-N150P:~# ifconfig -a


enp9s0    Link encap:Ethernet  HWaddr e8:11:32:5e:23:5e  
          
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
          collisions:0 txqueuelen:1000 
          
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
          Interrupt:18 






lo        Link encap:Local Loopback  
          
      inet addr:127.0.0.1  Mask:255.0.0.0
          
      inet6 addr: ::1/128 Scope:Host
          
      UP LOOPBACK RUNNING  MTU:65536  Metric:1
          
      RX packets:2268 errors:0 dropped:0 overruns:0 frame:0
          
      TX packets:2268 errors:0 dropped:0 overruns:0 carrier:0
          
      collisions:0 txqueuelen:1 
          
      RX bytes:168104 (168.1 KB)  
      TX bytes:168104 (168.1 KB)






wlp5s0    Link encap:Ethernet  HWaddr b4:74:9f:e9:d7:25  
          
      BROADCAST MULTICAST  MTU:1500  Metric:1
          
      RX packets:0 errors:0 dropped:0 overruns:0 frame:472
          
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
      collisions:0 txqueuelen:1000 
          
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
      Interrupt:16 






root@cerebro-N150P:~# service network-manager stop

root@cerebro-N150P:~# ifconfig enp9s0 down

root@cerebro-N150P:~# ifconfig lo down


root@cerebro-N150P:~# ifconfig wlp5s0 down


root@cerebro-N150P:~# ifconfig wlp5s0 hw ether 4e:ad:4c:71:ca:cd


SIOCSIFHWADDR: _Too many open files in system_




root@cerebro-N150P:~# macchanger-gtk


[ERROR] Could not change MAC: interface up or insufficient permissions: _Too many open files in system_

```

I even tried this command:

```
root@cerebro-N150P:~# sysctl -w fs.file-max=999999

```

And did the same sequence of commands in the first code box.

I also tried "edit connections" and filled "clone", but it still won't work. ](*,)

I'm really stumped guys, I hope you can help me.

---

### Post by TheFu on 2016-11-17
SIOCSIFHWADDR: Too many open files in system

You'll need to figure out why that is happening.

The general answer is:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether  xx:xx:xx:xx:xx:xx
sudo ifconfig eth0 up
sudo service  networking restart

```
Just replace the device with yours and put in whatever MAC you like (needs to be valid hex). I had to restart networking, so DHCP would be refreshed. My normal MAC is static (dhcp-reservation) on this subnet for convenience. 

BTW, I just tested the above and it is working here on 16.04 - using an Intel wifi NIC. No *too many files open* issue.  When it comes to networking stuff, Intel. The others just aren't worth the hassles - especially for wired connections.

---

### Post by philomathus206 on 2016-11-17
> **TheFu said:**
> 
The general answer is:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether  xx:xx:xx:xx:xx:xx
sudo ifconfig eth0 up
sudo service  networking restart

```


I tried all of those, they did not work (initially). I have been delving through forums for hours, and I've finally found out what's wrong. Turns out, it was my network card. Both of the laptops I tried to spoof use Broadcom network cards, which isn't "really" compatible with Linux, so I replaced them with Qualcomm network cards (I have a repository of computer components), tried them spoofing again, and it worked!

 :guitar:

---

### Post by oldrocker99 on 2016-11-17
Since your problem has been resolved, please use the Thread Tools to mark this thread as [SOLVED].

Thanks.

---

