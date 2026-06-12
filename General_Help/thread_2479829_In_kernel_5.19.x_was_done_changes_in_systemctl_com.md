---
title: "In kernel 5.19.x was done changes in systemctl commands ?"
date: 2022-10-09
forum: General Help
---

### Post by aug7744 on 2022-10-09
Hello.
Ubuntu 20.04.5.
I have used the command below
sudo systemctl 
to enable an custom systemd script to run when the OS shutdown had worked in 5.18.
Now in 5.19.14 the script not run.

The script point to an bash file (executable) to run and dmwriteback flush before OS shutdown.
Another strange is trying install gamemode deb packages using "sudo dpkg -i *.deb" in an directory with all correct files and dependencies all is installed correctly, but the gamemode daemon not work.
However installing all same packages in "/var/cache/apt/archives/" the gamemode daemon work.
Pehrhaps in 5.19.x was done any security changes ?
Thanks for reading.
Have an nice day.
The script and command detail are below.

----
sudo nano /etc/systemd/system/test.service

[Unit]
Description=Test
DefaultDependencies=no
Before=sleep.target umount.target

[Service]
Type=oneshot
User=root
Group=root
ExecStart=/usr/local/bin/test.sh
TimeoutStartSec=0

[Install]
WantedBy=sleep.target umount.target

---

sudo systemctl enable test

---

