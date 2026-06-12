---
title: "Backup scheduling with systemd"
date: 2016-03-14
forum: General Help
---

### Post by marko-subasic on 2016-03-14
I am trying to do a backup of home directory from local SSD to local HDD on a desktop PC running Ubuntu 15.10. The idea is to perform a synchronization using rsyncrypto during the poweroff equence, because there are no file operations in home directory at that time, and I don't really care if the sync takes some time. So I created this systemd unit:

```
[Unit]
Description=backup to internal HDD before shutdown
Before=umount.target poweroff.target
After=plymouth-poweroff.service
DefaultDependencies=no


[Service]
Type=oneshot
User=root
ExecStartPre=/bin/plymouth message "--text=Backuping SSD to HDD..."


ExecStart=/bin/bash /home/user/rsyncrypto.backup


ExecStop=/bin/plymouth message "--text=Finished backuping SSD to HDD"
KillMode=none


[Install]
WantedBy=poweroff.target

```

The rsyncrypto.backup script executed by the unit, builds several file lists (using the find) and runs several rsyncrypto instances in parallel using those file lists. Once enabled, the service gets started during the poweroff sequence, as expected, but no actual syncing gets done. The problem seems to be that during the creation of backup file lists, the target HDD gets unmounted. I have checked that the HDD is mounted when the script starts, but by the time file lists are created (which takes a couple of seconds), the HDD gets unmounted, and rsyncrypto just reports error that it can't find encryption keys which are on the HDD. After all rsyncrypto instances report errors and exit, I check all mounts, and HDD is not there any more, as well as some other mounts that were present when the script was started.

From what I understand, this should not happen. Unmounting of all local drives is triggered by umount.target which should be started after my service. The service type is 'oneshot', so all subsequent units should wait until it finishes.

What am I missing?

---

### Post by marko-subasic on 2016-04-06
After some help from [Google+ systemd  page]("https://plus.google.com/u/0/113476905475449706999/posts/BuyQFHG3gpn") I have finally found a solution which seems to do what I want. 

The problem with the approach from the first post is in the fact that systemd (ver. 225 of Ubuntu 15.10) doesn't allow ordering of shutdowns of running units with starting of new units. The service unit from the first post is triggered by poweroff.target, but all local mounting points units are conflicting poweroff.target (actually local mounts are conflicting umount.target pulled in by the poweroff.target). Conflicting units are shut down before any newly triggered unit gets started, so my backup service could not access its target drive which was unmounted before the service had started.

Here is the unit file that does what I want, together with comments explaining the entries.

```

[Unit]
Description=backup to internal HDD before shutdown

## The service will be stopped only during poweroff sequence (not during the reboot sequence)
Conflicts=poweroff.target

## The service has to be stopped proir to stopping of local-fs.target - unmounting of local mounts
After=local-fs.target

## This mount points are needed for the backup. This entry is just ni case, as ordering with local-fs.target should ensure the same thing
RequiresMountsFor=/tmp /media/user/backup /home

DefaultDependencies=no


[Service]
## oneshot type makes all following unit to wait for this service to finish - this applies to starting and shuting down
Type=oneshot

## The service does nothing when started but has to wait to be stopped at the right time
RemainAfterExit=yes

## The backup usually takes couple of minutes so shutdown timeout is set to 2h which should be enough
TimeoutStopSec=7200

User=root

## The actual backup gets done when the service is shuting down
ExecStop=/bin/bash /home/user/rsyncrypto.backup

KillMode=none


[Install]
## The service is started only when I log in
WantedBy=user-1000.slice

```

One nice thing with this approach is that no backup will be done if I haven't logged in prior to poweroff. In such case no backup is needed, as probably no changes have been made in my home directory.

---

