---
title: "[SOLVED] Share Internet Connection - Wirelessly"
date: 2008-06-16
forum: General Help
---

### Post by computer_freak_8 on 2008-06-16
[FONT="Verdana"]I'm trying to share my internet connection, with no luck. I use a Sprint card located at "/dev/ttyUSB0" to connect to the internet. I tried using the tutorial at <a href="http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html">this link</a> ( [http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html](http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html) ) to get me going, but when I issue the command 

[FONT="Lucida Console"] sudo iwconfig ath0 essid multiboot-as-host mode ad-hoc [/FONT]

 I get the error 

[FONT="Lucida Console"]Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
[/FONT]

I don't know what to do. I try using the [TAB] key to help me, but nothing - it shows "ad-hoc" (no quotes) is the correct argument, and when I try 

[FONT="Lucida Console"]sudo iwconfig ath0 essid multiboot-as-host mode adhoc[/FONT]

I get 

[FONT="Lucida Console"]Error for wireless request "Set Mode" (8B06) :
    invalid argument "adhoc".
[/FONT]

Any ideas, anyone? (Note: I can enter the command
[FONT="Lucida Console"] sudo iwconfig ath0 essid multiboot-as-host [/FONT] 
and it completes without errors.)

[/FONT]

---

### Post by plucky on 2008-06-16
> sudo iwconfig ath0 essid multiboot-as-host mode ad-hoc


Try ```
sudo iwconfig ath0 essid multiboot-as-host mode Ad-Hoc
```


Linux is case sensitive


Good Luck

---

### Post by computer_freak_8 on 2008-06-16
> **plucky said:**
> 

Linux is case sensitive



Yes, I saw that on the link I gave, they have it capitalized - on the online Linux manpage (or wherever it was) it showed it lowercase... anyhow:

```
jaredtbrees@multiboot:~$ sudo iwconfig ath0 essid multiboot-as-host mode Ad-Hoc
[sudo] password for jaredtbrees: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
jaredtbrees@multiboot:~$ 

```

so, it still doesn't like me...

---

### Post by ericguo on 2008-06-17
run "ifconfig down" first
```

sudo ifconfig ath0 down
sudo iwconfig ath0 essid multiboot-as-host mode Ad-Hoc
sudo ifconfig ath0 up

```
hope this help

---

### Post by computer_freak_8 on 2008-06-17
[FONT="Lucida Console"]jaredtbrees@multiboot:~$ sudo iwconfig ath0 essid multiboot-as-host mode Ad-Hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
jaredtbrees@multiboot:~$ sudo iwconfig ath0 essid multiboot-as-host mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
[/FONT]

What really gets me is that when I type:

[FONT="Lucida Console"]sudo iwconfig ath0 essid multiboot-as-host mode [/FONT]

followed by the [TAB] key twice, it tells me:

[FONT="Lucida Console"]ad-hoc     managed    master     monitor    repeater   secondary  [/FONT]

But when I try it, no luck!


I get the same error with all the others - except "managed" - it processes without errors.

However, if I type in something random as an argument (like the word "purple"), I get: 

[FONT="Lucida Console"]jaredtbrees@multiboot:~$ sudo iwconfig ath0 essid multiboot-as-host mode purple
Error for wireless request "Set Mode" (8B06) :
    invalid argument "purple".
jaredtbrees@multiboot:~$ 
[/FONT]

So, it is apparent that it sees some sort of difference, but it still won't process it. Maybe I need to reinstall the software? If so, how do I do that?

Thanks,
computer_freak_8

---

### Post by computer_freak_8 on 2008-07-02
Okay, does anyone know if this could be caused by some sort of incompatibility with my wireless card? Here is the result of "lspci", with (what I feel is) the relevant line in bold:

[FONT="Lucida Console"]jaredtbrees@multiboot:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0612 (rev a2)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
**05:0a.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)**[/FONT]


It is a Dynex card. (Dynex is Best Buy's generic brand of electronic equipment.)

Any ideas??


computer_freak_8

---

### Post by computer_freak_8 on 2008-07-02
I think I might have fixed, but I still have to test it. Take a look at:


```
jaredtbrees@multiboot:~$ sudo wlanconfig ath0 destroy
jaredtbrees@multiboot:~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode adhoc
ath0
jaredtbrees@multiboot:~$ sudo iwconfig ath0 essid multiboot-as-host mode Ad-Hoc
jaredtbrees@multiboot:~$ sudo ifconfig ath0 up
jaredtbrees@multiboot:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ppp0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"multiboot-as-host"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:14:A5:CB:45:44   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

(I found some of these commands on the madwifi website)

---

### Post by computer_freak_8 on 2008-07-03
Yes, it worked. Now to get Squid working...

---

