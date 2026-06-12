---
title: "microsoft GPS-168 ublox 1372?"
date: 2014-01-30
forum: General Help
---

### Post by metroedged on 2014-01-30
[ATTACH=CONFIG]249944[/ATTACH]Does anyone know if this GPS reciever is supported in ubuntu?

[http://i.imgur.com/K3Ruq4z.jpg](http://i.imgur.com/K3Ruq4z.jpg)

---

### Post by tomearp on 2014-01-30
Yes it will most likely work. The sticks are generally just GPS devices that spew serial data, connected to a USB-serial adapter.

I have used a cheapo GPS stick with a Raspberry Pi and it works fine. I wrote a [blog post]("http://tomearp.blogspot.co.uk/2012/07/using-usb-stick-gps-receiver-with.html") about it, the instructions will be essentially the same in Ubuntu.

---

### Post by metroedged on 2014-01-30
> **tomearp said:**
> Yes it will most likely work. The sticks are generally just GPS devices that spew serial data, connected to a USB-serial adapter.

I have used a cheapo GPS stick with a Raspberry Pi and it works fine. I wrote a [blog post]("http://tomearp.blogspot.co.uk/2012/07/using-usb-stick-gps-receiver-with.html") about it, the instructions will be essentially the same in Ubuntu.

I actually figured out that ubuntu had automatically installed the drivers for it. I just had a bit of trouble navigating the program menus to enable the GPS and show the real time data/location. Also, it seems there are no working navigation programs, unfortunately :(

---

