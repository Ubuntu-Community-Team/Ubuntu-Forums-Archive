---
title: "Crontab does not run command"
date: 2013-09-04
forum: General Help
---

### Post by charkel2 on 2013-09-04
Hello,
I am running a server with a craftbukkit server. It runs in a screen called "minecraft". I have a rsync command that runs every hour backing up the serverfiles and now I want to make a automatic restart. But the command I use to restart the server apparently doesn't work with crontab.

root@charkel:~# crontab -e
```

59 * * * * rsync --progress -azv /home/serverfiles/ ~/Dropbox/serverbac$
0 10 * * * screen -S minecraft -X stuff 'stop'`echo -ne '\015'`

```

---

### Post by bkline on 2013-09-04
If minecraft is controlled /etc/init.d it might be simpler and more reliable to use the restart command implemented by that script.

---

### Post by ian-weisser on 2013-09-04
A couple issues here.

First, your minecraft server should not be running as root or your username. It should be a separate system user. Your current setup will cause permission and ownership headaches when you need to reinstall from a backup.

Second, you seem to want access to the op commands. For that you need screen. If you don't need access to those commands, there are easier ways to start/stop the headless minecraft server and you don't need screen.

Third, cron jobs run in a limited environment. That means that wherever your minecraft executable (or script) is installed, it's probably not in any of the places cron checks. That's easy to fix: Use full path names for all commands and scripts.

---

