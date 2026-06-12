---
title: "GPS over Bluetooth, GPSD rfcomm already in use."
date: 2013-04-25
forum: General Help
---

### Post by buffy^ on 2013-04-25
Ok I am using ubuntu 12.10 and Galaxy note.
Connected via bluetooth to rfcomm1 using BT GPS over BT from the play store [https://play.google.com/store/apps/details?id=com.Saenko.GpsOverBt&hl=en](https://play.google.com/store/apps/details?id=com.Saenko.GpsOverBt&hl=en)

I am able to cat /dev/rfcomm1 and get a updating list of GPS info pouring though however when I attempt to connect GPSD to it I get the error that it is already open by another process.

Command I used sudo gpsd -bNnD 2 /dev/rfcomm1

I have checked for background GPSD tasks using ps -C gpsd and tried killall -TERM gpsd I found nothing.

I have trawled google, and checked many different threads and posts and still I cant work out what using /dev/rfcomm1 (except hcitool connect 1) or a way of telling GPSD not to check.

---

### Post by buffy^ on 2013-04-28
so it looks like bluetoothd is acessing rfcomm, so you need to bind it by hand and change the permissions in the udev file.

---

### Post by tgalati4 on 2013-04-28
```
sudo chmod 777 /dev/rfcomm1
```

Try that, and if it works then you can dial back the permissions to 755 and see if it still works.  Add that to your udev script or a custom launcher when you bring up your gps app.

For stress-testing, I have had 7 instances of gpsdrive grabbing gps data from one USB GPS puck, so I know that the gps stack is fairly robust.  Processes went from 400 to 4000 when I started the 8th instance.

---

