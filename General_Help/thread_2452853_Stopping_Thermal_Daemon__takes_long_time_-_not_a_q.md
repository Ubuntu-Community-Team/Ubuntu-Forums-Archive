---
title: "Stopping Thermal Daemon  takes long time - not a question"
date: 2020-10-29
forum: General Help
---

### Post by helen314 on 2020-10-29
After issuing "reboot" the process get "stuck"  "stopping thermal daemon"  . 
It seem like over a minute , there is no "stopping" counter as used in some other processes. 

This of not big issue, but like to know why it takes such  relatively long time. 

BTW - my motherboard is "fan less", perhaps that may be the reason. 

I have also observed one and an half minute "timer"  when starting and stopping disk manager.
Maybe nobody did not pay attention that modern mechanical disk do not have to be "parked"
nor solid state technology needs  same.

---

### Post by CatKiller on 2020-10-29
The default timeout for starting and stopping systemd services is 90 seconds. It seems a bit long to me, too. It's fairly straightforward to change it to something shorter - just changing a text file - although I can't remember exactly where off the top of my head. It's only when a service has stalled in some fashion that it's an issue; when things are working properly they only take as long as they take.

---

### Post by ajgreeny on 2020-10-29
The file that you can edit, though I have no idea how wise it is to do so, having only ever done it in a VM Xubuntu system running in VirtualBox, is ***/etc/systemd/user.conf***

Booting and shutdown in the VMs was regularly paused for 90 seconds with the notification (if using a text boot instead of quiet splash as is normal) ***a start-job is running*** or a ***stop-job is running*** then showing the jobname and a count of seconds.  Changing those 90s in the user.conf file to 10s and removing the # comment from the start of the lines worked and appeared to cause no problems but as I say, I do not know if it really is safe to do this.

You can check which files include the 90s content using command ***egrep 90s /etc/systemd/****.

---

### Post by helen314 on 2020-10-29
> **ajgreeny said:**
> The file that you can edit, though I have no idea how wise it is to do so, having only ever done it in a VM Xubuntu system running in VirtualBox, is ***/etc/systemd/user.conf***

Booting and shutdown in the VMs was regularly paused for 90 seconds with the notification (if using a text boot instead of quiet splash as is normal) ***a start-job is running*** or a ***stop-job is running*** then showing the jobname and a count of seconds.  Changing those 90s in the user.conf file to 10s and removing the # comment from the start of the lines worked and appeared to cause no problems but as I say, I do not know if it really is safe to do this.

You can check which files include the 90s content using command ***egrep 90s /etc/systemd/****.


```

f@f-SATA:~$ egrep 90s /etc/systemd/*
grep: /etc/systemd/network: Is a directory
grep: /etc/systemd/system: Is a directory
/etc/systemd/system.conf:#DefaultTimeoutStartSec=90s
/etc/systemd/system.conf:#DefaultTimeoutStopSec=90s
grep: /etc/systemd/user: Is a directory
/etc/systemd/user.conf:#DefaultTimeoutStartSec=90s
/etc/systemd/user.conf:#DefaultTimeoutStopSec=90s
f@f-SATA:~$ 


```


Thanks for reply.
When I feel adventurous and bored I'll try to change these timers.

---

