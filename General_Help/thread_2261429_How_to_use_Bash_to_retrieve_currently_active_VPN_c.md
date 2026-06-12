---
title: "How to use Bash to retrieve currently active VPN connection name?"
date: 2015-01-19
forum: General Help
---

### Post by tom155 on 2015-01-19
Hi,

I would like to write a bash script that I can add to the system monitor program so that I can display the currently active VPN connection name (as I've named it in the network connections) in the top bar.

I'm running Ubuntu 14.10. 

Does anyone know the code for this? I've had no luck with google and stuck on how to do it.

Thanks in advance :D

---

### Post by nerdtron on 2015-01-19
What does "ifconfig" from the terminal output? Maybe we can extract the output text there.

---

### Post by tom155 on 2015-01-19
This is the output from ifconfig dont think it has what i'm looking for unless we can using something in tun0 to link with the connection name in network manager?

```
eth0      Link encap:Ethernet  HWaddr 11:22:33:44:55:66          
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:398894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32642966 (32.6 MB)  TX bytes:32642966 (32.6 MB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.100.1.1  P-t-P:10.100.1.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3300 errors:0 dropped:110 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1089049 (1.0 MB)  TX bytes:375526 (375.5 KB)


wlan0     Link encap:Ethernet  HWaddr 11:22:33:44:55:66  
          inet addr:192.168.0.84  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: [FONT=Ubuntu Mono]fe80::28cf:38ff:fb7b:da19/64[/FONT] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15833304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12115971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10362781272 (10.3 GB)  TX bytes:5187567203 (5.1 GB)



```

---

### Post by nerdtron on 2015-01-19
Here's another command. I think the network manager applet has its own cli tool:
```

kenneth@nerdtron:~$ nmcli -p c
======================================================================================================================
                                                   Connection list
======================================================================================================================
NAME                      UUID                                   TYPE              TIMESTAMP-REAL                    
----------------------------------------------------------------------------------------------------------------------
Wired connection 1        79c94c31-9d44-4ac7-b90e-9ee5a098ee0f   802-3-ethernet    Mon 19 Jan 2015 12:08:29 AM PST   

```

Now we can grep the name of the connection you want.

---

### Post by tom155 on 2015-01-19
Thanks [COLOR=#000000]nerdtron! 

That command works well, however it shows all of the vpn connection choices I have. After your help i just found:

[/COLOR]```
[FONT=Ubuntu Mono]nmcli con status[/FONT]
```

[COLOR=#000000]it returns only the active connection[/COLOR][FONT=Ubuntu Mono]

[/FONT]```

NAME                      UUID                             DEVICES    DEFAULT  VPN   MASTER-PATH                                 
My_Router             caaa63ea-9fb6-11e4-89d3-123b93f75cba   wlan0             no       no    --                                          
VPN - USA             f47ac10b-58cc-4372-a567-0e02b2c3d479   wlan0             yes      yes   /org/freedesktop/NetworkManager/Devices/1  
```[COLOR=#000000]


[/COLOR]

---

### Post by steeldriver on 2015-01-19
You can also use the -f (--fields) option to limit the output to specific fields of interest e.g.

```

nmcli -f NAME,VPN,STATE con status

```
or (with : separators - useful for scripting since the connection name may contain whitespace)
```

nmcli -t -f NAME,VPN con status | awk -F: '$2=="yes" {print $1}'

```

---

### Post by tom155 on 2015-01-19
Works perfect thank you steeldriver!

:D

i'll mark as solved

---

