---
title: "Problems burning cd from SMB share with Brasero"
date: 2008-06-10
forum: General Help
---

### Post by megsona on 2008-06-10
Morning,

I've got a laptop running hardy and a QNAP NAS where I keep all my movies and mp3's etc. When I try and burn any kind of disk (audio, data, etc) from the share I get,

The "*filename*" is unreadable: access denied.

I have full RW access to the share, I logged into to the share using the admin password on my NAS. Checking the Brasero page also explicitly mentions that it supports burning files over SMB.

Is this a bug or am I missing something?

Cheers.

---

### Post by megsona on 2008-06-11
Solved, it was me missing something.

Used the correct mount command to a local folder rather than the Nautlius Go > Network option.

mount -t cifs -o username=netuser,password=hiddenword //server/origin /home/username/destination

All working well with Brasero now.

---

