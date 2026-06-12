---
title: "ubuntu box for backup and remote access"
date: 2008-02-10
forum: General Help
---

### Post by vtcat on 2008-02-10
I have a small network of XP boxes at one location, and a Feisty box I've been manually backing them up to.  I also occasionally access the Feisty box from a remote Feisty box via ssh.

I'm replacing the Feisty box with a newer Gutsy box, and would like to automate the process so that the XP My Document folders are mirrored/sync'd to folders on the Gutsy box, which are in turn available remotely.

I'm looking for advice, or a link to advice, on the best way to accomplish this.  I'm pretty much a newbie, but am guessing smbfs + rsync.  I've seen reference in the forums to cron also, but the XP boxes get turned off at night and rebooted occasionally during the day.

---

### Post by quaith on 2008-02-11
Here's a link with detailed instructions about setting up an rsync backup:

[http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/](http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/)

Al Stevens

---

