---
title: "Kubuntu uses up 2gb of memory?"
date: 2008-05-26
forum: General Help
---

### Post by LinuxLovesMJ on 2008-05-26
I'm currently running Kubuntu 8.04 with 4gb of ram, but since I'm not using the 64 bit version, I can only use 2.7gb of my 4gb installed ram. I have provided a screen shot of the problem: kubuntu monitor says that my computer is using up over 2gb of my memory, but I barely have any programs running, only pidgin and firefox. How is this possible? I've tested this out for many days and it keeps using over 2gb of memory, I'm confused? It also shows random high load averages and massive cpu usage, what could be causing this? (screen shot included below)

[IMG]http://i26.tinypic.com/sc3r47.png[/IMG]

---

### Post by latna on 2008-05-26
Are you having performance issues, or are you just concerned with the amount of memory being used? If it's the latter, linux uses a lot of memory as cache. The memory is free if a program needs it, but if you close firefox for instance, linux keeps it in memory in case you start it up again.

Here's a long thread on the subject. There are more out there I'm sure.
[http://ubuntuforums.org/showthread.php?t=794854&highlight=memory]("http://ubuntuforums.org/showthread.php?t=794854&highlight=memory")

---

