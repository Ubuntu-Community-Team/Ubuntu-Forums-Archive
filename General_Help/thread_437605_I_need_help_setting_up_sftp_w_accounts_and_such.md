---
title: "I need help setting up sftp w/ accounts and such"
date: 2007-05-09
forum: General Help
---

### Post by billdotson on 2007-05-09
I have been looking for a way to setup a sftp server on my other box but I have not been able to find any real help from google regarding setting it up in Linux.  I have ssh and openssh-server installed and can do ssh and vnc stuff but I don't know how to setup sftp user accounts and the like.  I need to setup separate usernames, passwords and separate accessible directories for each.  And I do need sftp, regular ftp will not cut it security wise for what I intend to use it for

thanks.

---

### Post by crispy_420 on 2007-05-10
Is this what you looking for?

[http://ubuntuforums.org/showthread.php?t=79588&highlight=secure+ftp+server](http://ubuntuforums.org/showthread.php?t=79588&highlight=secure+ftp+server)

---

### Post by billdotson on 2007-05-12
sadly.. no.  I want to setup a sftp server.  Sftp is a part of the openssh-server package.  It is an encrypted ftp-like thing.  Normal FTP doesn't have password and data encryption on uploads/downloads and logins.. and I need encryption.

---

### Post by honeydew on 2007-05-12
all you have todo is add openssh-server then add users...? what exactly is the issue?  once openssh is running you dont have to setup anything else.


sudo apt-get install openssh-server
sudo adduser

---

### Post by billdotson on 2007-05-17
adding users, restrictions to certain folders, upload and/or download restrictions, etc.

---

### Post by fanatik on 2007-05-17
perhaps you shouldn't be using the sftp part of ssh and maybe you should look into something like vsftpd...

---

### Post by Wim Sturkenboom on 2007-05-17
vsftpd will do the trick; other ftp clients might as well. The problem with sftp is that it sounds complicated to jail users to their home directory.

Check Miles Brennan's [Linux Home Server HOWTO Chapter 14 - FTP Server](http://www.brennan.id.au/14-FTP_Server.html) how to get vsftpd secured.

---

