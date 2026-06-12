---
title: "MySql Ubuntu question"
date: 2008-01-04
forum: General Help
---

### Post by asnd16 on 2008-01-04
just learning PHP and MySQL what package would be good for ubuntu? 
Linux non-rpm or Linux RPM package?

[http://dev.mysql.com/downloads/mysql/6.0.html](http://dev.mysql.com/downloads/mysql/6.0.html)

---

### Post by cheahk on 2008-01-04
Neither of the above.

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

-K

---

### Post by gary0 on 2008-01-04
Hi, go in to synaptic package manager, select Edit --> Mark packages by task, and select LAMP. This will install everything you need.

Hope this helps.
Gary.

---

### Post by asnd16 on 2008-01-05
what about for gusty?  I see no install for gusty and in my synaptic package manager it is not visable

---

### Post by gary0 on 2008-01-06
What's not visible? The Edit menu? I am talking about Gutsy.

Gary.

---

### Post by indytim on 2008-01-06
1.  Invoke the terminal.
2.  $sudo tasksel
3.  Make you selection.  Sit back and enjoy the world of automation.

IndyTim

---

### Post by asnd16 on 2008-01-06
> **asnd16 said:**
> what about for gusty?  I see no install for gusty and in my synaptic package manager it is not visable

the package is not listed that is what I am talking about. . .

---

### Post by gary0 on 2008-01-06
Oh, ok. Have you updated your sources lately? sudo apt-get update, and did you try the tasksel option as mentioned by indytim?

Gary.

---

