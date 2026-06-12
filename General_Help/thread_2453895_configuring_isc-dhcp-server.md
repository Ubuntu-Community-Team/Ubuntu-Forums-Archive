---
title: "configuring isc-dhcp-server"
date: 2020-11-18
forum: General Help
---

### Post by sniper8752 on 2020-11-18
I am trying to configure this, and I set my interfaces variable to my internal interface on my server.  After  I do a restart of the service, I see that it is listening as follows:
```
[FONT=monospace][COLOR=#000000]udp        0      0 0.0.0.0:67              0.0.0.0:*                           2850/[/COLOR][COLOR=#FF5454]**dhcp**[/COLOR][COLOR=#000000]d          [/COLOR]
[/FONT]
```
This means all interfaces, right?  Is there any way to prevent this from happening?

---

### Post by SeijiSensei on 2020-11-19
Try specifying the interface on the command line. I haven't used dhcpd for a while myself, but I recall it was as simple as:

```
/usr/sbin/dhcpd eth1
```

---

### Post by sniper8752 on 2020-11-19
That did not work.  
I started it, did a status, and it says no subnet declaration for the external interface, so it's ignoring requests there, which is what I want, but I am surprised there isn't a way to just tell it to only listen on a certain interface.

---

### Post by HermanAB on 2020-11-19
Here you go:
[https://linux.die.net/man/5/dhcpd.conf](https://linux.die.net/man/5/dhcpd.conf)

No, we won't read the manual for you.

---

