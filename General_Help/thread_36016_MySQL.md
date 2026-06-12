---
title: "MySQL"
date: 2005-05-21
forum: General Help
---

### Post by makimonaco1 on 2005-05-21
I am trying to get an application running on my system which uses MySQL databases but I don't seem to have MySQL on my machine. How can I download and install it?

---

### Post by Gandalf on 2005-05-21
[QUOTE=makimonaco1]I am trying to get an application running on my system which uses MySQL databases but I don't seem to have MySQL on my machine. How can I download and install it?[/QUOTE]
 [http://ubuntuguide.org/#installmysqldatabaseserver](http://ubuntuguide.org/#installmysqldatabaseserver)

hope it helps

---

### Post by makimonaco1 on 2005-05-21
when I do sudo apt-get install mysql-server (I am root) I get:

[COLOR=Navy]Reading packages list... done
Creating dependency trees... done
Some packages could not be installed. This may mean that you requested an impossible situation or, if you are using a unstable distribution, that some packages needed have not been created or have been moved from Incoming.

Since you only requested this operation, it is very possible that the the package is simply not instalable and you should fill an error report against that package.
The following information may help you solve the situation:

The following packages have unrespected dependencies:
  mysql-server: Depends: mysql-client (>= 4.0.20-2ubuntu1.5) but will not be installed
                        Depends: libdbi-perl but will not be installed

E:Brocken packages[/COLOR]

Sorry if the error messages are not exacly that but I've translated them from Spanish.

Thanks.

---

### Post by Gandalf on 2005-05-21
[QUOTE=makimonaco1]when I do sudo apt-get install mysql-server (I am root) I get:

[COLOR=Navy]Reading packages list... done
Creating dependency trees... done
Some packages could not be installed. This may mean that you requested an impossible situation or, if you are using a unstable distribution, that some packages needed have not been created or have been moved from Incoming.

Since you only requested this operation, it is very possible that the the package is simply not instalable and you should fill an error report against that package.
The following information may help you solve the situation:

The following packages have unrespected dependencies:
  mysql-server: Depends: mysql-client (>= 4.0.20-2ubuntu1.5) but will not be installed
                        Depends: libdbi-perl but will not be installed

E:Brocken packages[/COLOR]

Sorry if the error messages are not exacly that but I've translated them from Spanish.

Thanks.[/QUOTE]
 did you add extra repository? [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

try this:
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

add this
```

# ubuntu repository
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse

```

update the repo
```

sudo apt-get update

```

and then start again

---

### Post by makimonaco1 on 2005-05-21
Thanks for the answer. Actually the /etc/apt/sources.list file was empty. I added the three lines of code you sent, updated the repo and just did the apt-get mysql-server command and it is downloading and installing.

Will pos a message in case of problems.

---

### Post by makimonaco1 on 2005-05-21
Evrything seemed to go ok. I also did the :

[COLOR=DarkRed][COLOR=Navy]mysqladmin -u root password db_user_password[/COLOR][/COLOR]

Now if I try doing anything with it like:

[COLOR=DarkRed]mysqladmin create hollyradius[/COLOR] I get an error saying:

[COLOR=Navy]mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'[/COLOR]

Sorry I can do this with WINDOWS but I am trying to change out OS base and I am new ad MySQL and LINUX.

Thanks.

---

### Post by makimonaco1 on 2005-05-21
Sorry. Was doing it wron. It is Ok now. Thanks.

---

### Post by Gandalf on 2005-05-21
[QUOTE=makimonaco1]Evrything seemed to go ok. I also did the :

[COLOR=DarkRed][COLOR=Navy]mysqladmin -u root password db_user_password[/COLOR][/COLOR]

Now if I try doing anything with it like:

[COLOR=DarkRed]mysqladmin create hollyradius[/COLOR] I get an error saying:

[COLOR=Navy]mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'[/COLOR]

Sorry I can do this with WINDOWS but I am trying to change out OS base and I am new ad MySQL and LINUX.

Thanks.[/QUOTE]
 when you type
mysqladmin -u root password db_user_password
then you change the root password to db_user_password

you must connect to mysql using that password
that means

instead of
mysqladmin create hollyradius
use
mysqladmin -u root -p create hollyradius

BTW that's mysql documentation not ubuntu documentations!!!


//EDIT: oops i was a bit slow :$ anyway no problem

---

### Post by themoddingden on 2005-06-01
hi;
could i use this for 2 data bases in mysql for 2 different forums???
I'm making 2 sites with mambo and simple machines forums.
and right now i'm haveing problems making the database conncet on bot
if i delete the current data base could i set up a new one ???
or could i just creat a new one

---

### Post by Gandalf on 2005-06-01
[QUOTE=themoddingden]hi;
could i use this for 2 data bases in mysql for 2 different forums???
I'm making 2 sites with mambo and simple machines forums.
and right now i'm haveing problems making the database conncet on bot
if i delete the current data base could i set up a new one ???
or could i just creat a new one[/QUOTE]
 you mean using mysql for different site??? well of course, mysql can contain as many databases as you want

---

