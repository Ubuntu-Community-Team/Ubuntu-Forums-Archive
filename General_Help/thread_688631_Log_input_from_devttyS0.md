---
title: "Log input from /dev/ttyS0"
date: 2008-02-05
forum: General Help
---

### Post by the_tazinator on 2008-02-05
I have a device that does not have a network interface on it but it does have a serial connection on it. What I want to do is connect this device to a Ubuntu server via the console port and collect all output from it, then I can ssh into the Ubuntu server and grab the log info. I can connect to the device using minicom and screen, so I know cabling and everything is good. I would like to have this start at system boot so all I have to do is power the machine on and walk away but at this point I am open to any help that you can provide.

---

### Post by cdenley on 2008-02-05
That sounds pretty simple. I don't have a serial port on my computer to test this, but you can try adding this line to /etc/rc.local
```

cat /dev/ttyS0>>/var/log/ttyS0.log&

```

---

### Post by the_tazinator on 2008-02-06
I tried your suggestion this morning when I got back to my machine and it works perfect. Thanks for the help!

---

