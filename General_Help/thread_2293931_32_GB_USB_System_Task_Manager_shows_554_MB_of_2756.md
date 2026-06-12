---
title: "32 GB USB System Task Manager shows 554 MB of 2756 MB Used"
date: 2015-09-08
forum: General Help
---

### Post by Boyntonstu on 2015-09-08
I expected to see the 32 GM total space,

The PC is running on the stick.

How to see the 32 GB USB stick?

---

### Post by Dennis N on 2015-09-08
The 554 MB is RAM memory used (memory installed on the motherboard).
The 32 GB measures non-volatile memory on the USB drive.

**df -h** run in the terminal will reveal usage of the latter for each mounted filesystem on the computer.

---

### Post by Boyntonstu on 2015-09-08
Wow!  You are SO smart. Thanks. My PC has 3 GB of RAM with  2.756 Available.

Is there a non-terminal program like Win7 File Explorer to see the drives?

Also, I did not partition the 32 GB USB OS nor did I create a swap.  Advice please.

Lubuntu and you are keeping my 76.5 year old brain from getting Alzheimers.

Edit:  df-h is not working.

Edit again:  df is working

---

### Post by Dennis N on 2015-09-08
> Edit: df-h is not working
there should be a space between df and the rest:

```
df -h
```

Now it will work.

---

### Post by Boyntonstu on 2015-09-08
Y e p  !!  It worked  fine.

Thanks again.

---

### Post by Dennis N on 2015-09-08
Just thought of this:

Gnome System Monitor shows the mounted file systems and usage in one of it's tabs. Lubuntu task manager doesn't have that option, so you might want to install gnome-system-monitor. I always do in Lubuntu (you are using Lubuntu?).  The resources tab would show the RAM in use, as well as download speed and CPU usage. The attached screenshot shows the mounted file systems in Gnome system monitor.

---

### Post by ventrical on 2015-09-08
You can use 'disks' program. What flavour are you using?

---

### Post by Boyntonstu on 2015-09-08
> **ventrical said:**
> You can use 'disks' program. What flavour are you using?

YES! 'Disks' shows it in 14.04.

Question answered.

Many thanks.

BTW Is there a part of the forum where forum members can show off their hobbies or inventions?

---

