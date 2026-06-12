---
title: "html code in a file"
date: 2008-02-25
forum: General Help
---

### Post by davidtuti on 2008-02-25
Hi,

I would like if it exists a command to can save the html code of a page in a file 

Thanks a lot and sorry for my english

---

### Post by AnRa on 2008-02-25
```
wget http://www.example.com/page.html
```

---

### Post by JimBuntu on 2008-02-25
did you try just right click>view page source>save file as ??

---

### Post by davidtuti on 2008-02-25
I would like to use in a shell-script and I need to use from command-line.

Thanks,

---

### Post by kesman on 2008-02-25
2nd post does the trick.

---

### Post by davidtuti on 2008-02-25
Well I have another problem...

When I do wget [http://webpage.html/pepito.php](http://webpage.html/pepito.php)

The SO create a directory with the name pepito.php with 2 files: robots.txt and pepito.php but I don't find  that I search.

The page need user and password and I don't know if this is the possible reaseon, althouht I save the password and the user in mozilla firefox.

Any help? Thansk a lot and sorry for my english

---

### Post by kesman on 2008-02-26
So you are trying to download the php file?
That's impossible since php translates itself into html according to the programming. The only way you can get the source of a php-script is to download the file via ssh or ftp.

---

### Post by pointone on 2008-02-26
Python + [ClientForm]("http://wwwsearch.sourceforge.net/ClientForm/") would probably do the trick, but it requires a bit of work.

---

