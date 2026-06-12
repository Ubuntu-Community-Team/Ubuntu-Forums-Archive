---
title: "Hibernation Problems"
date: 2015-09-08
forum: General Help
---

### Post by darkenvy6 on 2015-09-08
So I have been scouring the forums and google for way too long and have decided to post.

I cannot seem to get hibernation to work. pm-hibernate simply freezes and does nothing. I have checked my swap partition and it is larger than my RAM. 6.2GB while I only have 6GB of RAM (6144MB). I do not know if it is related but I also can't seem to shutdown my computer all the way either. It simply waits at "[sda] stopping disk". I would prefer to not fix that problem at the moment if I do not have to.

Oh I also want to mention, **cat /etc/initramfs-tools/conf.d/resume** returns**RESUME=UUID=6108cab9-3362-449f-8a2c-dd276a0304cd **which is the UUID of my swap partition.

Ideas?

---

### Post by Double.J on 2015-09-08
Hi there, 

you you can check swap is mounted okay with
```
swapon 
``` 

I also had a problem with swap and hibernation recently, in my case it was the swap itself. Maybe worth trying 
```
#swapoff 
#mkswap /dev/sdXY
#swapon /dev/sdxy
```

that does assign a new UUID so you may have to update fstab if you use UUID in fstab... Actually if you use 15.04 on a gpt disk, you don't strictly need to list your swap partition in the fstab because of systemd



JJ

---

### Post by darkenvy6 on 2015-09-08
I successfully disabled swap and created the swap again on the swap drive. However pm-hibernate still does not work. Is there a log for pm-hibernate? It is quiet silent on the terminal I launch it at and I would like to see the error log.

I heard that ubuntu 15.04 also doesn't like swap-to-file for hibernation. I remember reading that on the ubuntu website doc page. Is this true or is it just natively disabled?

---

### Post by darkenvy6 on 2015-09-11
It's been a while so... bump :P

Any logs to check? I'm not sure how to move forward with troubleshooting this.

---

