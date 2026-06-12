---
title: "PHP and mail"
date: 2007-02-02
forum: General Help
---

### Post by tinman on 2007-02-02
Hi There :) 

I am trying to get my php scripts to send mail and at the moment, it isnt working. :(  My 

question is do I have to install a mail server or is there a way to use my existing 

email to be forwarded to by php? I know you have to edit php.ini for a mail server like 

sendmail, but can I get around this??  Thanks in advance ):P

---

### Post by lamego on 2007-02-02
Your ISP must provide an SMTP server, the same one you use for your regular email client.
Just edit /etc/php5/apache2/php.ini and use it.

---

### Post by tinman on 2007-02-02
Thanks for the quick response lamego, but where in the php.ini file do I put my ISP's smtp

server? I thought that only worked for windoze and you had to enter the path to you mail 

"server" for linux? I did put my ISPs mail server on the send mail option in the php.ini file but 

that didnt work either. :confused:

---

