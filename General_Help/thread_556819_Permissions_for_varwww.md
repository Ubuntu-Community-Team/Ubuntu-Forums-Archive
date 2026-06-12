---
title: "Permissions for var/www"
date: 2007-09-21
forum: General Help
---

### Post by smQQkin on 2007-09-21
I am trying to setup up a testing server. However, when I try to add files to var/www it says I don't  have permissions. I have read online about using gksudo nautilus, but I am unsure what to set the permissions to. Any ideas? Should I set the "var" folder to have read/write access?

---

### Post by Sayers on 2007-09-21
no make /var/www chmod 777 which would work. Anybody could write there but... it'd work?

---

### Post by smQQkin on 2007-09-21
> **Sayers said:**
> no make /var/www chmod 777 which would work. Anybody could write there but... it'd work?

Ok... How would I do that? sudo chmod 777?

---

### Post by robotrodeo on 2007-10-12
i have the same question. i am new to linux and have tried the command sudo chmod 755 /var/www/ and it didn't return an error, but it didn't change the permissions either. i am stumped

---

### Post by nikhilk on 2007-10-12
Probably not a very good idea to set open permissions on your document root.
You should run ```
chmod -R 755 /var/www
```

---

### Post by the_nite_owl on 2007-10-12
> **smQQkin said:**
> I am trying to setup up a testing server. However, when I try to add files to var/www it says I don't  have permissions. I have read online about using gksudo nautilus, but I am unsure what to set the permissions to. Any ideas? Should I set the "var" folder to have read/write access?

You might be better off setting your WWW folder up for FTP then using FTP to control access to the folders.
Every time you made updates to files you would have to FTP them to web server folders but it would be secure without opening up access to the world.  You would also be able to make changes to the files from other locations as long as your web server is exposed to the network/internet.

---

### Post by az on 2007-10-12
No.

Do not change the ownership of anything in /var  For security reasons, you don't want just anyone to be able to write there.

Use sudo to copy files there.  Even apache should not be able to write to the document root folder - just read.

---

