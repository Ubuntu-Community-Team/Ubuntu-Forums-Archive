---
title: "Computer won't shutdown"
date: 2021-10-15
forum: General Help
---

### Post by rsteinmetz70112 on 2021-10-15
This mornintg I have one computer that won't shutdown. I tried reboot, shutdown and the commands below.

```
# systemctl reboot
Failed to set wall message, ignoring: Connection timed out
Failed to reboot system via logind: Connection timed out
# systemctl reboot
Failed to set wall message, ignoring: Connection timed out
Failed to reboot system via logind: Connection timed out
Failed to start reboot.target: Connection timed out
See system logs and 'systemctl status reboot.target' for details.
It is possible to perform action directly, see discussion of --force --force in man:systemctl(1).
```

I turned off the power, The first time I got a fast blinking power light. I restarted again after waiting about 10 seconds and it booted normally and I can now reboot.

---

### Post by ActionParsnip on 2021-10-15
If you run:
```

sudo shutdown -h now

```
Does the system power off OK or do you see the same output?

---

### Post by rsteinmetz70112 on 2021-10-19
Sorry I've been away for a long weekend. 

But I got the same output with the shutdown command and with reboot as well. I tried the systemctl reboot after the others had failed. The computer seemed very sluggish as well. 

Once I pulled the plug, alllowed some time before restarting and restarted it seems to work fine. It's now been running all weekend.
```
$ uptime
 10:08:03 up 3 days, 23:50,  1 user,  load average: 0.71, 0.30, 0.29
```

---

### Post by sudodus on 2021-10-19
- Maybe the file system need repairing and maybe some file is damaged. (Pulling the plug can cause such problems, even if there were no problems earlier, so there could be two reasons for checking the file system.)

- Did you check the S.M.A.R.T. information on the system disk?

- Maybe a fresh backup of everything that you cannot afford to lose is extra important now.

---

### Post by rsteinmetz70112 on 2021-10-19
I have automated backups to a remote server so I think my backups are fine. It actually seems to be running better than it was.
I did run fsck on the filesystems and they came out fine.
I didn't get the S.MA.R.T information of the drives.  The system disk is however a redundant RAID 1 array lvm2 over mdadm, so I'm fairly confident I'd find a hardware problem.
I haven't finished looking through the logs, but the results so far don't point anywhere obvious.
My current theory is that somehow multiple graphic sessions got started. I can see how that might really slow things down but I can't see how it would stop a shutdown.
I hate it when stuff happens and I can't figure out why, it's one of the reasons I hate Windows.

---

