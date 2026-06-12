---
title: "clamd daemon failing to start"
date: 2015-10-21
forum: General Help
---

### Post by blackflame2996 on 2015-10-21
I recently set up a samba server, and am trying to use clamav to scan for malware on the shared folders periodically. freshclam and clamscan both work correctly, but trying to start the service fails.

```

[FONT=monospace][COLOR=#000000]# systemctl start clamd@scan
# systemctl status clamd@scan[/COLOR]
clamd@scan.service - Generic clamav scanner daemon
   Loaded: loaded (/usr/lib/systemd/system/clamd@scan.service; enabled)
   Active: [COLOR=#FF5454]**failed**[/COLOR][COLOR=#000000] (Result: start-limit) since Wed 2015-10-21 00:02:47 MDT; 7min ago[/COLOR]
  Process: 6152 ExecStart=/usr/sbin/clamd -c /etc/clamd.d/%i.conf --nofork=yes [COLOR=#FF5454]**(code=exited, status=1/FAILURE)**[/COLOR][COLOR=#000000][/COLOR]
 Main PID: 6152 (code=exited, status=1/FAILURE)

Oct 21 00:02:47 localhost.localdomain systemd[1]: [COLOR=#000000]**clamd@scan.service: main process exited, code=exited, status=1/FAILURE**[/COLOR][COLOR=#000000][/COLOR]
Oct 21 00:02:47 localhost.localdomain systemd[1]: [COLOR=#000000]**Unit clamd@scan.service entered failed state.**[/COLOR][COLOR=#000000][/COLOR]
Oct 21 00:02:47 localhost.localdomain systemd[1]: clamd@scan.service holdoff time over, scheduling restart.
Oct 21 00:02:47 localhost.localdomain systemd[1]: Stopping Generic clamav scanner daemon...
Oct 21 00:02:47 localhost.localdomain systemd[1]: Starting Generic clamav scanner daemon...
Oct 21 00:02:47 localhost.localdomain systemd[1]: [COLOR=#000000]**clamd@scan.service start request repeated too quickly, refusing to start.**[/COLOR][COLOR=#000000][/COLOR]
Oct 21 00:02:47 localhost.localdomain systemd[1]: [COLOR=#FF5454]**Failed to start Generic clamav scanner daemon.**[/COLOR][COLOR=#000000][/COLOR]
Oct 21 00:02:47 localhost.localdomain systemd[1]: [COLOR=#000000]**Unit clamd@scan.service entered failed state.**[/COLOR]
[COLOR=#000000][/COLOR]
[/FONT]
```

Googling this issue, everyone said that this issue is caused by having low memory, less than ~300MiB. However, my system has 8GiB, 7.1GiB of which are free. Does anyone know another problem that may cause this issue?

---

### Post by SeijiSensei on 2015-10-21
I wonder if it has something to do with this:
```
Process: 6152 ExecStart=/usr/sbin/clamd -c /etc/clamd.d/%i.conf --nofork=yes (code=exited, status=1/FAILURE)
```

My guess is that the %i isn't being replaced with the correct value to match the name of the configuration file in /etc/clamd.d.  I've tried to stay away from systemd as long as possible, so I don't know where you would need to make the change.  However "%i.conf" is a valid file name, so if the correct configuration is named something else, you could create a symlink to it.  Suppose the correct name is myclamd.conf.  Then you could use:
```

cd /etc/clamd.d
sudo ln -s myclamd.conf %i.conf

```

You'll need to replace "myclamd" with the actual name of the configuration file in that directory.  Whether that will fix the problem I cannot say.  I'm just guessing here.

---

