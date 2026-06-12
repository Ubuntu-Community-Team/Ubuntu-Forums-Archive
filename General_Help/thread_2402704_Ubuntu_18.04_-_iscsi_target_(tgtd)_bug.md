---
title: "Ubuntu 18.04 - iscsi target (tgtd) bug?"
date: 2018-10-03
forum: General Help
---

### Post by BobMaze on 2018-10-03
And again a bug in Ubuntu 18.04?

I've purged and reinstalled everything for tgtd and get this error all time!

```
root@vmm:~# systemctl restart tgtd.service
Failed to restart tgtd.service: Unit tgtd.service is not loaded properly: Exec format error.
See system logs and 'systemctl status tgtd.service' for details.
root@vmm:~# systemctl status tgtd.service
&#9679; tgtd.service - Start TGTd iSCSI server
   Loaded: error (Reason: Exec format error)
   Active: inactive (dead)

Oct 03 15:19:39 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:19:41 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:19:41 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:19:41 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:19:42 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:19:42 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:21:12 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:22:28 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:22:34 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
Oct 03 15:22:46 vmm systemd[1]: /lib/systemd/system/tgtd.service:6: Executable path is not absolute: killall -9 tgtd
```

So, what is wrong in Ubuntu again?

Installed tgt version:
```
ii  tgt                                    1:1.0.72-1ubuntu1        amd64                    Linux SCSI target user-space daemon and tools
```

---

### Post by thedrj on 2018-12-07
I've had a similar issue in upstream Debian and noticed I have 2 services set up for tgt (tgt and tgtd) and it willl try *killall -9 tgtd* before starting, because tgtd is killed, systemd restarts it from the other service entry! Highly possible you may have the same issue.

I ran disabled the second (tgtd.service) so it will no longer run, leaving only the first tgt.service to act as my tgt service
```
sudo systemctl disable tgtd
``` 

So, if it's the same on 18.04 servers, it may be a leftover file from a previous package version like it seems to be on [Debian Stretch]("https://packages.debian.org/stretch/amd64/tgt/filelist"), the tgtd.service is not listed as being in the package now.

```

systemctl status tgt
&#9679; tgt.service - (i)SCSI target daemon
   Loaded: loaded (/lib/systemd/system/tgt.service; enabled; vendor preset: enab...
   Active: active (running) since Fri 2018-12-07 14:40:34 GMT; 4min 48s ago
     Docs: man:tgtd(8)
  Process: 732 ExecStartPost=/usr/sbin/tgtadm --op update --mode sys --name Stat...
  Process: 476 ExecStartPost=/usr/sbin/tgt-admin -e -c /etc/tgt/targets.conf (co
  Process: 471 ExecStartPost=/usr/sbin/tgtadm --op update --mode sys --name Stat...
 Main PID: 465 (tgtd)
   Status: "Starting event loop..."
    Tasks: 49 (limit: 4915)
   CGroup: /system.slice/tgt.service
           &#9492;&#9472;465 /usr/sbin/tgtd -f

```

(Note: Below tgtd.service this is already manually disabled in systemd, as I ran the status command after having already disabled it)
```

systemctl status tgtd
&#9679; tgtd.service - Start TGTd iSCSI server
   Loaded: loaded (/lib/systemd/system/tgtd.service; disabled; vendor preset: en...
   Active: inactive (dead)

```


The reason I chose to disable tgtd.service is because */lib/systemd/system/tgtd.service* is much smaller than */lib/systemd/system/tgt.service*. It seems *tgt.service* is a more complete unit, so I suspect it's the newer service unit of the two.
Looking a little further Debian's *tgtd.service* does indeed _not_ have a full path to the killall executable, so could be the case for Ubuntu 18.04 too.
```

[Unit]
Description=Start TGTd iSCSI server

[Service]
ExecStart=/usr/sbin/tgtd && sleep 2 && /usr/sbin/tgt-admin -e
**ExecStop=killall -9 tgtd**
Type=forking

[Install]
WantedBy=multi-user.target

```

You could if you like fix that to **ExecStop=/usr/bin/killall -9 tgtd** if you want/need to use the *tgtd.service* unit over the *tgt.service* unit

---

