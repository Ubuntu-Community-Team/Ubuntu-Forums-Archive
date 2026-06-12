---
title: "My hard drive spins down really fast after Feisty upgrade"
date: 2007-06-10
forum: General Help
---

### Post by H.E. Pennypacker on 2007-06-10
When shutting down, my hard drive spins down really fast, instead of gradually coming down to a halt since I upgraded to Feisty.

I am not suggesting that Feisty is causing this.  I am saying that this can't be good (tells me something is seriously wrong).

I have googled the problem, and I couldn't find anything.

What could be going on?  How would I solve this problem?

---

### Post by H.E. Pennypacker on 2007-06-11
This problem may not be caused by Feisty at all.  Any ideas?

---

### Post by cookies on 2007-06-11
I think it's a known bug with some hardware, and there seems to a be script:

> **Unicast said:**
> Fan-bloody-tastic, found it and you know what, it works as well! 8)

Bug report here: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

With the salient information here:


What I did, for the less technically minded:

```
gksudo nautilus
``` - opens nautilus in gnome** environment with root privileges - so be careful kids! ;)

**or for KDE enviro```
kdesu konqueror
``` or for Xubuntu.```
gksudo thunar
```

Navigate to /etc/rc0.d

Right-click - Create new document - right click on new doc and rename to **S00hdd-shutdown-workaround**

Right-click on the renamed doc and select "open with text editor."

Copy and paste the following into the empty file and save.
```
#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
```

In terminal change to the etc/rc0.d directory and make the new file executable:

```
sudo chmod +x S00hdd-shutdown-workaround
```

and you're done. :D

Next time you shutdown there will be no nasty clunk / whirr.

---

### Post by H.E. Pennypacker on 2007-06-12
cookies, thanks a lot.  It, surprisingly, has solved my problem.  I did searches on hard drive spinning down, but nothing about noise.

---

### Post by tombott on 2007-08-01
Cheers for this, applied and works a treat!

---

