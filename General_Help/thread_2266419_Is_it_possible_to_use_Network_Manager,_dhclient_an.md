---
title: "Is it possible to use Network Manager, dhclient and avahi-daemon on only 1 interface"
date: 2015-02-22
forum: General Help
---

### Post by mindaa on 2015-02-22
My situation is that I have two wireless network interfaces, wlan0 and ra0.  I want to be able to use the network manager, dhclient and avahi-daemon on the ra0 interface and not have it in any way effect the wlan0 interface.  I want to manually manage the channel and various configuration settings on my wlan0 interface.  I have searched and have not been able to find a good way to do this.  I have spent quite a while goggling this issue and have not been able to find an answer that works.  I am not looking for an exact answer(though i wouldn't hate it) I would really love some advice that would set me off in the right direction so I can perhaps find it on my own and post back my solution.  I have included several outputs of what I think could be important settings.  Please let me know if you need anything else.  Also I forgot to mention and its probably not relevant but the ra0 interface is not the typical "wlan0 or wlan1" as it is a patched native driver which I have had to edit several times so I believe this is the reason for the strange naming convention. 


```

dylan@xaelah:~$ iwconfig
ra0       Ralink STA  ESSID:"MYWIFIACCESSPOINT"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 40:8B:07:79:C5:B6
          Bit Rate=52 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=84/100  Signal level:-57 dBm  Noise level:-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

dylan@xaelah:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:bf:9a:01
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22652 (22.6 KB)  TX bytes:22652 (22.6 KB)


ra0       Link encap:Ethernet  HWaddr 10:c3:7b:c8:a9:30
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::12c3:7bff:fec8:a930/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78880 errors:0 dropped:1 overruns:0 frame:0
          TX packets:50929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:103503442 (103.5 MB)  TX bytes:6992688 (6.9 MB)
          Interrupt:16


wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:65:c6:61
          inet6 addr: fe80::2c0:caff:fe65:c661/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:99911 (99.9 KB)  TX bytes:32312 (32.3 KB)


dylan@xaelah:/etc/NetworkManager$ cat NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false



```

If you need anything else please ask, I will be sure to respond ASAP which will be with in minutes.

Thanks guys!

---

### Post by steeldriver on 2015-02-22
What do you mean by "manually manage" exactly? AFAIK, once you create an entry for an interface in /etc/network/interfaces, then network-manager will ignore it (consider it "unmanaged") by default - that's what the 'managed=false' line in the conf file's [ifupdown] section means. Have you actually tried it?

---

### Post by mindaa on 2015-02-22
@steeldriver Thank you sir that was a great idea. I was being extremely dense about this for some reason, i pulled up the documentation for the Network Manager Configuration file and found unmanged-devices as a configuartion option. So I issued the command ```
sudo pico /etc/NetworkManager/NetworkManager.conf
``` and changed the configuaration file from:

```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false

```

to the following:

```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


[keyfile]
unmanaged-devices=mac:00:c0:ca:65:c6:61

```


Then I rebooted and network manager was none the wiser to the existence of my wlan0 interface which is exactly what I wanted!!!

 was trying to solve this problem by configuring wlan0 to not use network manager, as opposed to the other way around.  So stupid now that I realize the proper way to do it.  Thanks!!!

---

### Post by steeldriver on 2015-02-22
TBH I'd forgotten about the unmanaged-devices option (although I've used it in the past to work around a misbehaving internal wireless device that would lock up my system). I was thinking more about adding a line like 'iface wlan0 inet manual' to /etc/network/interfaces. Whatever works!

---

