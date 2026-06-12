---
title: "Built in webcam on DV6000 help"
date: 2007-12-30
forum: General Help
---

### Post by jasonpeinko on 2007-12-30
How do i get my built in webcam to work  with ubuntu, i cant even tell if it is being picked up

```

jasonpeinko@jasonpeinko-laptop:~$ lsusb
Bus 002 Device 007: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 006: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 064e:a101 Suyin Corp. 
Bus 001 Device 001: ID 0000:0000  


```

I have no idea how to get it to work because i cant even find out which one it is

---

### Post by breaking on 2008-01-23
```
Bus 004 Device 003: ID 064e:a101 Suyin Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0084 Microsoft Corp. 
Bus 001 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

m having same problem to,
mine is HP pavilion dv9000 serias laptop.

anyboy here with a solution, plz help.

p.s. i've tried drivers from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) but still my camorama shows error like,
"could not connect to vedio device /dev/video0"

---

### Post by cdtech on 2008-01-23
I have the same cam:

```
Bus 001 Device 003: ID 064e:a101 Suyin Corp.
```

I had no problems setting the cam up on my HP. Using Skype and Ekiga webcam.

---

### Post by jasonpeinko on 2008-01-26
with ekiga
```

Error while opening video device HP Webcam

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Your video driver doesn't support the requested video format.

```

i cannot open it with vlc either

---

### Post by quequeque2 on 2008-03-18
i also got a d6000 and i cant make it work on ubuntu

does anybody have a working built-in webcam that is working with ubuntu?
if yes, please tell mehow you did it

---

