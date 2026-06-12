---
title: "MySQL vs. Postgre SQL"
date: 2007-12-05
forum: General Help
---

### Post by WIGGMPk on 2007-12-05
Not sure where this should go. So I decided to just throw it in general.

MySQL vs Postgre SQL

What are the pro's/con's over each other?

Is there a need for both?

If running 2 completely different application that require DB's, is it a good idea to use 2 different applications for those DB's?

Or can one just create 2 different DB's under one app (IE: MySQL)??

I know that you can create multi DB's with the same app, but I installed both LAMP and Postgre SQL without thinking about it. Also, im a bit new so thought I would install everything lol.

But, im just not sure as to the need of both DB's. I have a mail server using Postgre SQL and I also have an Apache2 website which im soon going to incorporate a phpbb2 forums into the site and use MySQL for that.

Just thought I would get more info on any pro's/con's on my setup.

Thanks in advance.

---

### Post by ccprog on 2007-12-05
The quick answer is: MySQL is good if you only want a DB delivering data to an application, without much considerations about security. If things like concurrent writing, connecting of multiple clients over a network, or transaction policies are an issue, DBs like Postgres or Firebird are much better suited.

That is why a lot of Web content managment systems, or Apache, use MySQL. Its not like you have hundreds of users entering data at the same time, or critical financial records. I would even think that its capabilities suffice for the mail server.

The longer answer is that you can combine MySQL with several storage backend engines. Those may differ widely in their capabilities. Some have safe transactions, some have not. Documentation is here: [http://dev.mysql.com/doc/refman/6.0/en/storage-engine-overview.html](http://dev.mysql.com/doc/refman/6.0/en/storage-engine-overview.html)

---

### Post by WIGGMPk on 2007-12-06
Thanks for the reply..

Needed a second mind to shed some light on the situation. I appreciate the info link.

---

