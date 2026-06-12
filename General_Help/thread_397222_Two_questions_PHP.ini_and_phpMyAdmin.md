---
title: "Two questions: PHP.ini and phpMyAdmin?"
date: 2007-03-30
forum: General Help
---

### Post by theaverageidiot on 2007-03-30
Two questions:

#1: I need to change some things in my php.ini but I don't know where to find it :D. Can someone tell me where? (I have PHP5 installed)

#2: I just installed phpMyAdmin. I went to it ([http://localhost/phpmyadmin](http://localhost/phpmyadmin)) and it's asking for a username and password. What do I enter? I never set a password. And more importantly, once I figure out what the default password is, how do I change it to my own username/password?

Thank you! :)

---

### Post by theaverageidiot on 2007-03-30
bump

---

### Post by acormack on 2007-03-30
1)

sudo find / -name php.ini

2)

Try this page:

[http://www.phpmyadmin.net/documentation/#faq](http://www.phpmyadmin.net/documentation/#faq)



Alec

---

### Post by theaverageidiot on 2007-03-30
Can't find anything in that link about what I'm looking for :(.

---

### Post by acormack on 2007-03-30
Are you sure mysql is running and you have created a mysql root password?

sudo /etc/init.d/mysql status

If so then login using the mysql credentials.

If not then try 

mysqladmin -u root password "mypassword"

you may need to restart mysql

sudo /etc/init.d/mysql restart



Alec

---

### Post by theaverageidiot on 2007-03-30
Okay that helped me figure it out. I've set the pass now thanks :)

---

