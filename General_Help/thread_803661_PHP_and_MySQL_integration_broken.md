---
title: "PHP and MySQL integration broken"
date: 2008-05-22
forum: General Help
---

### Post by Boyohazard on 2008-05-22
Since upgrading to Hardy I haven't been able to get PHP and Mysql to work together on Apache.

I have removed and re-installed everything; apache 2, mysql, php, phpmyadmin, php5-mysql and still no luck. No matter what php package I try to run that requires MySQL I keep getting an error.
e.g. phpmyadmin: "cannot load mysql extension. please check your php configuration"
wordpress: "Your PHP installation appears to be missing the MySQL which is required for WordPress."

MySQL is running fine, I can access it via the terminal, create DB's, tables, users etc

php is installed fine; apache processes .php files correctly

I have modified the php.ini (all 3 copies that I could find!) to point at 3 different directories containing the mysql.so (that I could find)

Anyone able to offer help/suggestions please?

---

### Post by Boyohazard on 2008-05-27
4 days on and still no luck, anyone with any insights?

---

### Post by alinsenb on 2008-06-01
I'm gonna "second" the problem...  I've been using Wordpress for years now, and just did a fresh install of Hardy on my server box, with the newest PHP and MySQL files set up.  Wordpress can't connect and/or see my database, despite having the correct config files set up.

So yeah, you aren't alone!  I'll keep working on it, too, but it certainly seems like a problem...

---

