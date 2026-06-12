---
title: "ubuntu 14.04 server setup help"
date: 2014-10-07
forum: General Help
---

### Post by guldberg72 on 2014-10-07
Hey. I am working on putting my first ubuntu 14.04 lts server up. 
i have managed to setup a server before in the desktop envi. but when it it all is terminal based i am hitting a wall :S


```
**sudo nano / etc / network / interfaces **


#iface eth0 inet dhcp 
# The loopback network interface 
auto lo 
iface lo inet loopback 


# The primary network interface 
auto eth0 
#iface eth0 inet dhcp 
**iface eth0 inet static **
**address 192.168.1.120 **
**netmask 255.255.255.0 **
**network 192.168.1.0 **
**broadcast 192.168.0.255 **
**gateway 192.168.1.0** 
```



```
**sudo nano /etc/resolvconf/resolv.conf.d/base **

**nameserver 192.168.1.1 **

```




my local ip  is 192.168.1.120 
and the router's IP is 192.168.1.1 




after I have entered above (in bold) and restarted the machine  i loose my internet connection. if i hit ifconfig the eth0 is missing and the lo is the only one there ??
it must be said it's this guide I have used [https://www.youtube.com/watch?annotation_id=annotation_2592210455&feature=iv&src_vid=xWVcUHo8YWg&v=EmdqwvPppXg](https://www.youtube.com/watch?annotation_id=annotation_2592210455&feature=iv&src_vid=xWVcUHo8YWg&v=EmdqwvPppXg) and it goes wrong at 3.40 min

---

### Post by SeijiSensei on 2014-10-07
> sudo nano / etc / network / interfaces 

If that's really what you typed, with the extraneous spaces, then you didn't edit the interfaces file.

---

### Post by guldberg72 on 2014-10-07
without the spaces :D 
but i think where i am wrong is that i have entered some wrong numebrs/address but i cant figure out witch..

---

### Post by matt_symes on 2014-10-07
Hi

> **gateway 192.168.1.0**

Should be

```
gateway 192.168.1.1
```

Assuming your router is your gateway :)

Kind regards

---

### Post by Michael_McKenney on 2014-10-07
I think the gateway should be 192.168.1.1 not 0.1.  The address is 1.120 and network is 1.0.  Unless you changed your internal router address like I do.

---

