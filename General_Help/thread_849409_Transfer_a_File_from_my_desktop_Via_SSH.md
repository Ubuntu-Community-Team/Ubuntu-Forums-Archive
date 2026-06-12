---
title: "Transfer a File from my desktop Via SSH"
date: 2008-07-04
forum: General Help
---

### Post by dethredic on 2008-07-04
So I have a .htpasswd file on my desktop and I need to transfer it to /var/secure on my server (both comps running Ubuntu). I have done stuff via ssh before, but not transferring files. Also in the future I might need to transfer folders.

---

### Post by mzhb@mac.com on 2008-07-04
use 'scp' command
e.g

  scp -r ~/fileToCopy  [email]yourname@server.com[/email]:~/filefolder

---

### Post by dethredic on 2008-07-04
> **mzhb@mac.com said:**
> use 'scp' command
e.g

  scp -r ~/fileToCopy  [email]yourname@server.com[/email]:~/filefolder

> scp -r /home/phil/Desktop/.htpasswd root@192.168.1.137:/var/secure

This worked great. Thanks man. Does this also work for whole folders?

---

### Post by mzhb@mac.com on 2008-07-04
> **dethredic said:**
> This worked great. Thanks man. Does this also work for whole folders?

yes, -r here stands for recursive copy all the subfolders

---

### Post by Typhoeus on 2008-07-05
Hi all, just a quicky, how do i scp using a non standard port.

cheers

its ok i sussed it. I added -P (capital p) and the port number after the scp command

---

### Post by GregoryDWeed on 2008-07-05
> **Typhoeus said:**
> Hi all, just a quicky, how do i scp using a non standard port.

cheers

you'd use an uppercase P like so 

> scp -P yourport -r ~/fileToCopy [email]yourname@server.com[/email]:~/filefolder

---

### Post by ixus_123 on 2008-07-05
While we are making progress here,
does anyone know how (if I can) secure copy from my local machine to a privileged location on m server if root logins over SSH are disabled?

Currently I copy to a users home directory and then log in as them, SU and then copy to /var

---

### Post by kevdog on 2008-07-05
Or you could use sftp -- its like ftp -- same commands - get/put, but works only over ssh.

---

