---
title: "Modprobe does only work from terminal"
date: 2017-02-02
forum: General Help
---

### Post by JanFlorijn on 2017-02-02
Hi all,

In previous releases of Ubuntu(14) I could add a line "modprobe snd-virmidi enable=1,1,1,1," to the file /etc/modules.

In Ubuntu 16 this does not work.

Creating a script file and executing it as root does not work.

Adding the script or the command to "session and startup" does not work.

The only way is opening a terminal and typing sudo modprobe snd-virmidi enable=1,1,1,1,1

How to solve this?

Kind regards,

Janflorijn

---

