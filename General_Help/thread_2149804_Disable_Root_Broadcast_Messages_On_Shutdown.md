---
title: "Disable Root Broadcast Messages On Shutdown"
date: 2013-05-30
forum: General Help
---

### Post by jyamut on 2013-05-30
Hello All,

Is there a way to prevent or disable root from displaying the shutdown message on the console? If there is no configuration settings for this, can this be modified from source? Which program is responsible for this annoying broadcast message and where do I pull the source?

This is a remnant of the past when users where all logged in terminals to one machine. Now, we're using it as desktops with a DE and most of the time, nobody connects to my machine remotely.  It's a personal computer not a server.

Thanks and Regards,
JY

---

### Post by jyamut on 2013-06-04
Is it deathly silent here or what?  Maybe not too many people on the ubuntu forums anymore. Did I put this on the wrong category? :O

---

### Post by Cheesemill on 2013-06-04
If you are using the shutdown command you can add the --no-wall switch...
```
sudo shutdown now -h --no-wall
```

If you're not using the shutdown command then you can edit the value of the kernel.printk variable in /etc/sysctl.conf to alter which messages get written to the console.

---

### Post by jyamut on 2013-07-31
Thanks much @Cheesmill ! Good info. I'll try to look into that.  :D

---

