---
title: "php"
date: 2015-04-15
forum: General Help
---

### Post by yazvoprosywebw on 2015-04-15
Hell0


Set php:


sudo apt-get install php5-cli
sudo apt-get install php5-cgi
sudo apt-get install libapache2-mod-php5
sudo a2enmod php5



but when I try to run the file test.php with content:


<?php echo '<p>Hello World</p>'; ?> 


file does not run in a browser, and offer to save.

How to run the test.php ?
[COLOR=#000000][FONT=Ubuntu Beta]
[/FONT][/COLOR]

---

### Post by yancek on 2015-04-15
That would be expected if you tried to open it in the file manager by clicking the icon for the file.  If you open it with a web browser, is it on a local machine?  Open your browser and in the address bar enter [http://localhost/test.php](http://localhost/test.php), is that  what you do?  Do you have the file in /var/www/html?

---

### Post by yazvoprosywebw on 2015-04-15
I manage to run test.php after moving to the folder /var/www/html, using:


sudo nautilus


How to run a file test.php from the desktop /home/ ?

---

### Post by dragonfly41 on 2015-04-16
It is not the usual approach to place php files on ~/Desktop to be run.
But if you must here are some ways (if you want the output to be rendered in browser).

Create folder (say www/html/) on Desktop (reflecting the apache2 structure you have just tested).

Use php _built in server_ to serve from that Desktop directory.

Place a test file phpinfo.php in Desktop/www/html/ folder

```

<?php phpinfo(); ?>

```

You can create a launcher to run this command .. (you can change the listening port) .. or just use command terminal

php -S localhost:8000 -t ~/Desktop/www/html/

Now go to your browser .. [http://localhost:8000/phpinfo.php](http://localhost:8000/phpinfo.php)

So you can reflect the apache2 /var/www/html/ structure .. but on your Desktop.

...

Another way would be to create an apache virtualhost conf file in /etc/apache2/sites-available/ to map to ~/Desktop/www/html/ as DocumentRoot.

...

Another approach would be to embed your php script in a python script (which I've used for a Desktop app). That is a hybrid approach.   But you then need to learn python and php.

The Ubuntu Quickly package allows Desktop apps to be rapidly built using say webkit browser.

...

---

### Post by SeijiSensei on 2015-04-16
If you want to run a PHP script from the command prompt, use a "hash-bang" at the top like this:
```

#!/usr/bin/php5 -q
<?php
[your code here]
?>

```
Mark the script executable with "chmod a+x /path/to/your/script". 

You should be able to create a desktop launcher that points to your script.

---

