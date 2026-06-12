---
title: "Running audio software using VMware"
date: 2007-08-25
forum: General Help
---

### Post by Visti on 2007-08-25
Hi, I was reading up on VMware the other day and it seems interesting for some uses, but what about RAM-heavy operations such as audio production - Specifically, I would like to run something like Ableton Live through it, since dual-booting just for that can get tedious at times.

---

### Post by kidders on 2007-08-26
Hi there,

How successful vmware is depends on a few things, not least the quality of the software you want to run with it.

For best results, I would suggest running vmware on a multi-core CPU, with several GiB (4 or more?) of RAM, so that...[LIST]
[*]a heavily-loaded virtual environment doesn't cripple the rest of your system too badly, and
[*]to avoid forcing Linux to swap if at all possible, which would severely degrade the virtual environment's performance.[/LIST]

---

