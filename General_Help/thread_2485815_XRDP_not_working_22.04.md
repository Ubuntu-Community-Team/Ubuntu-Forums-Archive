---
title: "XRDP not working 22.04"
date: 2023-04-10
forum: General Help
---

### Post by fahza on 2023-04-10
I have tried just about everything I can find in google to get this working, I even ran some script that most said worked and well it removed XRDP and did a clean install my error still persists.

The error is that either the xrdp-sesion.service will not start along with  xrdp not running with the same kind of errors.
error for xrdp-sesman is Apr 10 14:50:29 nagios xrdp-sesman[4588]: sesman is not running (pid file not found - /var/run/xrdp/xrdp-sesman.pid)

Apr 10 15:09:41 nagios systemd[1]: Starting xrdp daemon...
Apr 10 15:09:41 nagios xrdp[5421]: [INFO ] address [0.0.0.0] port [3389] mode 1
Apr 10 15:09:41 nagios xrdp[5421]: [INFO ] listening to port 3389 on 0.0.0.0
Apr 10 15:09:41 nagios xrdp[5421]: [INFO ] xrdp_listen_pp done
Apr 10 15:09:41 nagios systemd[1]: xrdp.service: Can't open PID file /run/xrdp/xrdp.pid (yet?) after start: Operation not permitted
Apr 10 15:09:42 nagios systemd[1]: Started xrdp daemon.
Apr 10 15:09:43 nagios xrdp[5422]: [INFO ] starting xrdp with pid 5422
Apr 10 15:09:43 nagios xrdp[5422]: [INFO ] address [0.0.0.0] port [3389] mode 1
Apr 10 15:09:43 nagios xrdp[5422]: [INFO ] listening to port 3389 on 0.0.0.0
no connections are available
I do have ssh working just fine but would like a GUI as well, I do not know every Linux command and something for me are just easier with a GUI.
If there is a better program then xrdp I am willing to try it.

---

### Post by fahza on 2023-04-10
Figured it out, forgot to add the /24 after the IP address for firewall, DOH!

---

### Post by #&amp;thj^% on 2023-04-10
Good Job, great detective work. ;)

---

### Post by mIk3_08 on 2023-04-10
> **fahza said:**
> Figured it out, forgot to add the /24 after the IP address for firewall, DOH!
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by vietairs on 2023-04-18
> **fahza said:**
> Figured it out, forgot to add the /24 after the IP address for firewall, DOH!
Hi fahza,
 
I have the similar issue with xrdp.
Can you show me where should I add /24 after the IP address? 

Best Regards,
Harvey

---

