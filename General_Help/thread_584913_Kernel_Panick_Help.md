---
title: "Kernel Panick Help"
date: 2007-10-21
forum: General Help
---

### Post by _simon_ on 2007-10-21
My partners Ubuntu 7.10 32bit has started panicking (numlock and scrolllock lights flash) since an update she did this morning. She thinks it was something to do with time zones.

This happens within about 20 seconds of booting into a GUI.

What do I do?

---

### Post by weijie90 on 2007-10-21
> **_simon_ said:**
> My partners Ubuntu 7.10 32bit has started panicking (numlock and scrolllock lights flash) since an update she did this morning. She thinks it was something to do with time zones.

This happens within about 20 seconds of booting into a GUI.

What do I do?

Try digging out the syslogs from recovery mode.

---

### Post by _simon_ on 2007-10-21
This is showing in the log before every halt

Oct 21 14:31:49 SIMPLICITY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 21 14:31:49 SIMPLICITY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Oct 21 14:31:49 SIMPLICITY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 21 14:31:49 SIMPLICITY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 21 14:33:10 SIMPLICITY exiting on signal 15

It only started happening after she clicked on an advert link in an e-mail via Thunderbird.

---

### Post by _simon_ on 2007-10-21
Would a fresh install resolve whatever the problem is?

---

### Post by _simon_ on 2007-10-21
Not 100% sure yet as It's only been running 15 mins but it looks like the overclocked Athlon CPU in it finally gave up the ghost. 

It started refusing to POST, swapped the PSU, still the same, swapped the CPU and it seems to be working now.

EDIT: It was the CPU.

---

