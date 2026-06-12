---
title: "Issues with some webhosting"
date: 2014-03-05
forum: General Help
---

### Post by kyle15 on 2014-03-05
Hey guys,

I am fairly new to Linux and am learning as I go. I have just bought a cheap Linux box to mess around with and learn with. 

I am trying to do a few things with it, some basic webhosting is one of those things. I have a webpage that I am trying to host and I can't quite get it to work right. It works fine off my xampp on my home windows computer, but not off of the Linux server. I can access it but things don't load quite right. It is a php with javascript in it and it has to make a connection to a mysql database. I'm not sure if it's something to do with the javascript or if the box just can't make a connection to the database. 

If anyone has any ideas on how to fix this or if you want additional information let me know.

Thanks
Kyle

---

### Post by Habitual on 2014-03-05
So, the first thing to know is the php-based site has a .php file somewhere with mysql credentials in it.
on Wordpress for example, it wp-config.php

Find the file and test the credentials in it like so:
```
mysql -h <HOST> -u <USER> -p <PASSWORD>
```
where [COLOR=#ff0000]**HOST**[/COLOR], [COLOR=#ff0000]**USER**[/COLOR], and [COLOR=#ff0000]**PASSWORD**[/COLOR] are the *values in the site's .php* file with the credentials.

If that doesn't connect, issue this 
```
mysql -u root -p
```, enter the mysql-root-user password and then issue this:
```
grant all privileges on *[COLOR=#ff0000]db_name[/COLOR]*.* to '**[COLOR=#ff0000]user[/COLOR]**'@'127.0.0.1' identified by 'secret_[COLOR=#ff0000]**password**[/COLOR]'; flush privileges;"
```
127.0.0.1 should be correct if the mysql and php-enabled site are on the same host...
using the same [COLOR=#ff0000]**USER**[/COLOR], and [COLOR=#ff0000]**PASSWORD**[/COLOR] as the *values in the site's .php* file with the credentials in that statement.

Try to connect again, using
```
mysql -h <**[COLOR=#ff0000]HOST[/COLOR]**> -u <**[COLOR=#ff0000]USER[/COLOR]**> -p <**[COLOR=#ff0000]PASSWORD[/COLOR]**>
```

hope that helps.

---

### Post by kyle15 on 2014-03-05
Thanks for replying Habitual

So I tried your commands there and it appeared like I didn't have mysql installed. So I did these
```
 $sudo apt-get install mysql-server
 $sudo apt-get install mysql-client 
``` 

And then I retried the 

 ```
    mysql -h <HOST> -u <USER> -p <PASSWORD>  
```

Then it appears to make a connection [http://puu.sh/7ksDb.png](http://puu.sh/7ksDb.png) .

So, I guess this would mean that my server isn't blocked in anyway from reaching the mysql database?

---

### Post by kyle15 on 2014-03-06
Anyone have any other ideas how to figure out what's going on?

---

### Post by jpowers718 on 2014-03-06
Nothing is wrong it's making a connection. 

If you want to connect to mysql from your computer.. Run this command inside the mysql connection.

Pretty much if you see

mysql>

then paste this in, just replace YOUR_IP_ADDRESS_FROM_YOUR_HOME_COMPUTER with your actual ip address.
Also you might have to replace root with your mysql username (but most likely it's already root).

```

[COLOR=#00008B]GRANT[/COLOR] [COLOR=#00008B]ALL[/COLOR] PRIVILEGES [COLOR=#00008B]ON[/COLOR] *.* [COLOR=#00008B]TO[/COLOR]  [COLOR=#800000]'root'[/COLOR]@[COLOR=#800000]'YOUR_IP_ADDRESS_FROM_YOUR_HOME_COMPUTER'[/COLOR]  IDENTIFIED  [COLOR=#00008B]BY[/COLOR]  [COLOR=#800000]'PASSWORD'[/COLOR];

```

After that command above is ran successfully.. run this command to save it.

```

FLUSH PRIVILEGES;

```

It should say this below twice (for each of  the commands) if it's successfully done.
```

Query OK, [COLOR=#800000]0[/COLOR] [COLOR=#00008B]rows[/COLOR] affected ([COLOR=#800000]0.27[/COLOR] sec)

```

---

### Post by kyle15 on 2014-03-06
I personally don't need to make a connection the the mysql it's the PHP webpage that needs to.

---

### Post by jpowers718 on 2014-03-06
PHP page will have no problem since it runs on the same server as the mysql you just need to download some simple mysql php examples and 
edit the php page (all of them are different) usually in a file like config.php the information below
server to localhost 
username to root
password to your password

and look at the errors or whatever that's it.


Make a new php file call it like test.php and inside put this 

```

<?php echo phpinfo(); ?>

```

and post that here.. people might help you more if you post that.. it has all the PHP information that PHP has installed etc..

---

### Post by Iowan on 2014-03-06
What is (or isn't) going on?  You can connect via the mysql console. Does SHOW DATABASES  reveal your database?
Is your HTML showing?
Does a phpinfo.php script work (dump the server's configuration)?

(WOW, I must type REALLY slow)

---

### Post by kyle15 on 2014-03-06
I'll give you guys the whole rundown of what's going on. It's a web based admin map for a game server.

It has a config.php with database information, the database is not local to the server the website is on.

The website works properly (exact same files, not just database info) off of my xampp server running off my computer.

When I go to the website the image of the map loads up, but none of the live tracking loads up, which is why I was wondering if for some reason the connection is blocked. 

Since then as Habitual guided me through, I made a connection to the database (Which isn't local) so I know my box can make a connection to the database.

---

### Post by kyle15 on 2014-03-06
Alright, after doing some research here. It looks like I might not have PHP enabled or installed (Whichever makes more sense). I made a phpinfo.php and it just wants to download rather than display it. Did some googling on that and people say that's usually due to PHP not being enabled.

Now I need to figure out how to do that. Off to google I go.

---

### Post by kyle15 on 2014-03-06
Got php installed, installed a bunch of extra modules for it that were recommended, restarted apache server. Voila, all is working.

Thank you guys for your assistance.

I'm sure I'll be around as most of linux/webhosting is new to me.

---

### Post by jpowers718 on 2014-03-06
It's extremely easy to install PHP/MySQL etc.. best way is to go to youtube instead like

[https://www.youtube.com/watch?v=KHHXrdb4EKk](https://www.youtube.com/watch?v=KHHXrdb4EKk)
^ Above one has good music

[https://www.youtube.com/watch?v=ioqa-ZT-WSg](https://www.youtube.com/watch?v=ioqa-ZT-WSg)
^ this one is for ubuntu

---

### Post by Habitual on 2014-03-07
install php-mysql

---

