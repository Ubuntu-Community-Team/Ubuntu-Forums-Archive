---
title: "undelete function in ubuntu"
date: 2007-05-02
forum: General Help
---

### Post by chronister on 2007-05-02
Hi all,

I am pretty new to linux in general. I have Ubuntu Breezy Badger installed and need some assistance.

Not paying close enough attention, I dropped a database using PHPMyAdmin when I simply meant to delete a couple tables. Is there any way to recover this databse from the filesystem??

I appreciate any help with my stupidity that you folks can give me, at least in regards to this problem. :)

Thanks,

Nathan

---

### Post by kidders on 2007-05-03
Hi there and welcome,

You ***might*** be able to get the database's underlying files back (assuming the filesystem they were on hasn't already reallocated the disk space), using a forensic data recovery tool. There are a few in the repositories, and elsewhere. To have any hope, you really need to stop using the relevant filesystem _immediately_. Even if you succeeded however, my guess is that the deleted files would not represent a consistent database.

Normally I wouldn't even *attempt* to restore a database after having accidentally done something innocuous like **sudo mv /var/lib/mysql/dbname /tmp** ... let alone **sudo rm -R /var/lib/mysql/dbname** (which is effectively what has happened). The potential for inconsistencies, leading to data loss (or worse ... corruption) would be too great. I fear you'll have an uphill struggle on your hands. :-(

I'm sorry for being so discouraging ... if you absolutely _have_ to have your data back, and you decide to try, [COLOR=Red]nothing would make me happier than being contradicted[/COLOR].

**Edit:**
[SIZE=1] In general terms, it's important to remember never to be more generous than is absolutely necessary, when it comes to permissions and access privileges. Think of it in terms of never doing **chmod 777 ....** when **chmod 644 ....** will do. For MySQL, creating multiple gradated accounts is a good idea. That way, whenever you want to do something that requires elevated privileges, you know you need to be awake (just like when using **sudo**).

As an example, I use MySQL a lot with PHP. My PHP scripts use reasonably unprivileged MySQL accounts, reducing the probability of a serious accident. I also like to impose similar restrictions on _*myself*_, when using phpMyAdmin.

[/SIZE]

---

### Post by chronister on 2007-05-08
Thanks for the input. I have decided to simply recreate the database. It was not a VITAL DB anyway. It simply stores Movie Information about the movies in our library.

I found an IMDB php class that allows me to extract the information that IMDB has about a particular title and modified it so I can add the information to my database. It is a lot faster to simply search the IMDB for a movie and then click a link that I created which initiates a db write or db update query.

So in the end, my movie database is better this way, just sucks that I erased all 200 movies in it. 

But such is life. I figured that I would not have much luck getting the data back as that is a benefit of Linux over Windows. When something is deleted, it is really deleted.

thanks,

Nathan

---

### Post by kidders on 2007-05-09
I'm glad things are back in working order. :-)

> **chronister said:**
> I figured that I would not have much luck getting the data back as that is a benefit of Linux over Windows.Actually, Windows & Linux (along with all other major OSs) handle deletions identically. If you were to delete something today, it's at least *possible* that fragments of data will still be recoverable years from now. (Just something to be aware of, from a privacy perspective.)

Something I forgot to mention in my previous post is that the safest way to protect against nasty accidents in the future might be to gzip an SQL dump of your database periodically (particularly since it's so small), and put it aside somewhere.

---

