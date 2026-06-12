---
title: "I need to learn my ip adress to open new port of my router"
date: 2007-05-29
forum: General Help
---

### Post by GooKaa on 2007-05-29
Like i wrote in the title ;
I need to learn my ip adress to open new port of my router.
I will open  a new port for aMule and Warcraft III but what an ip adress i have to write there ?

---

### Post by fanatik on 2007-05-29
typing ifconfig in a terminal will show you, it'll probably start with 192.168, eg:

```
james@maple:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:39:8A:4D
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
```

---

### Post by Docter on 2007-05-29
or

```
sudo route
```

---

### Post by fragos on 2007-05-29
The router has given you a local IP with NAT.  The router on your side will also have a local addresss.  Right click the network manager icon in the upper right applet bar and select "Connection Information".  I believe the address you want is called "Default Route:" aka gateway address.

---

### Post by GooKaa on 2007-05-30
thx for all its succesful.

---

