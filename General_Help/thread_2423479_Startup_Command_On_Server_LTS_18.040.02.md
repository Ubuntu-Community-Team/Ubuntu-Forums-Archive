---
title: "Startup Command On Server LTS 18.040.02"
date: 2019-07-24
forum: General Help
---

### Post by krypticroadkill on 2019-07-24
We have Ubuntu Server 18.04.02 server with no desktop/GUI.

We run it inside VirutalBox for PiHole.  

Is  there a way (putting aside the security and best practice concerns) to  automatically run a command elevated after startup (ex:pihole -c which brings up the chronometer)?

---

### Post by mastablasta on 2019-07-24
with a script.

the search didn't take long: [https://askubuntu.com/questions/88589/run-command-at-boot-as-root](https://askubuntu.com/questions/88589/run-command-at-boot-as-root)

---

### Post by TheFu on 2019-07-24
For any non-interactive, non-GUI command, use cron.  It can start daemons using any userid on the system.  The most common issue is that cron doesn't bring an interactive environment with it, so any extra environment variables need to be manually setup for the program.

---

