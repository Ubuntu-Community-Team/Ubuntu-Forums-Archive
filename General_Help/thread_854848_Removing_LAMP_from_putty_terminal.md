---
title: "Removing LAMP from putty terminal"
date: 2008-07-09
forum: General Help
---

### Post by Jimbo13 on 2008-07-09
Is there anyway I can remove apache, mysql and php5 through putty?

I went through and ran 
[B]
sudo rm -r /etc/php5/
sudo rm -r /etc/mysql
sudo rm -r /etc/apache2

[/B]

They are all gone but when I go to **sudo apt-get install apache2** they are still installed.

---

### Post by sonofusion82 on 2008-07-09
if you are trying to remove them, i suppose you should try:
sudo apt-get remove apache2 php5 mysql

---

