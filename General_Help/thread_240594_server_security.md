---
title: "server security"
date: 2006-08-21
forum: General Help
---

### Post by compwiz18 on 2006-08-21
I just installed Ubuntu on a computer that is DMZ'ed to the internet running apache2, mysql, php5, and proftpd, as well as the remote desktop thing that can be turned on under preferences.  Is there anything special I need to do to keep from getting my server hacked?

---

### Post by Sam on 2006-08-21
Use strong passwords, avoid ftp and use ssh instead, disable root acces in ssh, enable certificate authentication in ssh, disable remote MySQL access, are a good beginning. You can also use an another port for ssh to prevent script kiddies attacking your computer, and if possible, use https for any page that require authentication.

---

### Post by compwiz18 on 2006-08-21
What is the difference between SSH and FTP?

---

### Post by Sam on 2006-08-21
Found in the web:
> FTP is a (separate, obsolete) protocol for file transfer. It has no encryption, and cannot unless the client and server agree beforehand on a separate encryption layer -- in which case the encryption has nothing to do with FTP.

SSH is a protocol for encrypted network sessions. The common use for this is remote command shells, but a file transfer can be done using (among others) SFTP, a command protocol carried over SSH and designed to look like FTP.
You can do every ftp tasks with ssh, but everything is encrypted.

You can also mount a remote ssh directory to your filesystem, then copy/paste/edit files in that directory as you would do with your files on your harddisk.

The point with ssh is: security


Google a bit or check Wikipedia, there is a LOT of informations about this.

---

### Post by compwiz18 on 2006-08-21
Awesome, I'll do that tomorrow.  Thank you for your help.

---

