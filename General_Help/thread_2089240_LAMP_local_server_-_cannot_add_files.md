---
title: "LAMP local server - cannot add files"
date: 2012-11-28
forum: General Help
---

### Post by RebeccaB37 on 2012-11-28
Hello all,

I have been trying to establish a local server using the LAMP instructions here [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It all seems to have gone fine - I have the test "it works!" page, the test.php displays and myphpadmin runs but I cannot get the local host to recognise files I move into the var/www folder using nautilus Localserver it just keeps posting the "it works"

I guess the index.html is not being updated but it really seems like I'm missing a step. This is the first time I've attempted anything like this so advice / ideas would be most welcome!

Thanks for reading!
Rebecca

---

### Post by Lars Noodén on 2012-11-28
If you left the DocumentRoot alone then the files you put in /var/www should show up on your server.  If you open /var/www/index.html with gedit or some other editor, do you see your changes?

---

### Post by Monotoko on 2012-11-28
Do you have the correct permissions to access /var/www ? You don't by default when you install LAMP.

---

### Post by RebeccaB37 on 2012-11-28
Yes I changed the permissions for the folder using chown, i am able to copy files to the location they just don't show in the localhost

I used the default with no modifications.
index.html remains unaltered despite adding folders and files to var/www
just containing the following text:

<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>

---

### Post by Monotoko on 2012-11-28
index.html shouldn't be altered even if you add files/folders to the directory. Can you access the files directly? IE: [http://localhost/randomfile.html](http://localhost/randomfile.html) - if you remove the index.html it should give you a directory listing.

---

### Post by SeijiSensei on 2012-11-28
Rename /var/www/index.html to something like index.old.  Now look at the site again with your browser.  You should see the default Apache directory listing with all your files.

If index.html or index.php exists, that is the only "index" page you can see.  This is generally a good idea since it keeps people from randomly grabbing files out of the website's root directory.  Without an index.* page, Apache will generate a directory listing on its own.

---

### Post by RebeccaB37 on 2012-11-29
Ah I see - A misunderstanding of the function of the index file :s
I have now removed it and all is well!

Thank you all for your help,

Rebecca

---

