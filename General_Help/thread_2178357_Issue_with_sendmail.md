---
title: "Issue with sendmail"
date: 2013-10-03
forum: General Help
---

### Post by andrew47 on 2013-10-03
So, I've been having problems with sendmail for a couple days now. Finally I got it to work but it still shows the error message, "Could not execute: /usr/sbin/sendmail". Even though it works and the message gets sent, it shows this error. So my question is, how can I hide this error? Thank you.

---

### Post by enterdavertex on 2013-10-04
What are the rights about this file ? 
Try this in a terminal :  _***ls -l /usr/sbin/sendmail***_
The rights (First Collums result) should be looking like this: [U][B]lrwxrwxrwx

[/B][/U]Otherwise do this command : **sudo chmod 777 /usr/sbin/sendmail**

---

