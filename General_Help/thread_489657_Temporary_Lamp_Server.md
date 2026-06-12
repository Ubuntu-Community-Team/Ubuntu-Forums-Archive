---
title: "Temporary Lamp Server?"
date: 2007-07-01
forum: General Help
---

### Post by mikaelsnavy on 2007-07-01
Hello,
I need to install a lamp server on my feisty laptop that can turn on and off. Is there a good tutorial on how to do this?
Thanks,
Mikael

---

### Post by eggdeng on 2007-07-01
There is an easy to follow guide at [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper). Although, it was written with dapper in mind, it should work just the same for Fiesty. Don't follow the link 'Build Ubuntu LAMP Server With Screenshots' which is for the server edition. To turn apache or the mysql server on and off from a nice graphical interface, one option is to install boot up manager. ```
apt-get install bum
```.

---

### Post by mikaelsnavy on 2007-07-01
thanks!

---

### Post by kbracer on 2007-07-01
You could use VMWare to run one of the pre-made virtual LAMP appliances available for download from the VMWare site.

---

### Post by az on 2007-07-01
> **mikaelsnavy said:**
> Hello,
I need to install a lamp server on my feisty laptop that can turn on and off. Is there a good tutorial on how to do this?
Thanks,
Mikael

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You can remove apache2 when you want to stop serving and reinstall it when you want to .

---

