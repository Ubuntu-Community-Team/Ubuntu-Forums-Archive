---
title: "Wifi Connection issues (hardware issue?)"
date: 2007-05-19
forum: General Help
---

### Post by shadowimmage on 2007-05-19
I have just installed Feisty Fawn on my **IBM T30** as a dual Windows-Linux system, but I am having a problem getting the wireless to connect or even work while I'm in Ubuntu.

When I check my available adapters it shows my modem, my Ethernet card, and **2** wireless connections!

I have **eth0** **eth1** and **wifi0**
eth0 is the wired connection, and it works fine - checked this morning at my house
eth1 and wifi0 show up as wireless connections, but I only have 1 wifi card (**Cisco 350** series, PCMCIA card, airo_cs driver (70% sure about that...)) 

the wireless networks show up, and the one i want to connect to has no security, but when I click on it, nothing ever happens. once I got it to say it was connected, but i couldn't do anything online and the actual card looked dead - None of the LEDs were doing anything at all.

I also have an infrared port on this computer, and I was thinking that might be a problem? maybe that's one of the "wireless connections"? 

I want to know whether this is a hardware or software issue. Right now I'm on Windows, and everything is fine. I'm on wireless right now, and there's no problem at all. But in linux, my card doesn't even seem to be powered, and only sporadically, sometimes the LEDs will jump to life, and then nothing. 

I can see the networks, but I can't connect, and if it thinks it's connected, then it won't do anything, and I don't seem to have any sort of IP, even though it's a DHCP, and automatically assigns me an IP in windows.

Also, after running iwconfig, both eth1 and wifi0 show EXACTLY the same information... so I don't know what's going on.

Please help! I would like to use Ubuntu, but without wireless it's pretty useless, and I am stuck with crappy windows.

thanks-
shadowimmage

---

### Post by shadowimmage on 2007-05-19
I was doing some things in the terminal, and noticed something:

```
chase@shadowimmage:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

chase@shadowimmage:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6B:D0:CE:E3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4336 (4.2 KiB)  TX bytes:4336 (4.2 KiB)

chase@shadowimmage:~$ 

```

this is with my wireless card not plugged in, notice that there is the same adapter in both sections... what is causing this and how do I fix it??

---

### Post by Cene on 2007-05-19
What is the output of iwconfig command with your card plugged in?
You should also try the ndiswrapper driver. On my laptop with broadcom 4300 wireless card i have to do the following at each boot:
```

# iwconfig wlan0 essid SpeedStream enc off
# dhclient wlan0

```

The SpeedStream there is the name of my wlan box and enc off tries to connect without any passwords etc, just like you want to.
I also have blacklisted the original driver (bcm43xx) at /etc/modprobe.d/blacklist, compiled ndiswrapper myself (back then the version in repos had no support for that card; dunno if it's fixed) and installed the driver .inf file with ndiswrapper. You can usually get the .inf from your wlan card's Windows drivers.

Check also this: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by broughcut on 2007-05-19
> **shadowimmage said:**
> 
Also, after running iwconfig, both eth1 and wifi0 show EXACTLY the same information... so I don't know what's going on.


it's not recognised as a wireless card. I doubt it's exactly the same info - does it have its own HWaddr/MAC address? Or is the MAC empty? If it has a unique MAC address, you're on the right path, you probably just need to get the driver. If the MAC is a string of zeros you have a little bit more fiddling ahead.

Does the card use the Intersil Prism chipset? If so, have you installed linux-wlan-ng?

---

