---
title: "How open is ubuntu if I perform database programming?"
date: 2016-01-26
forum: General Help
---

### Post by Sherman_Willden on 2016-01-26
I have heard that database programming can open my computer to the world. So how open to the world is Ubuntu if I install a database and perform database programming?

Thank you;

Sherman

---

### Post by 1clue on 2016-01-26
You mean as a security vulnerability?  That depends on what you do and how you do it.  Can you give us a scenario?

What database (mysql, microsoft, oracle...)
What programming languages?
What scenario? (web framework, c/c++ style odbc connection, client-server, will database ports be opened directly to non-localhost clients)

---

### Post by grahammechanical on 2016-01-26
If you allow Ubuntu to connect to the internet, you have opened Ubuntu to the "world." Maybe. Maybe by only a little bit.

If you then open a web browser you are opening Ubuntu to a wider world experience. There is a reason why it is called the world wide web. If you go online to buy something you are connecting to a database running on someone else's computers even if all you are doing is looking at what is for sale.

Ubuntu is no more open to the world, as you put it, then any other OS. I think that you have been misinformed. Installing a database program does not of itself open Ubuntu to the world any more than creating a web site of itself opens Ubuntu to the world.

Where are you going store the created database? On your machine? In the cloud? Are you going to host the database on a hosting service?

Regards.

---

### Post by 1clue on 2016-01-26
I would read these, in this order:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

The last one is a list of security notices for Ubuntu, and it's a moving target.  EVERY operating system and app has something like this, even if most people don't know it.

What I can't link to is best practices for programming, which is a complicated issue even if I knew the information I asked in my first post.

---

### Post by Sherman_Willden on 2016-01-27
Thank you. I am programming for mysql and what concerned my was the ssl that came with mysql. Thank you Sherman

---

