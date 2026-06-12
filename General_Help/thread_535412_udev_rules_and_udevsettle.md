---
title: "udev rules and udevsettle"
date: 2007-08-26
forum: General Help
---

### Post by Austin_KW on 2007-08-26
I am trying to write a udev rule as follows
```

* cat /etc/udev/rules.d/10-local.rules*

KERNEL=="event*",ATTRS{product}=="SOHO-FX2",ACTION=="add",SYMLINK="input/irremote",**RUN+="/etc/init.d/lirc start"**
KERNEL=="event*",ATTRS{product}=="SOHO-FX2",ACTION=="remove",RUN+="/etc/init.d/lirc stop"


```

Should be simple enough; when I plug in my DVB card add a symlink and start the lirc server. 
The problem is that the RUN command is waiting for udevsettle to finish so it takes a few minutes to start the lirc server. After plugging in the device pstree reports 
```

...
     &#9500;&#9472;start_kdeinit
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-tools-ba&#9472;&#9472;&#9472;dbus-daemon
**     &#9492;&#9472;udevd&#9472;&#9472;&#9472;udevd&#9472;&#9472;&#9472;lirc&#9472;&#9472;&#9472;udevsettle**

```
When udevsettle exits, lirc starts.
What am I missing, how can I make the RUN+ command complete immediately

thanks /austin

---

