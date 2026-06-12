---
title: "Shutdown script required for RefiND"
date: 2019-03-30
forum: General Help
---

### Post by Steve1961 on 2019-03-30
Hi
I’ve just installed the refind boot manager on Ubuntu Mate 18.10 and it works great for my needs. However, I would like to create a systemd shutdown script to ensure that refind-mkdefault is run every time I shutdown.

I’m clueless when it comes to systemd, so wondered if anyone has a ready-made script and service file they could share?

---

### Post by him610 on 2019-03-30
```
man systemd 
```
You might take a look at [https://www.digitalocean.com/community/tutorials/systemd-essentials-working-with-services-units-and-the-journal]("https://www.digitalocean.com/community/tutorials/systemd-essentials-working-with-services-units-and-the-journal") or [https://www.linux.com/learn/understanding-and-using-systemd]("https://www.linux.com/learn/understanding-and-using-systemd")

---

### Post by Steve1961 on 2019-03-30
Thanks for this but I'm not having any luck.  I've created a script that works but can't seem to get the systemd service unit to run.  Here's the file:

[Unit]
Description=Run refind-mkdefault at shutdown
DefaultDependencies=no
Before=shutdown.target halt.target reboot.target
# If your script requires any mounted directories, add them below: 
RequiresMountsFor=/boot/efi
 
[Service]
Type=oneshot
RemainAfterExit=yes
ExecStop=/usr/local/sbin/refind_restore.sh
 
[Install]
WantedBy=halt.target shutdown.target reboot.target


Anyone have any ideas?

---

### Post by Steve1961 on 2019-03-31
As a further update, I can start this service manually and enable it and it runs fine. It just doesn’t seem to run on shutdown

---

