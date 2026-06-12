---
title: "BUM does not ask for password"
date: 2005-07-20
forum: General Help
---

### Post by fedetxf on 2005-07-20
I installed BUM and I can use it, but it never asks for my password. Is it doing admin tasks like removing services from startup without root permission?
I wanted to remove these services rsync, firebird2, firestarter, acpi-support, powernowd, fetchmail, ppp and apmd,
AFAIK they don't start when I boot (some I don't need and some others I start when I need them) but how can I know BUM really did the task if it never asked for the password and I ran it as regular user?

---

### Post by amohanty on 2005-07-20
Thats strange, if I try to launch it from the terminal, it complains that it must be run with root provileges. In the System menu its in the Adminstration section and requires me to enter the password to fire it up.

ALl I can think of is that you can try reinstalling it via synaptic

AM

---

### Post by tread on 2005-07-20
Did you do a sudo access in the 15 minutes prior to using bum? Thats remembered for, like I said, 15 minutes.

---

### Post by fedetxf on 2005-07-21
[QUOTE=tread]Did you do a sudo access in the 15 minutes prior to using bum? Thats remembered for, like I said, 15 minutes.[/QUOTE]

That's it. That is the reason. Some prior task required me to enter the password. Now after a while BUM asks for it.

---

