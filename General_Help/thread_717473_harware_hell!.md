---
title: "harware hell!"
date: 2008-03-07
forum: General Help
---

### Post by robfromsactown on 2008-03-07
i just installed Kubuntu 7.10 and am having some massive hardware issues. I have the _nvidia 8800gt_ video card and _lniksys WUSB54GSC_ usb wireless adapter. Neither are supported by ubuntu. i tried to install the binary driver (for the video card) in recover mode but cant install it without an internet connection since the driver either needs to access the internet  to download the precompiled kernel interface. Also since a c compiler doesn't appear to be a standard part of the kubuntu and i can't directly access the internet to get the package, the driver cant compile on the computer and run. any help would be great!

ps I also use windows and can download the necessary--which i can burn to a cd

---

### Post by zvacet on 2008-03-07
Put Cd in drive and type in terminal

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

Or you can use [nonetdebs](http://nonetdebs.homeip.net/) to download needed packages from comp with internet.Put downloaded packages on CD/stick and install it on your comp.

---

