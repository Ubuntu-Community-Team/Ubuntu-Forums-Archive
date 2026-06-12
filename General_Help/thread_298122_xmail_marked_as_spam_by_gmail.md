---
title: "xmail marked as spam by gmail"
date: 2006-11-12
forum: General Help
---

### Post by jmvidalvia on 2006-11-12
I am sending mails using the console but, when being received, gmail considers they are spam.
I supose the reason is that sender appears as "user@ubuntu", instead as "user@domain.com".
Does anyone know how to change the sender identification?
Thanks a lot!

---

### Post by jmvidalvia on 2006-11-12
I solved it by myself.
I edit /etc/postfix/main.cf end modify the hostname
then I typed postfix reload
I add that domain to my contacts in Gmail
Ready!

---

