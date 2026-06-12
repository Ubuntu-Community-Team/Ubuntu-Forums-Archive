---
title: "X Server error on startup"
date: 2008-01-07
forum: General Help
---

### Post by bizzu on 2008-01-07
Hi everyone! I'm a Kubuntu Gutsy user ;)
Since some days ago my distro can't load the X server on startup... executing "tail /var/log/Xorg.0.log" I found this error:
> 
Fatal server error:
xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)

But, if I execute startx after the login, the X server starts normally :confused:

What can I do? I didn't make any significant change in my distro lately...

---

### Post by dcstar on 2008-01-08
> **bizzu said:**
> Hi everyone! I'm a Kubuntu Gutsy user ;)
Since some days ago my distro can't load the X server on startup... executing "tail /var/log/Xorg.0.log" I found this error:

But, if I execute startx after the login, the X server starts normally :confused:

What can I do? I didn't make any significant change in my distro lately...

I can only suggest you go through the process for reconfiguring your X server to fix any changes in your hardware config:
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bizzu on 2008-01-09
I even tried starting X without xorg.conf, in order to let it autoconfigure itself, but the problem persists.
I suspect there's a problem with ati proprietary drivers; tonight I'll try to install the latest drivers...

---

