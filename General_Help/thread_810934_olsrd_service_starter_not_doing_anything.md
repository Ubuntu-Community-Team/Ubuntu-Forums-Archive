---
title: "olsrd service starter not doing anything"
date: 2008-05-28
forum: General Help
---

### Post by Wej on 2008-05-28
In the /etc/init.d folder after installing olsrd (apt-get install olsrd), there is a script to run the service. When I try running sudo /etc/init.d/olsrd start, nothing happens. The service never starts and does not add or remove routes. If I run the same command but with restart as the argument, sudo /etc/init.d/olsrd restart, even if it is not currently running, it starts and works correctly. I don't understand the daemon starting function of Ubuntu, but I know if I run sudo olsrd -d 0 it will run as a daemon in the background, as I already do this on our OpenBSD machines. What is the easiest way to get olsrd to run at startup? Is there something wrong with the default script that must be adjusted?

Thanks

---

### Post by Wej on 2008-05-28
> **Wej said:**
> In the /etc/init.d folder after installing olsrd (apt-get install olsrd), there is a script to run the service. When I try running sudo /etc/init.d/olsrd start, nothing happens. The service never starts and does not add or remove routes. If I run the same command but with restart as the argument, sudo /etc/init.d/olsrd restart, even if it is not currently running, it starts and works correctly. I don't understand the daemon starting function of Ubuntu, but I know if I run sudo olsrd -d 0 it will run as a daemon in the background, as I already do this on our OpenBSD machines. What is the easiest way to get olsrd to run at startup? Is there something wrong with the default script that must be adjusted?

Thanks

nevermind, there is a file in the /etc/default folder that contains the parameters passed in. the START_OLSRD variable needed to be uncommented, as the "start" function read that variable but the "restart" function did not. Uncommenting that variable fixed the starting problem, it now just doesn't dump me back to a prompt after starting, I have to hit ctrl+c, which oddly doesn't kill the service, just dumps to the prompt. :confused:

---

