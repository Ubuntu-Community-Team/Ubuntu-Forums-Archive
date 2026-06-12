---
title: "No wireless in 12.04  RTL8101E/RTL8102E and  Intel Network Cntrlr Intel 08b2 (rev 73)"
date: 2013-12-03
forum: General Help
---

### Post by segfault666 on 2013-12-03
I have had no luck installing wireless in ubuntu 12.04  In my Lenovo ideapad flex dual-boot. With the following network controler and ethernet.

Network controller: Intel Corporation Device 08b2 (rev 73)    Subsystem: Intel Corporation Device 4262
    Flags: bus master, fast devsel, latency 0
    Memory at b0400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>


Ethernet Controller
    Subsystem: Lenovo Device 3805
    Flags: bus master, fast devsel, latency 0, IRQ 59
    I/O ports at 3000 [size=256]
    Memory at b0504000 (64-bit, non-prefetchable) [size=4K]
    Memory at b0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8101
    Kernel modules: r8101


eth0      Link encap:Ethernet  HWaddr 08:9e:01:db:c3:9d  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a9e:1ff:fedb:c39d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84943527 (84.9 MB)  TX bytes:4550744 (4.5 MB)
          Interrupt:59 Base address:0x4000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:364991 (364.9 KB)  TX bytes:364991 (364.9 KB)


I have tried to follow the posts at the link below but have no luck.  
[http://ubuntuforums.org/archive/index.php/t-2093992.html](http://ubuntuforums.org/archive/index.php/t-2093992.html)

Any help would be wonderful. I am a noob! Thanks.

---

### Post by jboyette on 2013-12-04
go to the command line and type the following rfkill list.  If your devices show blocked, then type rfkill unblock <device>.

If you get permission denied, then add sudo to the beginning of the command, and type your passworrd when asked.

---

### Post by chili555 on 2013-12-04
RTL8101E/RTL8102E is your ethernet card, not wireless. In order to see your wireless, I believe we need more information. From a terminal, please run and post:```
rfkill list all
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

PS- If the device turns out to be this:> 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [[COLOR="#FF0000"]8086:08b2[/COLOR]] (rev 73)...then we can install the driver with a fair amount of difficulty. If, on the other hand, you install 13.10, it will work out of the box! I will be happy to help in either case.

---

### Post by segfault666 on 2013-12-04
Of course that is the device!    
 rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
segfault@666:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
segfault@666:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Device [8086:08b2] (rev 73)


Thanks for the reply.  I will try 13.10  Appreciate your help!

---

### Post by segfault666 on 2013-12-04
13.10 worked! Thanks alot chili555

---

### Post by chili555 on 2013-12-04
I suggest you try the live CD. If it works well, and I'm pretty confident it will, just click 'Install,' and you should be all set!

---

### Post by dny1020 on 2014-01-02
how can i go about installing the driver ? ```
$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Intel Corporation Device [8086:08b2] (rev 73)


```
how is it difficult?

---

### Post by dny1020 on 2014-01-03
actually you can fix by updating the kernel

---

### Post by chili555 on 2014-01-03
> **dny1020 said:**
> actually you can fix by updating the kernelSince you answered your own post, I assume you are all set. If you need additional guidance, please post back.

---

