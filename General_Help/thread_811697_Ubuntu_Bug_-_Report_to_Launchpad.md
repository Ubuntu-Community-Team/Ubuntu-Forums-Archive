---
title: "Ubuntu Bug - Report to Launchpad?"
date: 2008-05-29
forum: General Help
---

### Post by kafkaian on 2008-05-29
I'd like to report a bug through launchpad but don't know what package it would refer to inc dependencies.

Basically, I'm getting the following sudden reboot

> May 27 20:55:56 ubuntu kernel: [ 671.215459] ACPI: Critical trip point
May 27 20:55:56 ubuntu kernel: [ 671.219373] ACPI: Unable to turn cooling device [f7c4c420] 'on'
May 27 20:56:03 ubuntu kernel: [ 677.950407] ip6_tables: (C) 2000-2006 Netfilter Core Team
May 27 20:56:05 ubuntu exiting on signal 15 

---

### Post by latna on 2008-05-30
Are you sure it's a bug in the kernel? It looks to me like your cpu fan isn't working properly.

---

