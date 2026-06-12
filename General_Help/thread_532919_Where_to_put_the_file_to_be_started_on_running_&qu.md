---
title: "Where to put the file to be started on running &quot;startx&quot;"
date: 2007-08-23
forum: General Help
---

### Post by satimis on 2007-08-23
Hi folks,


Ubuntu 7.04 lamp server amd64


On switching the PC it boots to runlevel 3.  On running "startx" it start Fluxbox desktop


I have following file;
$ cat /etc/X11/Xsession.d/scim_startup ```

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

```

$ ls -l /etc/X11/Xsession.d/scim_startup ```

-rw-r--r-- 1 root root 113 2007-08-23 15:00 /etc/X11/Xsession.d/scim_startup

```

I need to start it simultaneously on running "startx"

I tried puting it on ~/.xinitrc```

exec    /usr/bin/startfluxbox
exec    scim_startup

```
It did not work because it is not an executable file.

Please advise the solution?  To make this file executable?   TIA


B.R.
satimis

---

### Post by gashcrumb on 2007-08-23
I think you want to source "scim_startup" and then run fluxbox.  So your.xinitrc would be like:

```

. /etc/X11/Xsession.d/scim_startup
exec    /usr/bin/startfluxbox

```

That way startfluxbox will get the environment variables that are being set in scim_startup.

---

### Post by satimis on 2007-08-23
> **gashcrumb said:**
> I think you want to source "scim_startup" and then run fluxbox.  So your.xinitrc would be like:

```

. /etc/X11/Xsession.d/scim_startup
exec    /usr/bin/startfluxbox

```

That way startfluxbox will get the environment variables that are being set in scim_startup.
Hi gashcrumb,


Your advice works for me.  Tks


satimis

---

