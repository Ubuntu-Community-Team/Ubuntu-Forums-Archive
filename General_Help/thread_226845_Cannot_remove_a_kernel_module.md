---
title: "Cannot remove a kernel module"
date: 2006-07-31
forum: General Help
---

### Post by jaymode on 2006-07-31
I am trying to stop a kernel module from loading at startup. It is the ivtv kernel module. I m using the latest kernel from the repos. I installed ivtv following Hyams guide:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

I already took the module out of /etc/modules and removed the alias also.

However by checking dmesg, it still loads at startup. When I try:
```

sudo modprobe -r ivtv

``` 

nothing happens, it just sits there like it is doing something but doesnt.

Any ideas? Let me know what other info you need and I can post it.

---

### Post by xXx 0wn3d xXx on 2006-07-31
Try 
> rmmod Mod_name
Then add it to the blacklist file under /etc/modprobe.d/blacklist

add "blacklist ivtv" to it. Then reboot.

---

### Post by jaymode on 2006-07-31
> **xXx 0wn3d xXx said:**
> Try 

Then add it to the blacklist file under /etc/modprobe.d/blacklist

add "blacklist ivtv" to it. Then reboot.

Thanks that worked.

---

