---
title: "Packages to Run PHP?"
date: 2014-01-16
forum: General Help
---

### Post by rudolf.almeida on 2014-01-16
I need to use a Local server on my PC to view PHP files. But I am not sure of the Packages to install to run PHP. Can anybody please tell me the packages I should install to run PHP server locally. I need PHP, phpmyadmin, apache and MySQL. I use Ubuntu 12.04. Thank You.

---

### Post by bertan2 on 2014-01-16
If by "view PHP files" you mean you just want to view the php code, you don't need php installed. You can do that with a text editor.


If on the other hand you want to view the results of executing the php, then you need to do the Apache and PHP steps from the Ubuntu tutorial: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by SeijiSensei on 2014-01-16
```

sudo apt-get install tasksel
sudo tasksel install lamp-server
sudo apt-get install phpmyadmin

```

I suggest you try and learn how to use the command-line MySQL client rather than relying on phpmyadmin if you plan to build more sites with SQL backends.

---

### Post by TheFu on 2014-01-16
> **SeijiSensei said:**
> ```

sudo apt-get install tasksel
sudo tasksel install lamp-server
sudo apt-get install phpmyadmin

```

I suggest you try and learn how to use the command-line MySQL client rather than relying on phpmyadmin if you plan to build more sites with SQL backends.

Running PHP and/or MySQL without security knowledge can be dangerous to the PC and to any other PC on the same network.  Please be careful if you make those services available on the LAN or internet.

---

### Post by rudolf.almeida on 2014-01-17
Thank you. I have got Apache up and running but I still cant use 'phpmyadmin'. I get a 404 error on the address localhost/phpmyadmin. I included the line "Include /etc/phpmyadmin/apache.conf " in the apache2.conf file but it still hasnt solved anything. I have just started learning PHP and I need these just to view the results of the pages I create. How can I block incoming connections on the network and just view files locally?

---

### Post by SeijiSensei on 2014-01-18
You can attach Apache to the localhost interface by editing /etc/apache2/ports.conf and changing the NameVirtualHost declaration so it looks like this:
```
NameVirtualHost 127.0.0.1:80
```
In the virtual host declarations, replace the <VirtualHost *:80> directive with
```
<VirtualHost 127.0.0.1:80>
```

---

### Post by rudolf.almeida on 2014-01-20
Thanks. I dont know why but 'phpmyadmin' started working 2-3 reboots after editing the configuration file.

---

### Post by TheFu on 2014-01-20
> **rudolf.almeida said:**
> Thanks. I dont know why but 'phpmyadmin' started working 2-3 reboots after editing the configuration file.

A reboot should only be helpful to reset a hardware device.  Linux is not Windows where a reboot seems to fix all sorts of things. For something like this, a reboot shouldn't matter at all unless restarting a daemon was necessary and forgotten.

That is the theory.

---

### Post by dragonfly41 on 2014-01-20
Possibly the browser cache had not cleared .. try Ctrl+F5 after such changes to files. This refreshes browser.

---

