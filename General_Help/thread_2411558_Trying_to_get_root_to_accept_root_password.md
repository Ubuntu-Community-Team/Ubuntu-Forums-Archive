---
title: "Trying to get root to accept root password"
date: 2019-01-31
forum: General Help
---

### Post by terryfoster60 on 2019-01-31
I have installed Ubuntu 16 on an old 32 bit ex-windows Xp machine and want to install it as a web server.

I have gone through the installation and created my password for terry as Password1^ (for the purpose of thie email.)
I then installed Apache and that works ok.
I now install mySql and when it asks me to enter:
sudo /usr/bin/mysql_secure_installation
I get asked for the root password.

I try my password - no good

I can not log in as root nor will my password work.

This a brand new installation and I have never been asked to set up a root password.
It keeps asking for a password to start the MySql and neither the Mysqlpassword nor my password works.

How can I get around this su Authentication Failure
Thank you in advance for any feedback

---

### Post by terryfoster60 on 2019-01-31
the output of id is
uid=1000(terry) gid=1000(terry) groups=1000(terry), 4(adm),24(cdrom), 27(sudo),30(dip, 46(plugdev), 113(lpadmin), 128(sambashare)

---

### Post by jdeca57 on 2019-01-31
In mysql you have to be root to gain root access so try it with sudo.
 
addendum

this goes for mysql -u root -p

---

### Post by lisati on 2019-01-31
The password asked for when using "sudo" to perform admin tasks on your *buntu machine doesn't normally get displayed on screen when you're typing it in. Just type in your password as usual, and as long as the logged in user has sudo privileges, you should be good to go.

The mysql "root" password is a separate entity to the *nix "root" password, and needs to be created separately from any password you might have for general admin tasks on your Ubuntu machine.

Hope this helps. If you have any further questions, feel free to ask.

---

### Post by terryfoster60 on 2019-01-31
I enter at the $ prompt
mysql -u root -p
I tried the root password for MySql
It came back with:
Error 1045 (28000):Accenss denied for 'root'@localhost (using oassword:YES)

---

### Post by lisati on 2019-01-31
If this is a "fresh" installation of mysql, you might find [this guide]("https://support.rackspace.com/how-to/mysql-resetting-a-lost-mysql-root-password/") of some help if you have forgotten the "root" password for mysql. Note: instructions are given for a handful of different Linux distros, make sure you follow those for Ubuntu.

On a side note, which may or may not be relevant, are you using Ubuntu 16.04 or 16.10?

---

### Post by jdeca57 on 2019-01-31
> **terryfoster60 said:**
> I enter at the $ prompt
mysql -u root -p
I tried the root password for MySql
It came back with:
Error 1045 (28000):Accenss denied for 'root'@localhost (using oassword:YES)

Well, it should be sudo mysql -u root -p

and another idea if the password isn't set simply

sudo mysql -u root

---

