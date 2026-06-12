---
title: "How do I get the mysql.h library?"
date: 2005-08-08
forum: General Help
---

### Post by Zifnab on 2005-08-08
I need mysql.h to compile something, but I don't seem to have the file. All my Google searches seem to imply that it just *comes* with mySQL. Well, I definately have mySQL on my Ubuntu box and I definately don't have the file...

What package do I need? Or can I just get it elsewhere?

---

### Post by DJ_Max on 2005-08-08
If you installed MySQL from apt-get, it leaves out certain files & features. I'm not sure as I try to avoid using binaries. But you're probably looking for a dev package.

---

### Post by katu on 2006-04-07
after some searching I found the following:

```

mysql_config --cflags

```

should give you the directory where the mysql.h is installed. In my case this was in
/usr/include/mysql/ 

if this doesn't work, while trying to get this file I installed the following packages:
libmysqlclient12-dev
libsqlplus-dev

I think the second one isn't necessary. To compile programs using mysql you need to add the flags specified by the first command above.

I know this is a terribly old thread, but I couldn't find an answer the question and this one seemed the most relevant. 
cheers,
Katu

---

### Post by lingnoi on 2006-12-15
Sorry for bumping a really old thread but I just wanted to say that this helped me a lot.

Thanks for the info.

=D>

---

