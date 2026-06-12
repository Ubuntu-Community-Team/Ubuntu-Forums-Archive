---
title: "sudo question/etc/network/interfaces"
date: 2005-07-24
forum: General Help
---

### Post by majikstreet on 2005-07-24
Hello,

I put this in my /etc/network/interfaces file after the stuff about wlan0:
up dhclient wlan0

And, when I reboot, I am not connected to the internet and I had to run: sudo dhclient wlan0. 

My question is, am I putting that in the file right? Do I need to put sudo in front of it? Or do I need to rephrase what I put in the file?

Thanks,
majikstreet

---

### Post by Takis on 2005-07-24
/etc/network/interfaces isn't a script file, so you can't run commands in it just like that.
Try putting this instead in your interfaces file```
iface wlan0 inet dhcp
auto wlan0
```In English, "auto wlan0" means bring wlan0 up at boot time, and the second line means "set interface wlan0's inet (a.k.a. IPv4) address to use DHCP".
If you need more info, type
```
man 5 interfaces
```at the command line.

---

### Post by majikstreet on 2005-07-24
[QUOTE=Takis]/etc/network/interfaces isn't a script file, so you can't run commands in it just like that.
Try putting this instead in your interfaces file```
iface wlan0 inet dhcp
auto wlan0
```In English, "auto wlan0" means bring wlan0 up at boot time, and the second line means "set interface wlan0's inet (a.k.a. IPv4) address to use DHCP".
If you need more info, type
```
man 5 interfaces
```at the command line.[/QUOTE]
 Will try that now.

Thanks.

---

### Post by majikstreet on 2005-07-24
Thanks, it works!!!

Thank you soooo much,
majikstreet

---

