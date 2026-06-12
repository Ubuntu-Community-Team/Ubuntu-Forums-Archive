---
title: "Cannot Boot into Ubuntu - Think I know why"
date: 2007-01-26
forum: General Help
---

### Post by jameslong on 2007-01-26
Hi All,
    I am very new to Ubuntu/Linux and I have stuffed it up already by playing around with stuff.

Anyway, the problem is that I can no longer boot into the Ubuntu GUI/Gnome. Only access I can get is Failsafe Terminal.

The reason I think I have stuffed thing up is bacuse I changed the user directory from '/usr/jim' to just '/'

Does anyone know how I can change this back to '/usr/jim' by using the terminal ?

Just had the Girl Friend saying how great Ubuntu is aswell and that she will not go back to Windows...

Any help would be great. 

Regards,

James

---

### Post by dcstar on 2007-01-26
> **jameslong said:**
> Hi All,
    I am very new to Ubuntu/Linux and I have stuffed it up already by playing around with stuff.

Anyway, the problem is that I can no longer boot into the Ubuntu GUI/Gnome. Only access I can get is Failsafe Terminal.

The reason I think I have stuffed thing up is bacuse I changed the user directory from '/usr/jim' to just '/'

Does anyone know how I can change this back to '/usr/jim' by using the terminal ?

Just had the Girl Friend saying how great Ubuntu is aswell and that she will not go back to Windows...

Any help would be great. 

Regards,

James

Boot off the Live CD, and fix your /etc/fstab file - hopefully you can recover your "/" partition, if not then you may have to re-install.

---

### Post by meng on 2007-01-26
How did you make this change: "/usr/jim" to "/" in the first place? I don't even understand what you did.

---

### Post by highneko on 2007-01-26
> **meng said:**
> How did you make this change: "/usr/jim" to "/" in the first place? I don't even understand what you did.

I don't understand either. 

jameslong: Did you maybe rename "/home/jim" to "/home//"? That's probably not possable tho. Did you rename the folder? Move the folder? Check your bash history. 

You could check your bash history with this command "less $HISTFILE".

---

### Post by Buck2348 on 2007-01-26
These are the two main lines from my /etc/fstab file, which controls mounting the file systems during boot.  The "hdb2" and "hdb4" mean "hard drive 2, partition 2, and hard drive 2, partition 4" so you will have to change that depending on where your Linux partitions are.
```
 /dev/hdb2   /               ext3    defaults,errors=remount-ro 0       1
 /dev/hdb4   /home           ext3    defaults        0       2
```

---

