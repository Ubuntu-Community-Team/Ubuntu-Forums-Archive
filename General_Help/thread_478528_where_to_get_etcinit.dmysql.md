---
title: "where to get /etc/init.d/mysql"
date: 2007-06-19
forum: General Help
---

### Post by knight_killer on 2007-06-19
I accidentally deleted the Mysql init-script /etc/init.d/mysql. Where can I get a new one (Feisty Fawn)?
Or could someone post it here?

Thanks,
Roman

---

### Post by meatpan on 2007-06-19
Here is an idea you can try.  No doubt there are probably a zillion other ways to do this.

1.  Determine which mysql package you are using.  Run 'dpkg -l | grep mysql' to get a list of mysql related packages.

2.  Determine which mysql package should have the /etc/init.d/mysql file . Run 'dpkg -L <package from #1> | grep init.d' for each of the packages in #1

3. Download the source for the package w/missing file.  Run 'apt-get source <package from #2>'

4. Copy the /etc/init.d/mysql script from the source file installed during #3.

---

### Post by knight_killer on 2007-06-19
OK, I tried that, but it doesn't work. The init-script inside mysql-server-5.0 was for debian. I applied the ubuntu patch for that, but it still doesn't work....

Now I unistalled all mysql-related stuff from my machine and tried to reinstall it. But with "apt-get install mysql-server" (includes mysql-server-5.0) it doesn't install the init-script, but it wanted to start it...

That's what I made:```
apt-get remove mysql-server
apt-get autoremove
apt-get autoclean
apt-get clean

find -name mysql
> /var/lib/mysql
> /var/lib/mysql/mysql
> /var/log/mysql

rm -rf /var/lib/mysql
rm -rf /var/log/mysql

apt-get install mysql-server

[...various stuff...]
Preconfiguring packages ...
Selecting previously deselected package libdbd-mysql-perl.
(Reading database ... 19285 files and directories currently installed.)
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0008-1build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1_all.deb) ...
Setting up libdbd-mysql-perl (3.0008-1build1) ...
Setting up mysql-client-5.0 (5.0.38-0ubuntu1) ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
```

Why does apt-get know that I previously had mysql installed? I cleaned the cache... Is that the reason why the init-script isn't installed yet?

---

### Post by kornface13 on 2007-08-23
I have the exact same problem.  Someone has to know how to get the file back.  Can someone just e-mail it to us???  It's worth a try.  Thanks alot!!

---

### Post by kornface13 on 2007-08-27
I found out how to fix this....here's the 4 commands I ran....

sudo apt-get install mysql-server-5.0
sudo apt-get --purge remove mysql-server-5.0
sudo apt-get autoremove mysql-server-5.0
sudo apt-get install mysql-server-5.0

I don't think the autoremove is necessary, but I figured what the heck...why not?

---

