---
title: "Hardy Heron (8.04) upgrade, temperature shutdown problem"
date: 2008-05-29
forum: General Help
---

### Post by kafkaian on 2008-05-29
Hi,

I keep periodically getting an automatic shutdown after upgrading to Hardy Heron with a "critical temperature" warning.

Here's what my log says just before shutdown:

> May 27 20:55:56 ubuntu kernel: [  671.215459] ACPI: Critical trip point
May 27 20:55:56 ubuntu kernel: [  671.219373] ACPI: Unable to turn cooling device [f7c4c420] 'on'
May 27 20:56:03 ubuntu kernel: [  677.950407] ip6_tables: (C) 2000-2006 Netfilter Core Team
May 27 20:56:05 ubuntu exiting on signal 15

Didn't happen before the upgrade from Feisty, but I'll check for any physical hardware problems just in case 

Can anyone please point me to the right bug discussion or workaround because I don't seem to be searching and getting the right answers?

Thanks in advance

Ian

---

### Post by kafkaian on 2008-05-29
Hmm, can find old bug reports, but no new ones

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/54855](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/54855)

as in > boot option pci=noacpi

---

### Post by kafkaian on 2008-05-29
Just wondering if I had this [pci=noacpi ] in my original menu.1st.

Is this backed up on upgrade does anyone know?

---

### Post by kafkaian on 2008-05-29
[This laptop]("http://ge.ubuntuforums.com/showthread.php?t=539365&page=6") thread doesn't seem to apply to me either.

---

### Post by kafkaian on 2008-05-29
Took a look at the /proc/acpi/ directories and nothing listed against files currently installed, so I'm a little confused as to what parameters should be set in there - especially /thermalzone/

---

### Post by kafkaian on 2008-05-29
RIGHT! Had enough now. My system's gone AWOL twice in as many hours not leaving me the time to work on it before the critical temp warning kicks in and forces another uninformed reboot.

Time to file a bug report and hope to get an answer

---

