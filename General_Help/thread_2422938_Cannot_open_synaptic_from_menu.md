---
title: "Cannot open synaptic from menu"
date: 2019-07-15
forum: General Help
---

### Post by rdh61 on 2019-07-15
Lubuntu 18.04 recently upgraded from 16.04.

I cannot open Synaptic from the menu. (I can from the command line with 'sudo synaptic'.) I notice that the command in the menu entry is 'synaptic-pkexec'. If I run this in a terminal I get:


```
robert@robert-Lenovo-B590:~$ synaptic-pkexec
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: Robert,,, (robert)
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized


This incident has been reported.
robert@robert-Lenovo-B590:~$ 

```

Of course I can get around this by editing the menu entry. But I am wondering why pkexec is not working...?

(And as an aside, why was gksudo retired given that pkexec seems to be giving the whole world a headache?!!)

Thank you.

---

### Post by rdh61 on 2019-07-22
Nobody know anything about this?

---

### Post by #&amp;thj^% on 2019-07-22
Show us this please;
```
apt policy lxpolkit 
```
if not installed then Install it and try from the menu again.

---

### Post by rdh61 on 2019-07-30
@1fallen, Thanks for your response which I was not aware of till now (I didn't receive the expected email notification). In the meantime I found the solution you have suggested on another forum. After installation of lxpolkit Synaptic will open with the command synaptic-pcexec and via the menu. Given that pcexec is included in the Lubuntu installation, shouldn't lxpolkit be included too?

P.S. Note to myself and others that reboot is necessary before it will work.

---

