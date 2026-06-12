---
title: "What is the multiload-apple process?"
date: 2006-11-11
forum: General Help
---

### Post by SuperMike on 2006-11-11
Anyone know what the multiload-apple process is? I see it when I do a 'top' on my Ubuntu.

The 'whereis' command doesn't find it.

It's not in /etc/init.d.

Virus?

---

### Post by SuperMike on 2006-11-11
Oh Duh. Embarassing. I did 'pstree -pah | more' and paged down to find that it stands for "multiload-applet" and is part of the stuff that keeps GNOME desktop running smoothly.

It's **not** a virus.

---

### Post by glennzo on 2007-01-21
Well I'll be. I've never seen it before and it roused my curiosity. Matter of fact, why does it show up now? Been running Gnome for several years and have NEVER seen it.

---

### Post by wargod on 2007-02-15
Hi there,
it's as simple as it looks.

kill this process and you will see it's  that application in the Panel
that holds information about the CPU/STACK/NET/... 

I think it's called  "system-monitor".

---

