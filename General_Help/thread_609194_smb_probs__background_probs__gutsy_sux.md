---
title: "smb probs / background probs / gutsy sux"
date: 2007-11-10
forum: General Help
---

### Post by dubstar on 2007-11-10
gone from fesity to gutsy.

on this computer the problems are:

background disappears on reboot - have to re-apply from appearance

viewing network locally mounted folder, times out or takes ages with no activity - ?

suspend doesnt work, is unable to unload the nvidia module - ?

any solutions?

have also done this: [http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

which seems to have made it worse.

pc spec is 3.0ghz p4
2gb 3200
couple of hds
networked to raid 1 nas which hosts all my files

---

### Post by dubstar on 2007-11-11
up

---

### Post by skymera on 2007-11-11
sorry about your troubles with gutsy.

ive had problems too, feisty was great.
gutsy can do one as far as im concerned.

im gonna check that link,

maybe gnome-settings-daemon isnt starting right :(

check the logs for anything :)

hopesome one else can help you

---

### Post by dubstar on 2007-11-12
> **skymera said:**
> sorry about your troubles with gutsy.

ive had problems too, feisty was great.
gutsy can do one as far as im concerned.

im gonna check that link,

maybe gnome-settings-daemon isnt starting right :(

check the logs for anything :)

hopesome one else can help you


which logs? (still learning..... getting there but still learning!! lol!)

---

### Post by dubstar on 2007-11-14
?

---

### Post by skymera on 2007-11-14
system logs, just browse through, shouldnt take long

sorry for not replying

look for 

something around  gnome-settings-daemon

---

### Post by dubstar on 2007-11-15
right seems samba was arsing about, reinstalled, still bad, get this error in syslog, messages, and kern.log:

Nov 15 19:33:55 twisted kernel: [  715.527741] smb_add_request: request [f6c9de00, mid=27285] timed out!

well, lots of them to be exact!


 any ideas?

still doesnt explain why my background and desktop icons disappear..............????????????????????????

---

### Post by dubstar on 2007-11-17
???

---

### Post by skymera on 2007-11-17
i dont know,
i know as much as you

---

