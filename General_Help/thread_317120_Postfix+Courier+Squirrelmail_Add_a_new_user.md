---
title: "Postfix+Courier+Squirrelmail: Add a new user?"
date: 2006-12-11
forum: General Help
---

### Post by Airjoe on 2006-12-11
Hi,
I'm trying to create a new e-mail address on my server. I already have postfix, courier, and squirrelmail set up and running fine for my username. I did:

useradd pmac
passwd pmac
cp -r /etc/skel/Maildir /home/pmac/
chown -R pmac /home/pmac/Maildir
chmod -R 700 /home/pmac/Maildir

That's what I did when setting up courier with my existing username (except the useradd/passwd, of course).

However, when I go to login to squirrelmail with this user/passwd combonation, it says:
ERROR: Connection dropped by IMAP server.


How do I create a new e-mail address? Thanks!

Also, how do I make a "wildcard" e-mail address, so that if someone sends mail to [email]something@mydomain.com[/email], and there is no "something", it goes into my own inbox?

Thanks!

---

### Post by Airjoe on 2006-12-13
Any help? Thanks!

---

### Post by Airjoe on 2006-12-14
Please? Anyone?

Thanks!

---

### Post by Airjoe on 2006-12-18
Is this really all that hard?

---

### Post by Airjoe on 2006-12-21
**Anything?**

---

