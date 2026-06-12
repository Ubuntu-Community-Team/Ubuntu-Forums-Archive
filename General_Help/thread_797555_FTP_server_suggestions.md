---
title: "FTP server suggestions?"
date: 2008-05-17
forum: General Help
---

### Post by Cr0n_J0b on 2008-05-17
I'm looking for an easy to use, secure FTP server.  I tried VSFTP and it didn't seem secure enough.  I don't want to build a CHROOT environment...and I want some simple to use control features.  I really like ProFTPd, but I can't seem to get the darn thing to work.  If anyone has suggestions for another server I will try that, and if not, i'll just go back to proftpd and try to get that running.

thanks

---

### Post by bodhi.zazen on 2008-05-17
I was going to suggest vsftp, it is easy to configure ...

What did you not like about it ?

If you are interested in security, you could also use ssh (scp) or sshfs :

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

---

### Post by Cr0n_J0b on 2008-05-17
VSftp was really easy to setup and it worked out of the box.  The only thing I didn't like is that users could change directories up to the root.  I know that's probably my cinfiguration fault, but I couldn't find a good solution.  As for ssh, that's what I'm using now, but i don't want my users to have shell accounts.

---

### Post by Monicker on 2008-05-17
vsftpd has several options in the config relating to chroot.  I've done in the past and it worked well for me.  Did you look at the chroot_local_user option?


[http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html]("http://www.cyberciti.biz/tips/vsftp-chroot-users-limit-to-only-their-home-directory.html")

---

