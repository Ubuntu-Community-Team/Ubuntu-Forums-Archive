---
title: "Install git/gitolite/gitweb on Ubuntu 14.04"
date: 2014-09-20
forum: General Help
---

### Post by GouZi on 2014-09-20
[SIZE=5]Introduction[/SIZE]

While there are general instructions avaible some packages are partially broken in 14.04 ([https://bugs.launchpad.net/ubuntu/+source/gitweb/+bug/1329542](https://bugs.launchpad.net/ubuntu/+source/gitweb/+bug/1329542)) and a few things have to be tweaked.

[SIZE=5]I. git/gitolite/gitweb: general instructions[/SIZE]

To install/configure git/gitolite please refer to:
[https://help.ubuntu.com/14.04/serverguide/git.html](https://help.ubuntu.com/14.04/serverguide/git.html)

To install gitweb:
```
sudo apt-get install gitweb
```

[SIZE=5]II. A few things to tweak[/SIZE]

[SIZE=4]1. gitweb[/SIZE]

As mentionned in [https://bugs.launchpad.net/ubuntu/+source/gitweb/+bug/1329542](https://bugs.launchpad.net/ubuntu/+source/gitweb/+bug/1329542) gitweb install a config file in the deprecated /etc/apache2/conf.d/ location.

To fix this:
```
sudo cp /etc/apache2/conf.d/gitweb /etc/apache2/conf-available/gitweb.conf
cd /etc/apache2/conf-enabled
sudo ln -s ../conf-available/gitweb.conf

```

Modify gitweb.conf to look like:
```
Alias /gitweb /usr/share/gitweb

<Directory /usr/share/gitweb>
  Options +FollowSymLinks +ExecCGI
  AddHandler cgi-script .cgi
</Directory>

```
(I.e. adding "+" before +FollowSymLinks)

Enable cgi, so that the gitweb script is run and not displayed/downloaded from your web browser:
```
sudo a2enmod cgi
sudo service apache2 restart
```

In /etc/gitweb.conf make sure you have:
```

$projectroot = "/home/git/repositories/";
$projects_list = "/home/git/projects.list";
```


[SIZE=4]2. gitolite[/SIZE]

As detailed here [http://gitolite.com/gitolite/g2/rc.html](http://gitolite.com/gitolite/g2/rc.html):
> The default UMASK that gitolite uses makes all the repos and their contents have rwx------ permissions. People who want to run gitweb realise that this will not do.

The correct way to deal with this is to give this variable a value like 0027 (note the syntax: the leading 0 is required), and then make the user running the webserver (apache, www-data, whatever) a member of the 'git' group.


In /home/git/.gitolite.rc make sure you have:
```
$REPO_UMASK = 0027;

```

Add user www-data to the git group:
```
sudo usermod **-a** -G git www-data

```

Make sure projects.list has group read permission:
```
sudo chmod 640 /home/git/projects.list
```

Make sure projects.list is not empty!

Finally:
```
sudo service apache2 restart
```

Now you should see your projects in:
[http://localhost/gitweb/](http://localhost/gitweb/)

Updated: 
usermod command (add -a), to not overwrite any other groups www-data is in. Credits: foo5

---

### Post by mixim33 on 2015-02-17
Thank you so much for your post

---

### Post by foo5 on 2015-07-30
Just wanted to make a small correction to step II. second line: Add group "git" to www-data in **append** mode as

```
sudo usermod **-a** -G git www-data
```

Otherwise you'll be overwriting any other groups www-data is in.

---

