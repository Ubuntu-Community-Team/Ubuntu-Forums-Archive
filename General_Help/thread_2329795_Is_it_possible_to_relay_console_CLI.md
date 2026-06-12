---
title: "Is it possible to relay console CLI?"
date: 2016-07-05
forum: General Help
---

### Post by Pandee on 2016-07-05
Hello!

So for example i have a game server running and its input/output is through CLI.

Is there a way to stream the happening of the CLI window to users outside the network? And if it is possible have permissions to allow certain users to send through commands/text (Such as ctrl+c )

Thanks.

---

### Post by sudodus on 2016-07-05
You can connect to a server via the network (locally or globally) via for example ***ssh***. If you want to connect outside the LAN (and pass the firewall) you need to be very careful to avoid opening the system to attacks.

Maybe you can start by reading the sticky threads at the [security forum](http://ubuntuforums.org/forumdisplay.php?f=338) and the [server forum](http://ubuntuforums.org/forumdisplay.php?f=339) (at our Ubuntu Forums) and this link about openssh:

[SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by Pandee on 2016-07-05
I am aware of SSH (I use it with putty/VNC and FTP), I just want other users to be able to see a CLI console thats running. Kinda of like a RCON or relay of some form.

---

