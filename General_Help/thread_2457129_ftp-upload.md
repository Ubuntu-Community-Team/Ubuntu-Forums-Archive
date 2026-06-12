---
title: "ftp-upload"
date: 2021-01-26
forum: General Help
---

### Post by LaMpiR on 2021-01-26
Hi good people :)

I need a small help in order to resolve a "problem". I have been using the following command to upload a file after compiling it.

ftp-upload -h host.com -u username --password ver_complicated_password --passive -d / file*

But I get this error now:

ftp-upload: can't login to host.com (550 SSL/TLS required on the control channel)


I have changed my hosting and the new one has a bit more strict policy with the ftp.

Consulting the manual for my version 20.04. I have found no mention of being able to use ssl with ftp-upload command.
[http://manpages.ubuntu.com/manpages/focal/man1/ftp-upload.1p.html](http://manpages.ubuntu.com/manpages/focal/man1/ftp-upload.1p.html)

Would appreciate if you could help me out with it.

Best regards

---

### Post by spjackson on 2021-01-26
I'm not sure what your server requires but it looks like sftp or scp might possibly be what you need to use.

---

### Post by LaMpiR on 2021-01-26
It uses SSL certificate.

I don't have ssh access and cannot use sftp or scp with it. Is there anyway to use ftp-upload with SSL? 

I have to use the option for ftp in Filezilla "Require explicit ftp over TLS". So SSL/TSL is a must.

---

