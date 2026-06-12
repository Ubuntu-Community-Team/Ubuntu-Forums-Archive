---
title: "Easy web based mysql frontend"
date: 2013-01-08
forum: General Help
---

### Post by abandonedthe_mulletator on 2013-01-08
Hi,

I'm looking for an easy to use mysql frontend that can be accessed via web browser.  I want something basic that allows users to input, change and view data in the database.

I'm quite new at working with databases so I need something easy.

I tried Vfront ([vfront.org]("http://www.vfront.org/")).  Its really good but I am having some trouble getting it to behave the way I want.  There is some support but its all in Italian.  

I have phpmyadmin for administration but I don't want users to access all the databases or any other admin stuff.  Also I like the form style interface that Vfront offers, kinda like Microsoft Access.

Any ideas?  Thanks.

---

### Post by ScottDeagan on 2013-01-09
The only things I can think of is:

1) Make sure users are only granted access to databases and tables you want them to be able to access. For example, to give user 'tom' the ability to SELECT and INSERT from a table called 'employees' that exists in a database called 'company' from the LAN 192.168.1.x, you would use the following:

grant SELECT, INSERT on company.employees to 'tom'@'192.168.1.%';

If you have strict permissions set, you may then be able to get away with just using PHPMyAdmin or, better still, something like MySQL WorkBench (I would urge you, as the DB administrator, to evaluate anyway - it's the best :)).

2) Investigate the following possible alternatives (none of which I have experience with):

[http://www.libreoffice.org/features/base/](http://www.libreoffice.org/features/base/)
[http://www.kexi-project.org/](http://www.kexi-project.org/)

Both of the above are mentioned here: [http://ubuntuforums.org/showthread.php?t=742550](http://ubuntuforums.org/showthread.php?t=742550)

3) Learn how to develop your own front-end to the database using the LAMP stack coupled with a good PHP framework. My personal preference in regards to PHP frameworks is "Yii" ([http://www.yiiframework.com/](http://www.yiiframework.com/)). Using Yii it's very easy to develop customized DB front-ends for MySQL back-ends. I won't go into a very detailed "how-to" here as there is plenty of documentation on the Internet about Yii, but the general process is as follows:

a) Install the LAMP stack.
b) Download the latest version of Yii and extract it into a web directory (like /var/www).
c) Rename the extracted Yii folder name to "yii" (it makes life much easier, trust me).
d) Open your terminal.
e) Change into the directory containing the "yii" directory (e.g. cd /var/www if that's where it is).
f) Enter the following to create a skeleton web app: ./yii/framework/yiic webapp .
g) Open your browser and check that the web app exists: [http://yourserver](http://yourserver)

You should see your skeleton web app up and running. To hook this up to a database and start generation forms that will enable users to perform CRUD operations, you have to change the configuration:

a) Open terminal.
b) Change into your yii web app directory (e.g. cd /var/www)
c) Change into the config directory (e.g. from the yii web app root directory: cd protected/config)
d) Open the file in an editor.

From here, you have to uncomment a couple of sections and add your MySQL credentials. The first is to uncomment the "gii" section so you'll have access to a GUI interface for creating forms for your DB tables:

[PHP]
 'modules'=>array(
   // uncomment the following to enable the Gii tool

   'gii'=>array(
     'class'=>'system.gii.GiiModule',
     'password'=>'Enter Your Password Here',
     // If removed, Gii defaults to localhost only. Edit carefully to taste.
     'ipFilters'=>array('127.0.0.1','::1'),
   ),
 ),[/PHP]The next is to uncomment the MySQL section and enter your MySQL credentials accordingly:

[PHP]
   'db'=>array(
     'connectionString' => 'mysql:host=localhost;dbname=some_database',
     'emulatePrepare' => true,
     'username' => 'root',
     'password' => '',
     'charset' => 'utf8',
   ),[/PHP]From here, go to [http://yourserver/gii](http://yourserver/gii), enter the credentials you set in the config for gii, then create your models and CRUD forms/controllers.

As mentioned, there are plenty of resources on the Internet on how to use Yii/Gii (e.g. [http://www.youtube.com/watch?v=BCBIWNG8rL0](http://www.youtube.com/watch?v=BCBIWNG8rL0)). There is a learning curve, but it will pay off in the end if you put in the effort (I use Yii for many projects that require a web front-end to access a MySQL back-end).

Just some ideas....

---

### Post by CharlesA on 2013-01-09
Why not phpmyadmin?

---

### Post by ScottDeagan on 2013-01-09
I don't use phpmyadmin, but the OP mentioned that he doesn't want the users having access to admin functions. He wants to give users basic CRUD access.

---

### Post by CharlesA on 2013-01-09
Thought you could create users with limited access and their permissions would apply to phpmyadmin as well.

---

### Post by abandonedthe_mulletator on 2013-01-10
Thanks guys.  I think  Yii is what I am looking for.  I'll give it a shot.

---

