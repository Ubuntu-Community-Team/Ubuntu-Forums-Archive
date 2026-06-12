---
title: "Thunderbird won't connect to server after edgy upgrade"
date: 2006-11-03
forum: General Help
---

### Post by oliwally on 2006-11-03
I've just upgraded from dapper to edgy (Kubuntu) and most things are working well as before. However, Thunderbird doesn't seem to be connecting to the server any more and I keep getting error messages indicating this when trying to check my mail. It's definitely not the server - I can check the same accounts from my other computer and even from the WinXP boot on the same computer (dual boot Laptop Kubuntu 6.10 and WinXP).

Can anyone help or point me to other post? I looked for some time but could not find any help in existing posts.

---

### Post by simoncullen on 2006-11-06
Bump...  Same problem here.  Neither IMAP nor POP3.  This was on a clean install of Edgy.  I also cannot browse HTTPS sites in firefox, though I can in Konquerer. . .

---

### Post by simoncullen on 2006-11-06
Ah Ha! You need to disable IPv6 and everything will be fine again.  Or at least that's what I've found.  I now have the most perfect setup: my life's work for this afternoon is done.

---

### Post by oliwally on 2006-11-08
> Ah Ha! You need to disable IPv6 and everything will be fine again. Or at least that's what I've found. I now have the most perfect setup: my life's work for this afternoon is done.

And how is this done please? (and what does it do?)

---

### Post by oliwally on 2006-11-10
> **oliwally said:**
> And how is this done please? (and what does it do?)

Ok, I've done some looking and disabled ipv6 by putting the line 
```

KDE_NO_IPV6=true
```

at the end of /etc/environment.  But it has made no difference. Thunderbird is not connecting. Everything else is fine - it all connects to the network/internet.

I really need some help. Please, please help me.

---

### Post by oliwally on 2006-11-11
> **oliwally said:**
> I've just upgraded from dapper to edgy (Kubuntu) and most things are working well as before. However, Thunderbird doesn't seem to be connecting to the server any more and I keep getting error messages indicating this when trying to check my mail. It's definitely not the server - I can check the same accounts from my other computer and even from the WinXP boot on the same computer (dual boot Laptop Kubuntu 6.10 and WinXP).

Can anyone help or point me to other post? I looked for some time but could not find any help in existing posts.

Bump ;)

---

### Post by simoncullen on 2006-11-11
Can you post the result of "ifconfig" ?


Simon

---

### Post by oliwally on 2006-11-11
> **simoncullen said:**
> Can you post the result of "ifconfig" ?


Simon

Thanks so much for replying. Here it is:

```


eth0      Link encap:Ethernet  HWaddr 00:15:C5:1B:FE:49
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185

eth1      Link encap:Ethernet  HWaddr 00:13:02:AC:4F:1F
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:feac:4f1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1589 errors:1 dropped:23 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:109936 (107.3 KiB)  TX bytes:27111 (26.4 KiB)
          Interrupt:177 Base address:0x6000 Memory:dcfff000-dcffffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

---

### Post by simoncullen on 2006-11-11
```
 eth1      Link encap:Ethernet  HWaddr 00:13:02:AC:4F:1F
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
         **_ inet6_** addr: fe80::213:2ff:feac:4f1f/64 Scope:Link
```


So IPv6 is still switched on.  I can't remember how exactly I managed to get rid of it, but there was some difficulty.  Have you tried blacklisting the IPv6 module?

Simon

---

### Post by oliwally on 2006-11-12
I've got it!

Yes, it was the ivp6. 

The method listed above did not seem to work, so here is how I managed to switch it off in the end:

```
1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off ipv6
4. Save the file and reboot
```

Found it at :
[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

Thanks for your help everyone. Thunderbird now thundering away.

---

