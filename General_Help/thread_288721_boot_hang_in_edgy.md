---
title: "boot hang in edgy"
date: 2006-10-30
forum: General Help
---

### Post by kentonspr on 2006-10-30
I am having really slow boot times in edgy on my laptop. I am pretty surprised how long it takes as the computer is fairly new and Dapper seemed to be a lot faster. I installed bootchart and have attached the chart to this post. I am pretty much a newb so I'm not super sure what all I should be looking for on the chart or how to even fix it once I find it...

Any help would be very appreciated. Thanks.

---

### Post by kaveraj on 2006-11-03
Experienced the same problem. Even complete hangups during boot. Googling led to a bug in launchpad and disabled the wifi in bios and hardware switch as described in the thread. Now no probs. Boots ok.

u could enable wifi after booting thru the hardware switch.

Seems like some problem with the latest kernel and wifi. Just works now .. after days of frustration.[-(

---

### Post by kentonspr on 2006-11-03
Thanks. 

You wouldn't happen to have a link to the thread you found or the google search string you used would you?

---

### Post by kentonspr on 2006-11-03
Actually, it looks like I just fixed it by commenting out all the stuff in /etc/network/interfaces that I didn't need.

I also changed fstab so that it wasn't running fsck for every partition on boot. Much much faster now.

---

### Post by mirak63 on 2006-11-03
how do you generate that graphic image ?

---

### Post by kentonspr on 2006-11-03
You have to install bootchart. Then when you boot, it creates the image and puts it into /var/logs/bootchart/. I could be wrong about part of that path, but I am pretty sure it is right.

---

