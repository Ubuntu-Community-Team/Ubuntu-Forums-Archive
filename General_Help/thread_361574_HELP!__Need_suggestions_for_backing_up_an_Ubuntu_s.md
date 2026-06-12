---
title: "HELP!  Need suggestions for backing up an Ubuntu server"
date: 2007-02-14
forum: General Help
---

### Post by Dark Bensen on 2007-02-14
I need to backup up an Ubuntu machine.  I am backing up 40+ machines in my environment with a Windows machine running Veritas BackupExec v.9.1.  Normally, every machine that gets backed up needs a remote agent installed on it in order to get a good solid backup.  But none of the remote agents will install on the Ubuntu machine.

Please let me know if you:

1.  Have experience backing up an Ubuntu machine from a Windows environment running BackupExec.

...or...

2.  Have some other suggestion(s) for a way to get this Ubuntu machine backed up.

---

### Post by localzuk on 2007-02-14
This may be of interest to you: [http://www.ubuntux.org/ubuntu-veritas-backup-exec-and-you](http://www.ubuntux.org/ubuntu-veritas-backup-exec-and-you)

---

### Post by Dark Bensen on 2007-02-14
I really appreciate your input!  And I'm going to give that a shot.  However, the main thing that I'm up against is BackupExec's documentation that the new RALUS (remote agent for linux and unix servers) came out in BackupExec 10 and is incompatible with previous versions.  And since I'm on v9.1, it's quite possible that I'm screwed!  LOL!  But, like I said, I'm going to try these steps and see if it will work.  If not, I'll consider upgrading to v10 (which will open 40 new cans of worms!)

But thanks again for your offer of help!

---

### Post by Dark Bensen on 2007-02-14
:)

---

### Post by lamego on 2007-02-14
> 2. Have some other suggestion(s) for a way to get this Ubuntu machine backed up.
Is not a beautiful solution but you could always install samba and map a drive on a windows box, I guess the windows agent supports backing up from network drives..

---

