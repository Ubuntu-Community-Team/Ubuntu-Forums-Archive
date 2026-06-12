---
title: "Wubi stuck on installation - GUI problem?"
date: 2008-05-11
forum: General Help
---

### Post by Fireflock on 2008-05-11
I loaded Wubi on Vista, downloaded and restarted. Everything loads fine until I hit "Checking the installation..." prompt. The window is scrambled and I can't interact with it. The background picture shows up just fine and I can move the mouse around but I can't interact with the window. It scrambles differently every time I load it. I would like to run Ubuntu along Vista if I could get past this problem.

---

### Post by Fireflock on 2008-05-13
Any ideas on how to fix this? I tried downloading Kubuntu-KDE4 but I got a similar although not exact problem. Could it be incompatible hardware? I am trying to run it on:
[LIST]
[*]AMD Athlon 64 X2 4200+
[*]GeForce 7800 GT
[*]2GB Memory
[*]SATA 150GB
[/LIST]
I am running Windows Vista with SP1 if that matters. If you need anything more specific I can help.

---

### Post by ago on 2008-05-14
I would need access to the logs.

You can press ctrl+alt+f2 then run:

sudo sh /custom-installation/hooks/failure-command.sh

That will produce the logs in c:\ubuntu\installation-logs.zip

Post them here.

---

