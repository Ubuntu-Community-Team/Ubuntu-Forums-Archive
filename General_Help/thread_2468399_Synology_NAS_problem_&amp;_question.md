---
title: "Synology NAS problem &amp; question"
date: 2021-10-28
forum: General Help
---

### Post by uros-likar on 2021-10-28
I recently migrated from Windows to Ubuntu (KDE). 

The problem:
I own a Synology NAS which I ca'n login to like I did on Windows.  To get to the admin I accessed [https://somename:5001](https://somename:5001) with a browser, but in Ubuntu that page doesn't exist. In windows I'm in default "WORKGROUP" same as defined in samba config under Ubuntu. I don't have a certificate so I turned that off, so I could access it via [http://somename:5000](http://somename:5000) but no luck. Anyone had similar experience? Maybe I need to configure that 5001 and 5000 port in Ubuntu (if, yes => how)?

The Question:
How I can mount shared drives on that NAS?? I can access them with Samba but there I have limitations like I can't play video from it. Probably I need to turn on SSH acces on NAS and mount drives or something similar?

---

### Post by HermanAB on 2021-10-28
Try the IP address instead of the hostname.  For example:
[https://192.168.0.1:5000](https://192.168.0.1:5000)

Connect with Windows, then find the IP address by looking on your router DHCP status, or snoop it with tcpdump or ettercap or some such.

---

### Post by ActionParsnip on 2021-10-28
Can you ping the name and get an IP back OK?
Can you ping the IP and get replies?
Can you telnet to the network socket and get a connection (Run "telnet somename 5000" in a terminal)?

---

### Post by uros-likar on 2021-10-28
If I ping in windows I get ip6 address 

Telnet returns:
[FONT=monospace][COLOR=#000000]telnet: could not resolve somename/5000: Temporary failure in name resolution[/COLOR]
[FONT=monospace][COLOR=#000000]telnet: could not resolve [FONT=monospace][COLOR=#000000]somename[/COLOR][/FONT]/5001: Temporary failure in name resolution[/COLOR]


[/FONT]

[/FONT]

---

### Post by Morbius1 on 2021-10-28
You could use the IPv6 address to access the server but if you want a more customary IPv4 address specify that in your ping on Windows:
```
ping hostname -4
```

---

### Post by uros-likar on 2021-10-28
thanx, now I can access my nas with url [https://192.168.0.13:5001/](https://192.168.0.13:5001/)

How to deal with this if I didn't had windows at disposal?

---

### Post by Morbius1 on 2021-10-28
It's my understanding that Synology NAS is Apple friendly so you should be able to ping it with it's mDNS hostname in Linux:

```
ping -c3 hostname.local
```

EDIT: Most of the posts I see on this device have the host name of diskstation so you would use diskstation.local. Don't know if that is the default?

---

### Post by uros-likar on 2021-10-28
Under newtwork in synology control panel I had to turn on "Enable customized domain" and set it as "synology". After I've done that I was able to ping it and get the ip which I don't need anymore because I can connect to it via [https://synology.local/](https://synology.local/)

This is all fine but I managed to set this because I found admin IP with help of Windows. If I didn't had it, how I could find that IP ? Is there a local ip scan ot something similar?

---

