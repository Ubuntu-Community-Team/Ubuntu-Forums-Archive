---
title: "Sharing a folder from /media/ path safe?"
date: 2014-09-15
forum: General Help
---

### Post by Mk32 on 2014-09-15
Hi, 

I'm looking to create a persisent share directory, but I'm not sure what "path" is safe from unintended consequences and is persisent, meaning if I reboot or shutdown then it'll still be there. 

For instance, here I want to make a share directory accessible by anonymous/guest users (yes this is on a LAN, not WAN):

sudo mkdir /media/GuestF
sudo chmod 777 /media/GuestF

...and then share that directory from there. I don't want to share my home folder, because that's iffy. Should I create a folder in my /home/glaze/ directory, or perhaps someplace else? /media/?

---

### Post by mikewhatever on 2014-09-15
Safe from what/who? Are there any particular concerns?

---

### Post by ian-weisser on 2014-09-15
Any directory you create outside of /tmp will be persistent on a normal install. Only /tmp gets flushed at each reboot.

One normal place to put a real sharing service is in /var/<service_name> , but you can put it anywhere you like...except /tmp .

---

