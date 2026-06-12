---
title: "vsftp doesnt have primissions"
date: 2005-07-31
forum: General Help
---

### Post by HAMM3R on 2005-07-31
Hey.

I installed vsftpd.  I have a directory called /home/haycustoms/public_html.  This is a web directory.   Now, during an ftp session, i CAN edit the dir /home/haycustoms, but not the public_html folder.  I DID mkdir public_html as the user haycustoms, so i am able to edit that folder from the ssh.  I just think vsftpd doesnt have primisions.   So how can i configure vsftpd to be able to edit any folder, as log as they are logged into the ftp as the user who owns the folder?  (like sftp) Any and all help is much appreciated!

Thanks,

Austin

---

### Post by frodon on 2005-07-31
Sorry, I haven't any knowledge with vsftp but I'm used to work with proftpd which i find more secure. So if you want to try proftpd have a look to my [How to](http://www.ubuntuforums.org/showthread.php?t=51611), there is also a lot of documentation about it on internet.
Do you know if vsftp is based on system rights or if vsftp can overwrite the system rights ? proftpd is based on system rights and generally you have this kind of problems when your folder have not the good system rights.

good luck  ;-)

---

### Post by HAMM3R on 2005-07-31
[QUOTE=frodon]Sorry, I haven't any knowledge with vsftp but I'm used to work with proftpd which i find more secure. So if you want to try proftpd have a look to my [How to](http://www.ubuntuforums.org/showthread.php?t=51611), there is also a lot of documentation about it on internet.
Do you know if vsftp is based on system rights or if vsftp can overwrite the system rights ? proftpd is based on system rights and generally you have this kind of problems when your folder have not the good system rights.

good luck  ;-)[/QUOTE]
 I need to use vsftpd for various reasons.   I really have no knoledge of it either, so i dont know about the rights and such.  Im lost....

---

