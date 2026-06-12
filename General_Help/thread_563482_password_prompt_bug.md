---
title: "password prompt bug"
date: 2007-09-30
forum: General Help
---

### Post by squidy37 on 2007-09-30
on a fresh boot up, there's always the first time it asks you for the password for su access (such as the first time update manager is used after a reboot).

whatever prog that is trying to get access always freezes and i have force quit and try a second time to actually get that password prompt. does anyone know of this bug? maybe it has to do with the thinkfinger i have installed for my fingerprint reader. but that is just a guess.. can anyone help me with this?

---

### Post by jldugger on 2007-10-09
This is a known bug in gksudo.  If you swipe your finger at the point you were expecting a prompt I think it works.  But there's also a small patch to fix this.  I'm working on a package for Gutsy that fixes this, and I'm working on more patches that solve more.

Ultimately, I think gksudo needs work to integrate better with PAM.  In the meantime, I'm simply patching thinkfinger to work the way gksudo (stupidly) thinks.

---

