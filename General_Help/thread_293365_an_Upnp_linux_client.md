---
title: "an Upnp linux client?"
date: 2006-11-05
forum: General Help
---

### Post by zeltak on 2006-11-05
hi guys!

im lookin for a way to play my music in linux through Upnp from my windows (yeah i know it sucks but i still dont have time to switch my HTPC to linux...:) ) to my Ubuntu desktop (i use kubuntu actually). does anyone know of such a client?

thx alot in advance

Zetlak

---

### Post by angkor on 2006-11-05
I don't know if this helps but this is what I found in the repos:

```
apt-cache search Upnp
gmediaserver - UPnP Mediaserver
libupnp-dev - Intel Universal Plug And Play SDK for Linux (development files)
libupnp0 - Intel Universal Plug And Play SDK for Linux (shared libraries)
linux-igd - Linux UPnP Internet Gateway Device
```

---

### Post by deeptingler on 2006-11-07
I use gmediaserver with my philips streamium sl300i and have done since dapper days.  not sure how many songs it handles though as this newly installed version (since I upgraded) seems to have the songs in the wrong order.  However, since this was only installed tonight and doing a virus scan at the same time, I still need to check this out incase its something I have done.  give it a try anway, heres how I use it.

gmediaserver --friendly-name=Linux --verbose=0 --port=49152 --profile=generic /storage/Sound

where /storage/sound is my music directory.

if you add a -b option it will run in the background.

Also, take note that it takes a while to scan your collection before listening on ports for your media device.

---

