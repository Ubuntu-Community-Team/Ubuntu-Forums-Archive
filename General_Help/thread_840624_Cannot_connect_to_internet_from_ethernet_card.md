---
title: "Cannot connect to internet from ethernet card"
date: 2008-06-25
forum: General Help
---

### Post by geo909 on 2008-06-25
Hello everybody, I really need some help here..

I was given this kind of old laptop, a Compaq Presario 700.
It's about 5 years old or more (1.2 GHz, 256MB Ram).

Anyway, I am using an Ubuntu 7.10 live cd and I am connected to my router by USB. The connection was automatic immediately after I plugged the usb cord.

 However, that is not the case with the Ethernet card. Indeed there must be a problem.

[LIST=1]
When I plug in an Ethernet cable from the Ubuntu live CD, nothing happens. No internet.

[*]I have freshly installed Windows XP pro (I'm going to dual boot). When I plug in the Ethernet cable, windows search for a while and then a balloon pops up saying about limited connections and then no internet.

[*]Then I boot from a Puppy Linux live CD, I try to connect, puppy recognize my Ethernet card, finds the appropriate driver and says the connection is fine but -again- no internet..
[/LIST]

Btw, the router is set up well; I can connect from OpenSuse, Ubuntu, XP from both my desktop and my Dad's laptop by just plugging in the Ethernet cable.

 So I guess there is some hardware problems on my Presario? Do you think that this may be due to missing drivers? Though I had problems from XP, Ubuntu and Puppy Linux so that's strange..

 Please, I would really appreciate some help..

Thank a lot in advance

---

### Post by Thanoulis on 2008-06-25
I believe that your ethernet is broken, or is going to be soon enough...try to disable acpi (noacpi flag in grub, or by the bios settings) in case there is some kind of conflict. You can also try a crosswire connection to verify if your ethernet is really off or not.
If all fails then just go to the beach, enjoy the sun and have some beer...:popcorn:

---

### Post by John.Klockenkemper on 2008-06-25
I would like you to perform a few tests and paste the output into a reply for me.

1. Run ifconfig and paste the output.

2. open and copy the contents of your /etc/network/interfaces.

3. Are you running Network-Manager or not?

4. run lspci and paste the output.

---

### Post by geo909 on 2008-06-25
Thanks everybody for taking the time to answer this.


> **Thanoulis said:**
> I believe that your ethernet is broken, or is going to be soon enough...try to disable acpi (noacpi flag in grub, or by the bios settings) in case there is some kind of conflict. You can also try a crosswire connection to verify if your ethernet is really off or not.
If all fails then just go to the beach, enjoy the sun and have some beer...:popcorn:

No beach, no sun, no beer.. Exams!
(Guess you know the Greek exam periods.. The worst thing.)

> **John.Klockenkemper said:**
> I would like you to perform a few tests and paste the output into a reply for me.

1. Run ifconfig and paste the output.

2. open and copy the contents of your /etc/network/interfaces.

3. Are you running Network-Manager or not?

4. run lspci and paste the output.

Had to shut down the laptop. As soon as I reboot with the live cd I will post what you asked to..

---

### Post by geo909 on 2008-06-25
Here we are:

1)ifconfig output:
```

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:49:EF:5E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1A:4F:E3:91:20  
          inet addr:192.168.178.23  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4fff:fee3:9120/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1174387 (1.1 MB)  TX bytes:67931 (66.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

2)My /etc/network/interfaces contents:
```
ubuntu@ubuntu:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

3) Well, not sure..I'm just using the 7.10 live CD.. Booted with the default option. As I told before, I *can* connect from usb (not sure if that helps).

4)lspci output:
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 42)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)

```

Thanks again..

---

### Post by geo909 on 2008-06-25
Sorry!! I forgot to plug in the ethernet cable! Give me a minute and I will post again what needed..

EDIT: Here is the ifconfig command again with the cable plugged in (don't know if that makes any difference, so I just post it to be sure)

```

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:49:EF:5E  
          inet6 addr: fe80::208:2ff:fe49:ef5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:66 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:11 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1A:4F:E3:91:20  
          inet addr:192.168.178.23  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4fff:fee3:9120/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2114139 (2.0 MB)  TX bytes:192037 (187.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



```

---

### Post by geo909 on 2008-06-25
bump :(

---

### Post by geo909 on 2008-06-26
noone?!

---

### Post by Solicitous on 2008-06-26
Ok well I'm thinking perhaps your problem is hardware related.  Only two real things here could be going wrong I see, faulty ethernet port on the laptop (given no OS works, and XP reports limited or no connectivity), or faulty ethernet cable.

You mentioned the router works with another PC...are you using the same ethernet cable to connect the laptop to the router as you did the working PC?  If not, try using a different ethernet cable.

If that doesn't work, all I can suggest is look at the ethernet port on the laptop and make sure there aren't any bent pins.

---

### Post by geo909 on 2008-06-26
> **Solicitous said:**
> Ok well I'm thinking perhaps your problem is hardware related.  Only two real things here could be going wrong I see, faulty ethernet port on the laptop (given no OS works, and XP reports limited or no connectivity), or faulty ethernet cable.

You mentioned the router works with another PC...are you using the same ethernet cable to connect the laptop to the router as you did the working PC?  If not, try using a different ethernet cable.

If that doesn't work, all I can suggest is look at the ethernet port on the laptop and make sure there aren't any bent pins.

Thanks for your answer!

Yes, (unfortunately) I use the very same cable..
So I guess it's a hardware problem.
Will look for the pins, though it's too dark in there!

---

