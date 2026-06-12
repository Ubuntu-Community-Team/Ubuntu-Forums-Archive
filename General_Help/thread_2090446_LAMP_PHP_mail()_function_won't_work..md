---
title: "LAMP PHP mail() function won't work."
date: 2012-12-02
forum: General Help
---

### Post by TheHelpfulOne on 2012-12-02
Hey everyone,

Recently I have installed a LAMP server with tasksel, and it is up and working well.  I am starting to learn PHP via a book Head First PHP and the first lesson is taking user data from a form and emailing it.  So I followed the book's instructions and everything works great except for the emailing part, I just never get the email.

Am I missing something?  Do I need to configure the mail() function in some way?  Any help would be appreciated!

Thanks,
TheHelpfulOne

---

### Post by Sidner on 2012-12-02
> **TheHelpfulOne said:**
> Hey everyone,

Recently I have installed a LAMP server with tasksel, and it is up and working well.  I am starting to learn PHP via a book Head First PHP and the first lesson is taking user data from a form and emailing it.  So I followed the book's instructions and everything works great except for the emailing part, I just never get the email.

Am I missing something?  Do I need to configure the mail() function in some way?  Any help would be appreciated!

Thanks,
TheHelpfulOne

You either need a SMTP server working on your server or use one externaly (with the object's Mail function smtp. search for it :P), like you would use when sending emails from thunderbird through gmail.

---

### Post by TheHelpfulOne on 2012-12-02
You mean like msmtp or postfix?

---

