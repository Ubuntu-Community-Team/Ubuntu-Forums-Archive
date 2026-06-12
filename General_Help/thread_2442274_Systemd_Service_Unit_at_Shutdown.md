---
title: "Systemd Service Unit at Shutdown"
date: 2020-05-01
forum: General Help
---

### Post by Quarkrad on 2020-05-01
I'm looking to run a script at shutdown so created a service unit file in lib/systemd/system called backup.service.  The contents of the file is:

```
Unit]
Description=Run my custom task at shutdown
Before=shutdown.target

[Service]
Type=oneshot
ExecStart=/bin/true
ExecStop=/usr/bin/backup.sh
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

The script I'm running /usr/bin/backup.sh is currently just backing up my /home/user/Documents folder to a backup disc as a test to prove if everything works.  All appeared to be working fine in that the Documents folder is being backed up and if the contents of any file is changed these changes too are backed up in subsequent re-boots.  However ........... all is not working well.  When I power up I can hear my backup disc working away so it looks like I'm either not backup up at shutdown but at startup.  Or I'm backing up at both shutdown and startup.  On my last test I powered down at 20.03 and then power on again at 20.11  The output of **systemctl status backup** is:

```
backup.service - Run my custom task at shutdown
     Loaded: loaded (/lib/systemd/system/backup.service; enabled; vendor preset: enabled)
     Active: active (exited) since Fri 2020-05-01 20:11:42 BST; 54s ago
    Process: 933 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 933 (code=exited, status=0/SUCCESS)

May 01 20:11:42 dadubuntu systemd[1]: Starting Run my custom task at shutdown...
May 01 20:11:42 dadubuntu systemd[1]: Finished Run my custom task at shutdown.

```

Which is telling me (I believe) my backup.service file is running during startup and not shutdown.  At this point I'm not sure why this file is running at startup and not shutdown.  Any advice appreciated - I'm finding this whole systemd environment a bit of a minefield.

---

### Post by Quarkrad on 2020-05-02
Just done another and not much further. But I have noticed something that also appears in the above systemctl status backup:

[I]May 01 20:11:42 dadubuntu systemd[1]: Starting Run my custom task at shutdown...
May 01 20:11:42 dadubuntu systemd[1]: Finished Run my custom task at shutdown.[/I]

Although I can hear my mechanical backup disc hammering away during startup (my **/** and **/home** are on a SSD)  the above two lines appears to say that the backup.service started and finished at the same time - I think I'm now even more confused.

---

