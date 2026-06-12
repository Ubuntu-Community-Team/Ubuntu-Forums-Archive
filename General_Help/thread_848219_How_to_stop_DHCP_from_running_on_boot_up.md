---
title: "How to stop DHCP from running on boot up"
date: 2008-07-03
forum: General Help
---

### Post by NKane on 2008-07-03
I'm running Ubuntu 8.04 32bit Server edition and I want to disable DHCP on startup. What do I need to do besides manually calling /etc/init.d/dhcp3-server stop each time the system restarts.

Thanks.

---

### Post by justleen on 2008-07-03
in the GUI, you should be able to go to System > Admin > Services
Uncheck DHCP there.

in a terminal, its easiest to have rcconfig or sysv-rc-config installed..

there is no easy way, like chkconfig on a red hat, to do this.. AFAIK..

---

### Post by atomkarinca on 2008-07-03
Or you can install boot-up manager and disable whatever you don't use. Open up a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get install bum
```

and run bum from terminal.

---

### Post by Iowan on 2008-07-03
Probably better ways - but you can edit the appropriate rc?.d directory.  My **/etc/rc3.d** has a link named **S40dhcp3-server**.  If I rename it to  **xS40dhcp3-server** or even **s40dhcp3-server**, DHCP *shouldn't* start.  The corresponding **K40dhcp3-server** will leave nastygrams when shutting down.

---

### Post by NKane on 2008-07-03
Thanks for the suggestions.

I installed bum, but I should mention that this server is headless, so I would need a command line/terminal solution.

Any other ideas?

Thanks for the replies.

---

### Post by gabak on 2010-07-20
write this and it will stop ur dhcp
ifdown eth0

---

### Post by Iowan on 2010-07-20
Threads that are over a year old are generally considered closed.

---

