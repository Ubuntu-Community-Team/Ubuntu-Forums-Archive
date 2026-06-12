---
title: "Installed Ubuntu using Wubi... anyway of getting rid of Vista completely?"
date: 2008-07-09
forum: General Help
---

### Post by bastones on 2008-07-09
Hello,

When I have installed Ubuntu using Wubi I'll want to completely remove Vista after (after I have made sure everything is working correctly). Would there be anyway of doing that?

---

### Post by wannadumpwindows on 2008-07-09
The short answer is no. Ubuntu's on a virtual disk, and there's not a simple way to get rid of windows, because it's "installed" inside windows.

---

### Post by bastones on 2008-07-09
and if I installed Ubuntu fresh with latest version would there be ndiswrapper or something like that, that would make my wireless adapter inside my laptop work?

---

### Post by wannadumpwindows on 2008-07-09
One way or another, you'd be able to get it working. Some cards are easier than others. What kind of wireless card do you have?

---

### Post by bastones on 2008-07-09
Where can I find the wireless card information from?

---

### Post by wannadumpwindows on 2008-07-09
In the terminal, you can use:

```
ifconfig
```

And

```
iwconfig
```

And post the output here.

---

### Post by bastones on 2008-07-09
Is that for checking on Windows? Nevertheless here's the output:

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : home
   Link-local IPv6 Address . . . . . : fe80::7ded:76e9:5908:b0a2%10
   IPv4 Address. . . . . . . . . . . : 192.168.1.65
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.254

---

### Post by wannadumpwindows on 2008-07-09
> **bastones said:**
> Is that for checking on Windows? Nevertheless here's the output:

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : home
   Link-local IPv6 Address . . . . . : fe80::7ded:76e9:5908:b0a2%10
   IPv4 Address. . . . . . . . . . . : 192.168.1.65
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.254

No, that was for in the linux terminal. In windows, you can just go into control panel, and then device manager i think it is. Then expand the tab for your wireless device.

---

### Post by bastones on 2008-07-09
Hope this is helpful:

Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter

---

### Post by curtis on 2008-07-09
That device has native support. You won't need ndiswrapper.

---

### Post by wannadumpwindows on 2008-07-09
Yup. You should be all set. You should have no trouble at all.

You can back-up anything you'd like to save, and then just do a re-install. And then you'd have a fresh slate.

---

