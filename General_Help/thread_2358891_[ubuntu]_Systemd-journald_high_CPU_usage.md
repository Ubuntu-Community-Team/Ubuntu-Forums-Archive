---
title: "[ubuntu] Systemd-journald high CPU usage"
date: 2017-04-18
forum: General Help
---

### Post by spyros.d on 2017-04-18
Hello to everyone! It is my very first post here!! I am really happy to join Ubuntu Forums!

Now, let's cut to the chase:
A few days ago, I installed Ubuntu 17.04 on my Asus laptop (dual-boot with Windows 10) and after some days, I noticed that the "systemd-journald" process was constantly using 25-35% of CPU.
Following advice I found on the Internet, I straced the process and saved part of the output in the text file I am attaching.
As anyone can notice, it seems that the CPU is looping, doing something that is related to a device (PCI?).

Does anyone have any advice on the problem?
(If additional information is needed, I will be glad to supply it)

Thank you all in advance.

---

