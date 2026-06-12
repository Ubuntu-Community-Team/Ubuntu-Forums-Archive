---
title: "Wildcard SSL Certificate Installiton"
date: 2007-07-31
forum: General Help
---

### Post by imverk on 2007-07-31
Ok i've been messing with this for a while and am stummped. I bought  a wildcard certificate from network solutions after creating the .crt and .key and sent them to network solution, for a web my website [www.gomylocal.com](www.gomylocal.com). Network Solutions has sent me back the following files.

   AddTrustExternalCARoot.crt
   UTNAddTrustServer_CA.crt
   NetworkSolutions_CA.crt
    STAR.GOMYLOCAL.COM.crt 

and another file not sure what it for
    Apache_Plesk_Install.txt

 I can not figure out how to get this to work(being this is my first time). I am running the latest version of XAMPP 1.6.3 
I've looked at the httpd.conf and found the pointer to
 /opt/lampp/etc/extra/httpd-ssl.conf

I've also been looking at the forums, but i think i'm so new I cant grasp it.

I'm just not sure what files to point to etc..? or what to do next...? Any help would be great?

Thanks

---

### Post by kidders on 2007-08-01
Hi there,

It looks as though you have SSL working already, so assuming you're not doing any virtual hosting, the next step is to replace Apache's demo certificate/etc. with your own, and restart Apache.

Hopefully, you will find that Apache starts asking you for your private keyphrase on startup. Exactly what to do about that is up to you, but I wouldn't recommend leaving that arrangement as is (since your web server would no longer be able to boot successfully without you standing over it).

There's an endless collection of documentation & HOWTOs on this subject though, so I would suggest starting there.

---

