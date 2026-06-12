---
title: "Enabling FTP access to my Edgy machine?"
date: 2007-08-29
forum: General Help
---

### Post by william_hunter on 2007-08-29
Hey all. I am trying to figure out how to enable secure FTP access to my Edgy machine, both inside my LAN and from outside my WAN by a limited number of users. I have searched around, and found lots of parts of info, but nothing walking me through it, and I am stumped, as well as tired because school is starting back up. I would like to be able to access my files from school so I don't have to save everything on a thumbdrive every night while I lesson plan, you know?

---

### Post by kesman on 2007-08-30
first you got to install an ftp-server and then open the needed ports, 21-22 from your firewall in order to access the server from outside your home lan.

---

### Post by sumguy231 on 2007-08-30
I recommend proftpd for that, by the way. Documentation is on the website:
[http://www.proftpd.org/](http://www.proftpd.org/)

---

### Post by william_hunter on 2007-09-03
Ah, here I thought I already had an FTP server installed. I will do that now.

---

### Post by scxtt on 2007-09-03
if you want "secure" FTP why not just make use of SSH's sftp (not surprisingly, Secure FTP) ... if you have an OpenSSH server running, you have sftp ...

i'm not saying proftpd can't be "secure", it's just more work that you need ...

---

### Post by william_hunter on 2007-09-05
I do not currently have SSH server on my machine. I never really needed it I guess. I did install proftpd and it made a giant mess of my file system which took a while to repair. Not sure exactly what happened, but its ok now. I somehow doubt that is the intended result of installing it](*,)

---

### Post by scxtt on 2007-09-05
it's really as simple as **sudo aptitude install openssh-server** ... then,

sftp $USER@<somehostname>.{com/net/org}

and you just create normal Linux users to use the service ...

---

