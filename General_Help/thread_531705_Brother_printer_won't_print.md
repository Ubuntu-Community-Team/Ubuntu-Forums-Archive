---
title: "Brother printer won't print"
date: 2007-08-21
forum: General Help
---

### Post by baklava on 2007-08-21
I have a brother MFC-3240C. I installed it using brother's CUPS driver. It shows up under systems>administration>printing in the gnome pane, and says it's ready, but it never prints. When I open its properties the status says:
```
Ready: /usr/lib/cups/filter/brlpdwrapperMFC3240C failed
```

And in the jobs, it says
```
State:
Stopped: job-stopped

```
But I can't resume it. 

Apologies in advance if I'm doing something rather newbish.

Help?

---

### Post by baklava on 2007-08-22
I tried installing the lpr driver again, but it keeps giving me this error...
```
dpkg: error processing /home/jorge/mfc.deb (--install):
 trying to overwrite `/usr/local/Brother/inf/setupPrintcapij', which is also in package mfc3420clpr

```

But when I use --force-overwrite it returns
```
dpkg: error processing --force-overwrite (--install):
 cannot access archive: No such file or directory
dpkg-deb: `/usr/local/Brother/inf/setupPrintcapij' is not a debian format archive

```

---

### Post by baklava on 2007-08-22
Help?

---

