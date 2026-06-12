---
title: "sftp (openssh) auto change directory after login"
date: 2013-05-15
forum: General Help
---

### Post by sgm277 on 2013-05-15
I used openssh-server for SFTP, the user was chrooted to a specific directory (All components of the pathname must be root-owned directories that are not writable by any other user or group --- from sshd_config). Eg: /home/sftp

There are one sub-directory in /home/sftp named upload ,the sftp user has full access to this directory ( the owner of this directory is the sftp user). The sftp user will use winscp to login to the sftp server.

Is there any way to let the sftp user auto enter this directory  rather than typing "cd upload" manually.

Thanks

---

### Post by Nico_Tillmann on 2014-02-10
Solution seems simple when you found it, but it took me some time too getting it solved.

1) define in  /etc/ssh/sshd_config  the apropriate konfiguration[INDENT]Match User sftp_example[/INDENT]
[INDENT=2]ChrootDirectory /var/www/servers/my.server.root
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
[/INDENT]
[INDENT]Match User sftp_example2[/INDENT]
[INDENT=2]ChrootDirectory /home/sftp
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
[/INDENT]
 
2) define the users home in /etc/passwd like  this:[INDENT]sftp_example: x :1001:33::/htdocs:/bin/false
      sftp_example2: x :1002:33::/uploads:/bin/false
[/INDENT]
       

Who does it work?
sftp_example:
User is changed rooted to  /var/www/servers/my.server.root/ and after login he he get's am implizi chdir to /htdocs  which translates to  /var/www/servers/my.server.root/htdocs

sftp_example2:
User is changed rooted to  /home/sftp and after  login he he get's am implizi chdir to /uploads which translates to /home/sftp/uploads

Hope that will help you 

Nico

---

