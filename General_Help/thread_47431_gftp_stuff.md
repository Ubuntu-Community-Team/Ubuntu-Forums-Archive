---
title: "gftp stuff"
date: 2005-07-08
forum: General Help
---

### Post by ishkabob on 2005-07-08
Hey all, I'm trying to setup a user account for a friend so that can get files from me via ssh.  I created their home directory and symlinked the folder that they want access to.  Then i used useradd to give them an account.  Everything works fine from the shell, they can scp anything they want, however, If I try and use gftp, it says that the permission is denied.  My friend can browse all the files with gftp, do I need to change the files permissions do something more than just read access? Any help is greatly appreciated thanks!

---

### Post by ishkabob on 2005-07-08
quick update, i tried changing the permissions so that users could execute the files, this doesn't work either.

---

### Post by ishkabob on 2005-07-08
Another update.  I think the problem with gftp is that it uses the Open command as opposed to the Get command.  Anyone know what I'm talking about ?

---

### Post by ishkabob on 2005-07-12
Ok so apparently no one knows what I'm talking about, but the last bit of information I have is this.  I can use gftp and my friend's user account to connect to my machine from a Debian machine.  However, when I use to Ubuntu to connect to my machine (an ubuntu machine), I cannot get files.  There must be some configuration difference between Ubuntu and Debian that allows Debian users to use gftp.  Any help is appreciated.

---

