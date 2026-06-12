---
title: "Failed to load session &quot;ubuntu&quot; in Ubuntu 12.10"
date: 2013-03-12
forum: General Help
---

### Post by RaspberryPeanut on 2013-03-12
Hello all!

With me freshly installing this new distribution I ran into this problem after the first time I updated all my software. My steps were:
1) Install Ubuntu 12.10 WITHOUT being connected to the internet
2) Logging in and connecting to the internet
3) Updating all my software from the Software Updater
4) Restarting my computer
5) Trying to log back in but being met with "Failed to load session 'ubuntu'"

I've looked at similar threads but seeing as how I'm still somewhat new to Linux I'm unsure as far as what to do to fix my problem. I pressed CTRL + ALT + F1 and logged in using that method. I then used this bit of code from another thread```
sudo grep 'warning\|loops\|segfault\|error' -iHnr /var/log/dmesg /var/log/syslog /var/log/kern.log /var/log/Xorg.0.log $HOME/.xession-errors > $HOME/mylog.txt && nano $HOME/mylog.txt
```

which produced an incredibly long list of warnings and a few errors. Help?

---

