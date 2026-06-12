---
title: "SSH in KDE problems"
date: 2006-10-28
forum: General Help
---

### Post by krypto_wizard on 2006-10-28
I cant ssh into KDE box while I could do easily on gnome.

Please help.

---

### Post by KaroSHi on 2006-10-28
I am assuming you mean you have done a fresh install and cant get back in via ssh? if so, did you remember to apt-get install ssh, since ubuntu does not have ssh by default like some distro's.

---

### Post by fuzziefuz on 2006-10-29
If you want to access your linux box via ssh you will need the server package of ssh installed: openssh-server

Either use the package manager Synaptic or type > apt-get install openssh-server in the command line.

---

### Post by krypto_wizard on 2006-10-29
I mean I have ssh and openssh all installed fine and it works when i am in gnome.

Sometimes I switch to KDE. when KDE is on I can't ssh to my linux box.

Do l I need to modify some firewall settings or open some port or anything.

Please help.

---

