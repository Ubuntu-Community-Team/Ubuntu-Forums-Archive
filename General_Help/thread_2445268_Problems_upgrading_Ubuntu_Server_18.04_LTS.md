---
title: "Problems upgrading Ubuntu Server 18.04 LTS"
date: 2020-06-11
forum: General Help
---

### Post by tuck85 on 2020-06-11
Hello

Yesterday I tried to upgrade my Ubuntu Server 18.04 LTS install but I got some error messages. After doing "sudo apt update" and "sudo apt upgrade" I got this message:

```
Job for systemd-networkd.service failed because a timeout was exceeded.
See "systemctl status systemd-networkd.service" and "journalctl -xe" for details.
```

The progress bar was at 15% and it stayed there for a long time. I restarted and tried again to upgrade then I got this message:

```
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
```
The system suggested to do "sudo dpkg --configure -a" which I did. After some waiting the problem appeared to be solved. I did "sudo apt update" and "sudo apt upgrade" again and now everything ran fine.
What could have been the cause of these errors and what exactly happened? Did I do something wrong? Is my system damaged now? Or corrupted?

Also, when I run "ps -aux" I see the following running process:
```
/usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal

```

I suppose this has something to do with the restart I did. What should I do to solve this?

Thanks!

---

### Post by TheFu on 2020-06-11
Only 1 APT related process can run on the system at a time.  You may have started one at the time when an automatic task happened to be running.  Probably nothing more than that.

---

