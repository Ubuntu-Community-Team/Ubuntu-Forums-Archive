---
title: "make apache2 open index.php not index.html"
date: 2013-07-04
forum: General Help
---

### Post by mick463 on 2013-07-04
Hi i have installed apache2 on ubuntu 12.04. I have also installed wordpress as well all has gone well and i have started wordpress. When i type in [http://localhost](http://localhost) i get the dafault index.html page that comes with apache2. I would like to have the word press page come up in place of this page i have searched the internet for an answer but all say to edit my httpd.conf file but that is empty so i am at a loss. Please help thank you.

---

### Post by davetv on 2013-07-04
try putting the line : 

DirectoryIndex index.php index.html

into that file

---

### Post by davetv on 2013-07-04
try putting the line : 

DirectoryIndex index.php index.html

into that file

---

### Post by SeijiSensei on 2013-07-04
The default Apache configuration on Ubuntu is contained in /etc/apache2/sites-available/default.  You will see an entry that reads "DocumentRoot /var/www".  Change that to point to the directory where the WordPress index.php file resides.  Also replace the reference to /var/www in the corresponding <Directory> statement. Then restart Apache with "sudo service apache2 restart".

The file httpd.conf is deprecated in Ubuntu.  Please read the [Server Guide](https://help.ubuntu.com/lts/serverguide/web-servers.html) for details.

---

### Post by mick463 on 2013-07-04
Thank you for your reply my index.php file that i would like to point to resides in the var/www folder right next to the index.html file. I thought there was a file somewhere that gave a list of the files to try first starting with index.html.
My power cord on my laptop is at work and i have run out of battery so i will try your sugestion tomorow and let you know how i go.

Cheers Mick463

---

### Post by sahabcse on 2013-07-04
Copy the worpress folder in /var/www.
Move the index.html file to another name in /var/www, then type localhost in browser it display the list of directories which in /var/www,
Click worpress for access the same

---

### Post by SeijiSensei on 2013-07-04
> **mick463 said:**
> Thank you for your reply my index.php file that i would like to point to resides in the var/www folder right next to the index.html file. I thought there was a file somewhere that gave a list of the files to try first starting with index.html.

Yes, it is in /etc/apache2/mods-enabled/dir.conf:

```

<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

```

The files are listed in order of preference, so placing index.php at the front of the list will prefer it over an existing index.html in the same directory.

Remember to restart Apache with "sudo service apache2 restart" after making any changes like this.

---

