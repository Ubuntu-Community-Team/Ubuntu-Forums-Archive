---
title: "Ajaxterm and Apache2"
date: 2013-01-05
forum: General Help
---

### Post by iclestu on 2013-01-05
Hey folks,

I have been trying to set up Ajaxterm to enable me to ssh into my home pc from a browser but have hit an issue.

I have been following this help doc for ajaxterm:

[https://help.ubuntu.com/community/AjaxTerm](https://help.ubuntu.com/community/AjaxTerm)

and these ones for ssl/apache:

[https://help.ubuntu.com/10.04/serverguide/httpd.html](https://help.ubuntu.com/10.04/serverguide/httpd.html)
[https://help.ubuntu.com/11.10/serverguide/certificates-and-security.html](https://help.ubuntu.com/11.10/serverguide/certificates-and-security.html)

Everything seemed to have went fine (no error messages or anything and can access ajaxterm ok LOCALLY) and I have set up port forwarding for 443 on my modem.

I can reach the apache2 server from an external browser but it does not seem to accept the username and password I supplied when with these commands from the guide:

```
sudo mkdir /srv/ajaxterm 
``` 
```
sudo htpasswd -bc /srv/ajaxterm/.htpasswd [user] [pass]
```(I have, of course, double checked the details, etc)

It just keeps popping up the user/passwd prompt.

Anyone got any ideas what i'm missing?

---

### Post by iclestu on 2013-01-05
Forgive the bumping but has anyone got any idea?

---

### Post by iclestu on 2013-01-05
been googling this all day without success. Can anyone help?

---

