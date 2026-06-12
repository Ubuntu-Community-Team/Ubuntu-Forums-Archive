---
title: "SSH Remote Port Forward Troubles..."
date: 2007-05-09
forum: General Help
---

### Post by anaoum on 2007-05-09
I have two machines that are both running feisty on the same LAN. i want to set up a remote port forward as follows:

     andrew@machineA:~$ ssh root@machineB -R 2222:127.0.0.1:22

That supposedly works fine, without giving me any error messages. But, when I try to connect to the port 2222 on machineB, i get:

     andrew@machineA:~$ ssh machineB -p 2222
     ssh: connect to host machineB port 2222: Connection refused

I am 100% sure that machineB has no firewall whatsoever . Can anyone please tell me what I'm doing wrong?

---

### Post by fanatik on 2007-05-09
Ahh you're doing a remote forward, ie you would want to connect back to machine A from machine B. if you want to do a local forward, use the -L option instead of -R.

what are you actually trying to achieve?

---

