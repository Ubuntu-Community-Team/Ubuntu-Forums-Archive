---
title: "[SOLVED] backuppc and ssh problem"
date: 2008-03-25
forum: General Help
---

### Post by squeakyfrommage on 2008-03-25
I've got two systems with same version of ubuntu (7.10) installed. I have backuppc running on an server running ubuntu server.  I configured the two desktops in (it seems to me) identical fashion. One will work with backuppc and one won't.  No matter what I do, I can't seem to get the second (nonworking) computer to allow backuppc to login w/o a password. I've cleared everything and started over probably 15 times.  Does anyone have advice for where I should look for differences? config.pl, ssh_config and sshd_config are identical on the two machines. 

The error messages I'm getting: 
Running: /usr/bin/ssh -q -x -l root jeni /usr/bin/rsync --server --sender --numeric-ids --perms --owner --group --devices --links --times --block-size=2048 --recursive -D --ignore-times . /folders
Xfer PIDs are now 23723
Got remote protocol 1836213584
Fatal error (bad version): Permission denied (publickey,password).

Can't write 4 bytes to socket
fileListReceive() failed
Done: 0 files, 0 bytes
Got fatal error during xfer (fileListReceive failed)
Backup aborted by user signal

---

### Post by Dr Small on 2008-03-25
Could you please state what the problem is?

---

### Post by squeakyfrommage on 2008-03-25
As I stated, backuppc can't login via ssh w/o a password on one computer, but it can on the other. I need it to do so on both, otherwise backuppc simply fails.

---

### Post by Dr Small on 2008-03-25
Are you using SSH keys?

---

### Post by squeakyfrommage on 2008-03-26
Sorry for not being clear about that, I followed the directions here: [http://backuppc.sourceforge.net/faq/ssh.html](http://backuppc.sourceforge.net/faq/ssh.html) to set up keys.  It was succesful for 1 ubuntu desktop, and 2 other desktops, but not for an apparently identical ubuntu desktop.  I'm kind of making myself nuts with this one, I really can't see any differences between the one that works and the one that doesn't.

---

### Post by squeakyfrommage on 2008-04-02
I installed this morning's update to openssh and now the problem's gone. I still don't know what it was, since the two computers (one working one non) had the same version. But it's solved, at least.

---

