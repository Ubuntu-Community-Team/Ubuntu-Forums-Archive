---
title: "access denied?"
date: 2007-02-11
forum: General Help
---

### Post by mgame2k on 2007-02-11
I have properly installed the modules for my PVR 150 tv tuner card.
I have installed MySql, and Mythtv.

As I was following instructions and typed this command.

mysql -u root mysql

It tells me "access denided root@localhost password NO"

I have ininstalled mysql and am still having the same message.

I've also added both root and my username to mysql group and still get the same message.

I've switched to root using sudo su and still can't do anything.

How can root not have access to any program it wants to?

Does anyone have any ideas as to how to fix this?

Thanks

---

### Post by Ramses de Norre on 2007-02-11
Try ```
mysql -u root
```

---

### Post by fenian on 2007-02-11
When you uninstalled mysql did you use "apt-get remove --purge" or "mark for complete removal" in synaptic?If not some of the config files were probably not deleted.You can get rid of everything in two ways
1)From synaptic search for mysql find all packages currently installed and select the "mark for complete removal"
2)From the command line type 

> sudo apt-get remove --purge mysql-server mysql-client mysql-common

If you installed phpmyadmin and apache you may have to purge these as well.

After you have reinstalled mysql set the password (I know some mythtv guides don't do this but I think it's a good idea to set it and I don't think it does any harm.Set it with this command  (replace the second password with the word you want without the quotes)...

> mysqladmin -u root password "password"

Now if you type...
> 
mysql -u root password yournewpasswrd

Mysql will open to the options screen showing the commands that can be run with mysql.

---

