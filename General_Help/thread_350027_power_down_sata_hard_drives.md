---
title: "power down sata hard drives"
date: 2007-01-31
forum: General Help
---

### Post by Beer Barron on 2007-01-31
hi all, im using kubuntu 6.10 here and i want to power down my hard drives after a set amount of time like 1hr or something.

now, the problem i got is there all sata hard drives and they come up as scsi drives so i cant use hdparm to power them down, what can i do?

---

### Post by MoLE on 2007-01-31
Try the following:
```
sudo aptitude install sdparm
sudo sdparm --set SCT=50 /dev/sda
```

This will set a 5 minute timeout for the drive to spin down.

See the [sdparm man page]("http://sg.torque.net/sg/sdparm.html#mozTocId262297") for more details.

---

### Post by Beer Barron on 2007-01-31
wooooo thanks man :D

---

### Post by MoLE on 2007-02-02
Your're welcome.  Remember, [google]("http://www.google.com/linux") is your friend.

---

