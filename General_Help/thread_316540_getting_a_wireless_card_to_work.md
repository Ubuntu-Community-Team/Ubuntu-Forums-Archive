---
title: "getting a wireless card to work"
date: 2006-12-10
forum: General Help
---

### Post by Polygon on 2006-12-10
i am thinking about maybe installing linux on my bros computer, but when i tried the live cd on his computer, when i entered the information for the network, it wouldent work, so i am assuming that the wireless card is not autodetected or something along those lines

any suggestions on making it work? i really dont want to get a new one as this one works fine in windows

the wireless card is a "netgear wg311v2"

thanks

---

### Post by goodfella on 2006-12-11
You can use this link with information as to whether or not your bros card will work with linux [http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

---

### Post by noerrorsfound on 2006-12-28
The solution is pretty simple in Ubuntu.
> **ugufugu said:**
> With Ubuntu 6.06 LTS this worked for me, cheers!

I tried this:

```
$ sudo gedit /etc/modprobe.d/options
```
insert the line
  ```
options acx firmware_ver=1.2.1.34
``` 
(and if you don't want to reboot):
```
$ sudo modprobe -r acx
$ sudo modprobe acx
$ iwlist wlan0 scan
```
and now a list of access point is shown :)
I didn't need to set 'wireless-keymode restricted' because my accesspoint is open, but I am still using WEP.
(This also works in 6.10, by the way.)

If only I could find a solution as simple as that for Debian. :)

---

