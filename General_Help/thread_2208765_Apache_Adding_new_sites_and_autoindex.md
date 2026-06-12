---
title: "Apache: Adding new sites and autoindex"
date: 2014-03-02
forum: General Help
---

### Post by Daragaard on 2014-03-02
Hello, as a medium user of Ubuntu i have came to the "wall" of my knowledge with this one and i  need help.
I have a Ubuntu 12.04 64bit  install on a VM machine. 
It has a full L.A.M.P server install with all the trimmings, bells and  whistles. (fully updated)
I was running 2 small web sites on the apace and all was well.  Then I had to add a very large directory (12Gb) as a new site and here  is where all the problems starts.
I had to add a new disk on the VM to the Ubuntu and added all the stuff  to the following location /media/warehouse13/books The way the directory is built is like this:
Under /books there are all the letters from A to Z each letter is a  directory. Under each letter there are more directory’s with names starting in that  letter. /books/b/boy-a or /banana and so on.
Under each of those directory’s there are PDF files. So the full path or one of the directory’s will be  /media/warehouse13/books/b/banana/hello.pdf.
  Now I want to add /media/warehouse13/books to the apache2 server as a  website and have it auto-indexed so when you go to  http://<ip>/books you will see all the dir’s/sub-dirs/pdf’s and  download or review them to your leisure.
But I can’t find a way to do this.  I tried to create a logical link from /books to /var/www but I get  “forbidden” error on the web.
I I know I can move the whole default location of the apace to the  var/www/ to /media/warehouse13 but that’s just as bad.  How can I make this work for me? Thank you so much.

I do have root and all the other access to the macnie so that is not the problem.
please assist.

---

### Post by Lars Noodén on 2014-03-02
If you are talking about adding the directories to an existing site, then you can probably do it with [Alias](http://httpd.apache.org/docs/2.4/mod/mod_alias.html#alias) and [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory).  See the Alias link there for an example of using both.

---

### Post by Daragaard on 2014-03-02
no i need to have a link from /media/warehouse13/book in /var/www that will show all the content of /books down to the file level.
and not show me that "forbidden" error all the time.
other then that all is working.
/media/warehouse13/ is a 2nd HDD on that system.

---

### Post by Lars Noodén on 2014-03-02
This should make it look like /media/warehouse13/book is inside /var/www

```

Alias /book /media/warehouse13/book
<Directory /media/warehouse13/book>
 Options Indexes FollowSymLinks
</Directory>

```

The <Directory> directive is there to set the permissions.  The Option "Indexes" will show the files.  The Alias directive is there to give it the illusion of being somewhere it is not.   

Alternately you might be able to symlink it within the file system but you  would still need the <Directory> directive for /media/warehouse13/book to be set in the Apache vhost configuration file.

---

### Post by Daragaard on 2014-03-02
where do i do this command set? inside /var/www? 
and thank you very much.

---

### Post by Lars Noodén on 2014-03-02
It goes inside your virtual host's configuration file.  If you have the default for Ubuntu and have not changed anything it should be /etc/apache2/sites-enabled/000-default.conf

For the changes to take effect, you  have to restart Apache.

```

sudo service apache2 restart

```

Be sure to make a backup copy of the configuration file first before making any changes.

---

### Post by Lars Noodén on 2014-03-02
One thing that can help with debugging if it does not work on the first try is to open a terminal and track the error log real-time as you try accessing the files in the browser.

```
tail -f /var/log/apache2/error.log
```

---

### Post by Daragaard on 2014-03-02
Thank you very very much!!

---

### Post by SeijiSensei on 2014-03-02
You may want to look into Apache's "fancy" [indexing options]("http://httpd.apache.org/docs/2.2/mod/mod_autoindex.htm") and other methods to let users change the sort order.

---

