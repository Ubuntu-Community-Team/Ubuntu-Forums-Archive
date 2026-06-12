---
title: "Can not Log into Ubuntu - xsession error"
date: 2008-04-16
forum: General Help
---

### Post by BLo on 2008-04-16
I have been trying to setup my laptop the last couple of days so that I can finally remove my windows partition. Problem is now I've done something bad and I cant log in at all as the session doesn't load properly. The only thing i remember installing the last time I logged into Ubuntu was the ICA citrix client and VMware. I think something might of gone wrong when installing VMware but I wasn't  paying much attention.

I've had a look around but not exactly sure why this would of happened. I'd be much appreciative if anyone can shed some light on this.




**The ~/.xsession-error file has this in it:**

---------------------------------------
process : 6189 : GtK+ WARNING ** This process is currently running setuid or setgid
This is not a supported use of GtK+. You must create a helper program instead. For further details, see

[https://www.gtk.org/setuid.html](https://www.gtk.org/setuid.html)

Refusing to initialise GtK+

Process : 6193 : GtK+ WARNING ** This process is currently running setuid or setgid
This is not a supported use of GtK+. You must create a helper program instead. For further details, see

[https://www.gtk.org/setuid.html](https://www.gtk.org/setuid.html)

Refusing to initialise GtK+

/etc/gdm/xsession : Beginning session setup...
/etc/x11/Xsession.d/40guidance-displayconfig_restore : 11 : /usr/bin/displayconfig_restore : not found
mkdtemp : private socket dir : permission denied

------------------------------------

Thanks in advanced

---

### Post by BLo on 2008-04-17
I looked around a bit harder and found a solution. By changing the permissions to /tmp to 777 it fixed the problem and allowed me to log back in without any errors.

Not sure why this happened all of a sudden and if it is 'safe' to give that level of access to tmp, anyone know if this is good practice?

---

