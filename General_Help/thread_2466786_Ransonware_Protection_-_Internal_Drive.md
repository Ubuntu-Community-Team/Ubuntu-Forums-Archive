---
title: "Ransonware Protection - Internal Drive"
date: 2021-09-06
forum: General Help
---

### Post by Quarkrad on 2021-09-06
I currently backup (rdiff-backup) to an internal drive.  However, in the event of something nasty happening this drive is vulnerable as it is continually mounted.  I'm sure I have read, in the past on this forum, a technique (I think it was @TheFu) where the drive is in some sort of 'push' or 'pull' or 'read only' mode so that it is protected.  I may be wrong in my recollection/understanding.  If it is true the next question is how to set this up, but at least I will have something to start looking into.

---

### Post by ActionParsnip on 2021-09-06
Have a script to mount the drive, run the backup then unmount.
You can also unplug it physically when the job isn't running. This will ensure nothing can touch your data

---

### Post by rbmorse on 2021-09-06
If you're using rdiff-backup to backup to a dedicated partition on another device on the local machine, you can have the script that runs the backup mount/unmount the partition holding the store as part of the backup operation.  

Not as good as backing up on an external server (that's where the push/pull comes in) but it's better than nothing.

---

### Post by TheFu on 2021-09-06
Have the backup server "pull" the backups. This is the only way that backup data can ensure it doesn't get a chance to encrypt older versions of the backup sets.
The client machines shouldn't have direct access to any of the backup storage. Only the backup server should have that access.

rdiff-backup works over ssh, so setup a connection from the backup server account (can be sudo, root, or a root-equiv account) to each client machine to be backed up. On the client machine side, rdiff-backup has to run as root-equiv (which can be root or another userid with a uid of 0).

Lock down the ssh connection between the backup accounts used from the server to the client machines. We don't want any systems other than the backup server being allowed to ssh in as root-equiv, right?  The sshd_config "match" settings can do that on a per-user AND per-IP basis.

More advanced and security minded people would limit the programs that can be run by the client-side root-equiv account(s) to be just those needed for the backup processes.  
Perhaps a pre-backup script, post-backup script and rdiff-backup?   In my _pre-backup_ scripts, I gather system information like the partition tables, hardware connected, crontabs, ruby gems, perl modules, LVM layouts, and of course, the list of manually installed packages, then I'll have the script create an LVM snapshot or dump a DBMS to a file or stops a daemon providing network services. These things are necessary to get a clean backup on a running system.  

_rdiff-backup_ does what it does, then 

the _post-backup_ script runs and restarts daemons, deletes snapshots, and has the client back the way it was before the backup process started.

That's the theory.

A tiny "pull" rdiff-backup script - run from the backup server:
```
$ sudo /usr/bin/rdiff-backup  \
       --exclude-special-files \
       --include /usr/local --include /etc --include /home --include /root \
       --exclude '**'   backup3489@{remote-machine}::/ \
       /Backups/{remote-machine}

$ sudo /usr/bin/rdiff-backup    --remove-older-than 90d --force /Backups/{remote-machine}
```

Above, backup3489 is the userid on the "remote-machine" that is root-equiv. Here's what the passwd file looks like:
```
backup3489:x:0:0:Backup Account,,,:/home/backup3489:/bin/bash
``` Strictly speaking, the HOME could be /root/  Just need to put the ssh public key into the root authorized_hosts file correctly. On ubuntu, that would need to be accomplished manually, since ssh-copy-id to root isn't allowed (without some other security considerations).  There are always trade-offs.

Also, on the backup server, it might be very handy to setup the ~/.ssh/config file for each backup-client connection to automatically handle the different backup userids and ssh ports (if non-standard ssh port is used).

Nothing special about the backup3489 username.  I just use random usernames, to limit viable guesses. Don't use commonly used account names - no root or admin or administrator or backup, obviously.

---

