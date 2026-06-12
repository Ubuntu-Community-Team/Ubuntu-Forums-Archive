---
title: "Need help with VNC viewer install."
date: 2016-12-25
forum: General Help
---

### Post by przhevalskoye on 2016-12-25
hey all, I'm running Ubuntu MATE on my Lenovo Ideapad, and i need to install vEMan for school,
but when im trying to install VNC viewer, i cant figure it out. this is the output when i type ```
./vEMan
```

```
mrlinux@Linux-Ideapad:~/Desktop/vEMan_v0.9.6$ ./vEMan
DEBUG: User variable file /home/mrlinux/Desktop/vEMan_v0.9.6/etc/uservars_vEMan.cfg found.
DEBUG: User variable file /home/mrlinux/Desktop/vEMan_v0.9.6/etc/uservars_vEMan.cfg included successfully.
DEBUG: System variable file /home/mrlinux/Desktop/vEMan_v0.9.6/etc/sysvars_vEMan.cfg included successfully.
DEBUG: included >F_MKCFG< successfully
DEBUG: included >F_PARENTF< successfully
DEBUG: included >F_HELP< successfully
DEBUG: included >F_VERSION< successfully
DEBUG: included >F_LICENSE< successfully
DEBUG: included >F_INSTALLER< successfully
DEBUG: included >F_ERR< successfully
DEBUG: included >F_REVIEWER< successfully
DEBUG: Requirement /home/mrlinux/Desktop/vEMan_v0.9.6/vEMan met.
DEBUG: Requirement /usr/bin/yad met.
DEBUG: Requirement /home/mrlinux/Desktop/vEMan_v0.9.6/vmapps/general/connect.pl met.
DEBUG: Requirement /home/mrlinux/Desktop/vEMan_v0.9.6/libs/getx509certificate.vEMan met.
DEBUG: Requirement /usr/bin/ovftool met.
DEBUG: Error requirement /usr/bin/vncviewer is not available or executable!
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
DEBUG: informed keepalive handler about the exit
DEBUG: reached exit function
DEBUG: Cleanup end


```

Please help?

---

### Post by steeldriver on 2016-12-25
AFAIK there's not a single 'vncviewer' package, since there are several available implementations (there may have been a virtual package at one time?)

/usr/bin/vncviewer should be provided by **either **gvncviewer or xtightvncviewer, so you will probably need to choose and install one of those

---

### Post by przhevalskoye on 2016-12-25
i installed xtightvncviewer, but still, /usr/bin/vncviewer does not exist..

---

### Post by steeldriver on 2016-12-25
Ooops my bad - it looks like they install themselves as /usr/bin/xtightvncviewer and /usr/bin/gvncviewer

It may just be a matter of symlinking - but let's see if someone else has a better suggestion

---

### Post by przhevalskoye on 2016-12-25
I went and looked in /usr/bin/ but there was no xtightvcnviewer nor gvcnviewer

---

### Post by steeldriver on 2016-12-25
Well as far as I can tell, installing the xtightvncviewer package on regular Ubuntu does provide /usr/bin/xtightvncviewer binary and in fact provides the /usr/bin/vncviewer link automatically as well (via the update-alternatives mechanism)

Perhaps Ubuntu Mate does things differently? if so, I'm sorry - I can't help

---

