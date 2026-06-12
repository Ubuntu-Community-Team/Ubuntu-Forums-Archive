---
title: "SFTP chroot folder /var/www"
date: 2016-02-25
forum: General Help
---

### Post by vaarsn on 2016-02-25
I need to access to **/var/www** with reading and writing permissions through SFTP. I created the user called **sftp** with its home folder **/var/www**, I added it to existed group called **www-data**, executed **chown -R sftp.www-data /var/www**, set 755 and 644 perms to files and folders. Everything seem to be fine, I can establish SFTP connection, I'm reaching my home directory, which I mentioned above but sftp user I created has perms to open and edit the files outside its home directory and located upper level of **/var/www**.
That's why I added appropriate records to **/etc/ssh/sshd_config**:

```
Subsystem  sftp  internal-sftp
Match User sftp
    ChrootDirectory /var/www/
    AllowTCPForwarding no
    X11Forwarding no
    ForceCommand internal-sftp
```

Ater that I"m getting the next error in my FileZilla client:

```
Command:    open "sftp@mysite.com" 22
Command:    Pass: ***********
Error:    Network error: Software caused connection abort
Error:    Could not connect to server

```
If I'm doing **ChrootDirectory /var** then everything is working fine but sftp user can see all files and folders within **/var** folder. Could you please help me to solve the issue?

Thanks

---

