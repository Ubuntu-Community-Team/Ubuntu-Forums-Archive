---
title: "mySQL and Storage"
date: 2008-01-16
forum: General Help
---

### Post by TorchlightJay on 2008-01-16
Hey,

So I am wanting to setup a mysql server. I have one going and I was wondering, is it possible to store files and images or just data? I want to be able to scan documents and business cards and store them in my database and then pull them up as I need them. I didn't know the exact extent to get it to do that. Maybe there is some kind of third party software that can let me do that withthe mySQL backend? Let me know. Thanks.

---

### Post by indytim on 2008-01-16
MySQL will support storing storing binary data in the field type blob.  I have not used this type for data storage personally.

MySQL is a full database server and should not be considered as a simple file system.  In order to use it effectively, you will need a front-end program(s) that talk to the database server.  These front end programs take on many flavors but the generally favored application is PHP as used in web data applications.  This is not a simple drag-n-drop application.

IndyTim

---

### Post by TorchlightJay on 2008-01-16
I figured it wouldn't be simple drag-n-drop, I just wanted a better method of storing images. Any ideas of what kind of php programs I may be able to use on the front-end? I am sure there are a billion and one but maybe someone has experience with one of them. 

If mysql isn't the best option, how about other online storage methods?

---

