---
title: "Evolution problems..."
date: 2007-05-11
forum: General Help
---

### Post by daltocli on 2007-05-11
I recently installed Feisty, and I must say I am impressed so far!

Currently, though, I am encountering problems with Evolution + IMAP.  The username seems to be stuck as <email address>@<imap server address>, when my login address is my email address only, which I have set the username.

How do I resolve this issue?

---

### Post by .tommie on 2007-06-05
Good question, having the same issue with IMAP authentication in Evolution.

Evolution logs in with <email address>@<imap server address>, causing a failed login. This shouldn't be happening, because Evolution should login with <email address>.

Any idea's?

---

### Post by Big_Croc7 on 2007-06-05
Has this changed from edgy/dapper?  It works fine for me, but I'm not using feisty.  Are you wanting to log in with an email address like fred@ bloggs.com, where the server is mail.com? (I.e. the server address is different to your email domian?)

---

### Post by .tommie on 2007-06-05
Yes, that's the case.

The server address uses the hosting company's domain, but the login they've supplied is my own domainname.

What is your situation? Is it similar?

---

### Post by Big_Croc7 on 2007-06-05
My situation's similar, but I've just checked and (using the example before) I just have my username set to 'fred'.

Try that maybe, but if it dosen't work I don't know anything else to suggest.

---

### Post by .tommie on 2007-06-05
Thanks Big_Croc7, I've got it working.

When authenticating with <email address>, you should use the identical domain name from <email address> for the server address, instead of the hosting company's domain name.

My best regards!

---

### Post by Big_Croc7 on 2007-06-05
Cool, glad it works!

---

