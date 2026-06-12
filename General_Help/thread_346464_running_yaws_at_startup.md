---
title: "running yaws at startup"
date: 2007-01-25
forum: General Help
---

### Post by MrOdwin on 2007-01-25
I am running yaws-1.63 on an ubuntu 6.10 machine and am trying to have it start the server on boot. I placed the script in my /etc/init.d directory, set it to be exacutable, and lincked it with the command "update-rc.d -f yawsStart start 99 2 3 ." My script starts the server when i run it from the shell but it does not start it when I reboot the computer. Does anyone know the problem here?

This is my yawsStart script

#!/bin/bash
/opt/yaws/bin/yaws -D

---

