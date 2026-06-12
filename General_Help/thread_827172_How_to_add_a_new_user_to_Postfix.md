---
title: "How to add a new user to Postfix?"
date: 2008-06-12
forum: General Help
---

### Post by albertgrain on 2008-06-12
Dear all,

I have searched again and agian with the simple question:
How can I add a new user to my Postfix. The Postfix is running just fine WITHOUT a user...
But I got not answer...

I just want to setup up an account (best if it is not the Ubuntu user, and can just send email and block any receiving.)

Help!

---

### Post by brian_p on 2008-06-12
> **albertgrain said:**
> Dear all,

I have searched again and agian with the simple question:
How can I add a new user to my Postfix. The Postfix is running just fine WITHOUT a user...
But I got not answer...

I just want to setup up an account (best if it is not the Ubuntu user, and can just send email and block any receiving.)

Help!

If I understand you correctly: postfix accepts and delivers mail. It does not need to have a user added to it. It sets up accounts for all users by itself in /var/mail.

---

### Post by albertgrain on 2008-06-16
> **brian_p said:**
> If I understand you correctly: postfix accepts and delivers mail. It does not need to have a user added to it. It sets up accounts for all users by itself in /var/mail.

Thank you for your reply.

I tried to use Outlook to receive the email.

Establishing network connection ... done,
Try to find the SMTP server ... done,
Try to find the POP3 server ... done,
Logon to the POP3 server...

I used all the accounts (include the account that can use SUDO) that had already created in the Ubuntu to test the connection but none is sucessful.

I have freshly installed the Ubuntu server with mail+LAMP+SSH, and made no change to the system except use adduser to add a few account to Ubuntu.

Thank you !

---

### Post by albertgrain on 2008-06-19
I got the answer.
The connection type of POP3 should be secured type.

---

