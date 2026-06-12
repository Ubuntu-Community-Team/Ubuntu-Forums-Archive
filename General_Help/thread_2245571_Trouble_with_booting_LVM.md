---
title: "Trouble with booting LVM"
date: 2014-09-24
forum: General Help
---

### Post by gregor9 on 2014-09-24
I have a VPS server which I upgraded from 12.04 to 14.01 recently. Today I rebooted server and it doesn't boot any more. Here is screen shot where it fails. Any help appreciated because I'm stuck with non working server and I need it up and running ASAP.

---

### Post by gregor9 on 2014-09-24
I suspect that unattended installation of packet dbus or libdbus-1-3 corrupted my installation. How to fix this?

---

### Post by gregor9 on 2014-09-24
These packages were installed

---

### Post by gregor9 on 2014-09-24
apt history log

---

### Post by gregor9 on 2014-09-24
Here are relevant log files.

---

### Post by nerdtron on 2014-09-25
> I have a VPS server which I upgraded from 12.04 to 14.01 recently

I say this is a formula for a disaster. Especially on mission critical servers as you won't know the result of it. Is this even recommended by the Ubuntu website? Even Red Hat systems recommend to do a reinstall when you jump to a major version.

But it seems you error is on LVM and I hope an expert on LVM passes here to guide you.

---

