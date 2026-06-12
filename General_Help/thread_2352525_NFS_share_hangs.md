---
title: "NFS share hangs"
date: 2017-02-13
forum: General Help
---

### Post by mypalabok on 2017-02-13
ubuntu-16.04.1-server-amd64

i installed this ubuntu server version, shared a folder, type NFS, and mounted it remotely successfully.  this NFS share experiences heavy traffic as i use it for data backup. from time to time, the remote host that have mounted the NFS share would hang requiring me to restart the ubuntu server. after that, everything goes back to normal.


my /etc/fstab contains this entry for the shared folder: /dev/sdb1       /mnt/2ndHDD     xfs     defaults        0       0



this is my first time to use NFS shared directories that is heavily used, could there be more options/switches to provide for NFS shares to handle traffic or using NFS for heavy traffic is not a good thing?

---

### Post by SeijiSensei on 2017-02-13
You can try increasing the sizes of the read and write buffers.  If you're mounting the share from the client's /etc/fstab, then try changing "defaults" to "defaults,rsize=65536,wsize=65536" and see if that helps.

You can also try adding "async" to the options list if your backup server is well-protected against power outages.  Read the [manual page for nfs]("https://linux.die.net/man/5/NFS") if you have not done so already.

Otherwise I suggest using rsync to manage large transfers for backup purposes.

---

### Post by mypalabok on 2017-02-14
rsync is good but it expects data to be present already before using it. my data are generated at midnight and gets picked up at 5am by the backup process.

i will try the "async" option first and see. thanks.

---

### Post by SeijiSensei on 2017-02-14
I just time my backup script using rsync to run after all the needed files are created.

---

