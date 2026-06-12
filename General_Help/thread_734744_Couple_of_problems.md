---
title: "Couple of problems"
date: 2008-03-25
forum: General Help
---

### Post by sir_napsalot on 2008-03-25
Ok; 
First, I finally got Ubuntu to boot from disc had a couple of problems with some applications and peripherals right off the get-go. Tried using Firefox but it wasn't allowing me to view any sites. Any advice on how I can get this problem resolved?
Second, I have an Adesso CyberTablet 12000 which works with Ubuntu but it is very jumpy. What I mean by that is I can make a slow fluid motion with it and it will skip along the path but seems like the cursor is lagging behind the motion. But when I use my mouse I don't get that problem. Anyone heard of any problems similar to this?

---

### Post by cmnorton on 2008-03-25
It sound like you have no network connectivity. It would help getting you helped if you posted the output of ifconfig here.

Also, what does /etc/network/interfaces look like?

What kind of connection is this, wired or wireless?

---

### Post by sir_napsalot on 2008-03-25
Well I've determined that the problem is my integrated network card (Realtek RTL8139/810X) look at Realtek's site and they don't seem to have a Linux driver for my card. Downloaded a driver packet, not realizing that its for custom drivers >.<
As soon as I can get my network card to work with *Ubuntu* I'll be able to install my video drivers. If anyone knows of any third-party drivers for my specific network card written by a reliable source I'd be very appreciative!

P.S. - I haven't the faintest idea where to look for ifconfig. Can someone point me in the right direction?

---

### Post by forestpixie on 2008-03-25
Won't be able to help with the problem itself unfortunately - I've had as much wireless experience as you but if you're asked to post that sort of information it'll generally be from the terminal - which is in apps >accessories - so run these commands seperately from there and post the output here

```
ifconfig
cat /etc/network/interfaces
```

It might be better for you in future to use the absolute beginners forum - the expectation there is that you don't know :) , alos have a look in the network/ wireless forum - search for your card in there

[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

Good luck and welcome

---

### Post by sir_napsalot on 2008-03-25
heres what the ifconfig gave me:
eth0      Link encap:Ethernet  HWaddr 00:13:D3:20:E8:8c            
          inet6 addr: fe80::213:d3ff:fe20:e88c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:483 (483.0 b)  TX bytes:5495 (5.3 KB)
          Interrupt:16 Base address:0x6000
eth0:avah Link encap:Ethernet  HWaddr 00:13:D3:20:E8:8C  
          inet addr:169.254.8.118  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x6000
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)
hope this helps! will post the /etc/network/interfaces shortly

---

### Post by sir_napsalot on 2008-03-25
results from running the cat /etc/network/interfaces command:

auto lo
iface lo inet loopback

---

### Post by cmnorton on 2008-03-26
I misread your reponse. Mea culpa. Is it feasible for you to get a new network card, USB or Cardbus (if a laptop)?

Your /etc/network/interfaces looks like mine --

auto lo
iface lo inet loopback

-- and my networking regular and VPN did not work at all until I modified my interfaces file to look like this. Of course, I have not tried a static address and VPN. (I like to linger for a long time on some successes, and I don't need static IP addresses at home. )

---

### Post by cmnorton on 2008-03-26
Suggest you check this out:

[https://answers.launchpad.net/ubuntu/+question/19556](https://answers.launchpad.net/ubuntu/+question/19556)

---

### Post by sir_napsalot on 2008-03-27
Well I've tried just about everything available to me, that I know of. As far as I can tell my NIC just isn't compatible with *Ubuntu*. So I'm just going to have to spend the time, effort and money :( to get a new NIC that is compatible. Thanks for all the great advice everyone and I'll keep my posts in the noob area from now on. Once again thank you.

---

### Post by gaussian on 2008-03-27
Do not give up yet. Your NIC is Ubuntu and Linux compatible almost certainly. Just read the discussion on the following link:
[http://ubuntuforums.org/showthread.php?t=538448&highlight=RTL8139](http://ubuntuforums.org/showthread.php?t=538448&highlight=RTL8139)

This is what cmnorton was suggesting above. Trust me on this one, I have a computer with the same card. If you are dual booting between XP and Ubuntu, you just need to go to XP settings and change the "Wake-up-on-LAN" setting. Or you can power cycle your computer.

Caveat: If you have dual boot and you don't change your Windows settings you'll need to power cycle your computer every time when switching from XP to Ubuntu.

---

### Post by sir_napsalot on 2008-04-27
well i finally bit the bullet and installed <i>Ubuntu</i>. Now the networking card works fine with no problems. Thanks for all the help!

---

