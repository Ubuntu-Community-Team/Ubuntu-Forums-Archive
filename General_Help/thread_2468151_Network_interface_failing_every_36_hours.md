---
title: "Network interface failing every 36 hours"
date: 2021-10-19
forum: General Help
---

### Post by mikequist on 2021-10-19
I have a vps running Ubuntu 20.04.3. This is a server which is running a bunch of media programs (torrents, jellyfin, etc). I have been having a problem since I set it up, that the network interface (eth0) would go down from time to time, and the only way to fix it was log in to the web console, and reboot it. I found/adapted a script that runs every minute, which checks if eth0 is up, and tries to restart it if not. If that fails to work, it reboots. Looking through the logs for that script, it seems that eth0 goes down every 36 hours, pretty much exactly! This seems like it has to be significant, and should help solve the root issue-- which I have never been able to track down. I haven't noticed anything relevant in any of the other logs, though I could certainly be overlooking something. Can anyone help solve this issue? To be honest, the script works well, and my total downtime is about 2 minutes every 36 hours, so I can and have been living with it. Since I just discovered the cyclical nature of the problem though, it has gotten me curious.

```
cat /var/log/netcheck.log | grep rebooting
2021-09-26 22:35:27 Network is still not working, rebooting
2021-09-28 10:37:27 Network is still not working, rebooting
2021-10-01 06:43:26 Network is still not working, rebooting
2021-10-02 18:45:26 Network is still not working, rebooting
2021-10-05 11:31:26 Network is still not working, rebooting
2021-10-06 23:33:26 Network is still not working, rebooting
2021-10-08 11:35:26 Network is still not working, rebooting
2021-10-09 23:37:26 Network is still not working, rebooting
2021-10-11 11:39:26 Network is still not working, rebooting
2021-10-12 23:41:26 Network is still not working, rebooting
2021-10-14 11:43:26 Network is still not working, rebooting
2021-10-15 23:45:26 Network is still not working, rebooting
2021-10-17 11:47:26 Network is still not working, rebooting
2021-10-18 23:49:26 Network is still not working, rebooting


```

---

### Post by TheFu on 2021-10-19
Instead of rebooting, why not just restart the network subsystem?  That would take 5 seconds.
What do the system logs show at the times when the network fails?
Typically, I'd check the NIC, cables, switch port as part of my basic troubleshooting.

I have a motherboard Realtek NIC that was dropping packets. Disabled that and put in a spare $10 PCIe NIC I had lying around. No more dropped packets. Seems the Realtek NIC had some hardware issue. If I were doing it again, I'd have gotten a $25 Intel PRO/1000 NIC (or any in the family for a similar price that uses e1000e or igb drivers) and been done with it.

---

### Post by mikequist on 2021-10-20
Thanks for the reply. By network subsystem, do you mean the network interface? The script that runs does try that before rebooting, but it never seems to work. Here is an example from the logs:

```
2021-10-18 23:49:01 Network is down, failed check number 1 of 5
2021-10-18 23:49:06 Network is down, failed check number 2 of 5
2021-10-18 23:49:11 Network is down, failed check number 3 of 5
2021-10-18 23:49:16 Network is down, failed check number 4 of 5
2021-10-18 23:49:21 Network is down, failed check number 5 of 5
2021-10-18 23:49:21 Network was not working for the previous 5 checks.
2021-10-18 23:49:21 Restarting eth0
2021-10-18 23:49:26 Network is still not working, rebooting


```

Since this is a VPS I can't swap any cables.

Edit: here's the script if you're interested [https://github.com/ltpitt/bash-network-repair-automation](https://github.com/ltpitt/bash-network-repair-automation)

---

