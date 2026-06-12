---
title: "simple assets install problem"
date: 2008-01-10
forum: General Help
---

### Post by strip21 on 2008-01-10
i am trying to get simple assets working on ubuntu 7.10. 

[http://sourceforge.net/projects/simpleassets/](http://sourceforge.net/projects/simpleassets/)

i have downloaded this and put this in the webroot. when i open the directory all i get is 

**"We have not detected a database with valid permissions. To ensure a smooth install, please make sure you have MySQL Server running on port 3306 on the same server as this software. Also ensure you have given write permissions to user account 'root' @ localhost."**

I have got installed and working.....

apache2
php5
mysql 5
Joomla 1.5
Sugar 5
dotproject 2.2

Now when i looked at what it needs it said that i need php4. I have asked on there web but there hs been no reply as yet. 
I have setup a DB using the 

[B]mysql -uroot -p simpleassets
simpleassets < /ver/www/simpleassets/simpleassets.sql
use simpleassets[/B]

i have made the /var/www/simpleassets open to everybody (im using root on the test system), but i still getting this message. 

Can anyone help out with this.

---

### Post by Hayke on 2008-01-12
Simple Assets works like a charm here...

I had to edit config.php to set the right password for mysql. See the README-file that comes with Simple Assets.

After editing config.php, it works like a charm.

(by the way: I didn't know the application, but I'm impressed!)

---

