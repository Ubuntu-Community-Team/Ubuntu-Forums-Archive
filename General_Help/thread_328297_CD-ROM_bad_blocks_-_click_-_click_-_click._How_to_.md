---
title: "CD-ROM bad blocks - click - click - click. How to stop?"
date: 2006-12-30
forum: General Help
---

### Post by chrismyers on 2006-12-30
Hi there,

When my CD-ROM encounters a bad block whilst reading it gets into a bit of a loop trying to read. It ends up going click - click - click.

Does anyone know what command to use to force it to give up trying to read?

The only way I can stop it is by rebooting at the moment, which is not ideal.

Cheers in advance.

---

### Post by dcstar on 2006-12-30
> **chrismyers said:**
> Hi there,

When my CD-ROM encounters a bad block whilst reading it gets into a bit of a loop trying to read. It ends up going click - click - click.

Does anyone know what command to use to force it to give up trying to read?

The only way I can stop it is by rebooting at the moment, which is not ideal.

Cheers in advance.

It depends on what application you are actually using to access the CD-ROM, you can kill the process with System Monitor.

---

### Post by chrismyers on 2006-12-31
This was probably my mistake.

I used xkill to kill k9copy, but it may have just killed the k9copy app & left a process running.

Next time I'll try your suggestion or by using 'htop', which I've just discovered.

Cheers. :-D

---

