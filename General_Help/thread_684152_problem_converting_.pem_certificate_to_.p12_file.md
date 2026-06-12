---
title: "problem converting .pem certificate to .p12 file"
date: 2008-01-31
forum: General Help
---

### Post by CamranKhan on 2008-01-31
Well I am using OpenSSL and trying to convert a .pem certificate(s) to a .p12 file so I can use it in Windows XP (client). I am using the following command:
 
openssl pkcs12 -export -in winxp.com.pem -inkey winxp.com.key -certfile demoCA/cacert.pem -out winxp.p12
 
I am getting an error, which is as follows:
 
unable to load private key
 
Any suggestions as I am having this problem for the past few days trying to resolve it. I am using Ubuntu 7.10 and I have generated the Certificates in a directory called /var/sslca and I am running the above command from this directory.

Hope to hear from you all soon please urgent attention required!!!!!!!!!

Thanks

Cam

---

### Post by syed mehdi on 2008-02-04
This might be occuring as you are not having the proper version of java installed.
Just install jre 1.4 or later.
append the PATH variable with the path of bin folder in it.
and try this command after that...

Regards
Syed

---

### Post by CamranKhan on 2008-02-06
Thank you for your reply much appreciated.

Does this imply if you are writing the command in Linux command line as though I am using Linux. I assume that the suggested solution by yourself is achieved in Windows XP

---

