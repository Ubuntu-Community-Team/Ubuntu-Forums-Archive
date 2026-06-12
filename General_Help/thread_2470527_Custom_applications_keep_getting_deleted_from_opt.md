---
title: "Custom applications keep getting deleted from /opt/"
date: 2022-01-02
forum: General Help
---

### Post by megatron36 on 2022-01-02
I have several web apps installed using guides from the developers. They all work fine but for some reason every 3-4 weeks the whole /opt/ directory just gets wiped and I have to follow the guides and reinstall them. I'm at a lost to where to even look on what deleted the folders and everything under them.
I've taken to making a tar.gz of opt of the applications so I can just tar -xzvf it backl to /opt/ sometimes it works sometimes it doesn't for some reason. Does anyone know what log file I can look in to see whats deleting said folders or if its a system thing to stop deleting /opt/ custom application folders?

---

### Post by schragge on 2022-01-03
Are you perhaps running something like [tmpreaper](https://manpages.debian.org/unstable/tmpreaper/tmpreaper.8.en.html)? It's controlled by **/etc/tmpreaper.conf**.

---

### Post by dragonfly41 on 2022-01-03
I have not experienced that.

My first thought was to apply a watch on /opt/ .. or just one app in /opt/.

[https://askubuntu.com/questions/541128/monitor-folder-contents-changes](https://askubuntu.com/questions/541128/monitor-folder-contents-changes)

But since this /opt purge event occurs every 3-4 weeks this running background watch process might be a burden to impose on your system.

You could try watching one app subdirectory at a time in /opt.

   inotifywait /opt/myApp --recursive --monitor   

Yakuake drop down terminal is handy for this. You can launch yakuake, run the watch command and just toggle F12 to see the watch log.

---

### Post by KBar on 2022-01-03
What do you have in */etc/cron.monthly*?

---

### Post by schragge on 2022-01-03
Another possible culprit is systemd. See [tmpfiles.d(5)]("https://www.freedesktop.org/software/systemd/man/tmpfiles.d.html")

---

