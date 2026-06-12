---
title: "Weird Networking Glitch - Help !"
date: 2013-03-22
forum: General Help
---

### Post by Tim036 on 2013-03-22
I have two identical computers. One works fine and the other doesn't .

I've been playing with different WiFi dongles and I think one of the PC's objected !

Now Firefox on Internet using WiFi works great.

Ping does not

ssh does not

Ethernet has been unplugged.

How do I reset the Network ?

I'm happy to do it at a Bash level. But what do I do ? (I don't want to re-install the OS as Imvery happy with the rest of it. (Ubuntu 12.04 64 bit)

a very puzzled,

Tim

---

### Post by Tim036 on 2013-03-23
Guess its a re-install then.

It it possible to keep all my user directory on an install ?

: (

Tim

---

### Post by zero2xiii on 2013-03-23
Hay,

You really should wait at least 24 hours on these forums. They are not very active this time of day/night.

Anyway. Try some or all of this:

```
sudo /etc/init.d/networking restart
sudo dhclient **eth0**
```

eth0 shoudl be the device you network with. To check this:
 ```
ifconfig |grep eth
```

It should produce a result similar to:
```
**eth0**      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX 
```

Cheers

EDIT:
Just saw it was for wireless, so replace eth0 above with wlan0:
 ```
ifconfig |grep wlan
```

also try:
 ```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

Don't know how much more you want to "reset" the network.

EDIT 2:
All user settings and files are stored under: /home/username
So backing this up will save all the files (user related and created) and most settings.

---

### Post by Tim036 on 2013-03-23
Manu many thanks !

trying it right now !

:):):):)

Tim

---

### Post by Tim036 on 2013-03-23
ifconfig showed the wireless   was 'wlan1'

and the rest worked a dream !

Please accept the staus of ' MEGA HERO '.

I was dreading a re-install as this OS is working a dream !

:p:p:p

Tim

---

