---
title: "LTSP login becomes black screen"
date: 2008-04-16
forum: General Help
---

### Post by ivomans on 2008-04-16
I've got a Gutsy Ubuntu installation with a couple of LTSP clients. It has been running for months without a problem.

Starting today the login on the LTSP clients results in a proper validation of the password (checked auth.log on server). After that the screen turns black and the regular arrow mouse cursor appears. Mouse can be moved. But the screen remains black.
I checked the log files on the client and the last line in ldm.log says:
  ```
Executing rc files.
```Nothing that looks like an error at all.

Hope somebody can help me ASAP.

---

### Post by ivomans on 2008-04-16
Seems like I just solved this issue. Turned out the winbind setting in nsswitch.conf for passwd and group caused the problem. 
Somehow the connection with our Win-SBS server was down. Never expected LTSP to be sensitive for this authentication. Just removing the 'winbind' from nsswitch.conf solved it.

---

### Post by joehill on 2008-05-08
Same problem here but I don't have winbind in nsswitch.conf.  /var/log/auth.log shows my password was accepted, but I was booted out after several seconds of black screen.  I can log into a failsafe xterm but not gnome.

---

