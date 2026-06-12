---
title: "Create an executable file"
date: 2015-03-04
forum: General Help
---

### Post by Manuel_Ferrero on 2015-03-04
[SIZE=2][FONT=arial]hi, i've downloaded ODOO ARGENTINA ([http://odooargentina.com](http://odooargentina.com)) ERP system. Now, for run it i've to open a terminal and write ```
sudo docker run --rm -ti -p 8069:8069 adhoc/odoo-all-in-one /bin/bash
``` and then ```
service postgresql start && sudo -H -u odoo /opt/odoo/server/odoo.py -c /opt/odoo/odoo.conf
```. What I wanna do is to create a file in desktop which allows me to run the ODOO ERP system by simply double clicking... 
[/FONT][/SIZE]
I wrote this:


```
#!/bin/bash


echo CYBERTECH Soluciones Informáticas


echo ..dentro 1 seg se iniciará el sistema de gestión empresarial.


sleep 1s


sudo docker run --rm -ti -p 8069:8069 adhoc/odoo-all-in-one /bin/bash


service postgresql start && sudo -H -u odoo /opt/odoo/server/odoo.py -c /opt/odoo/odoo.conf
```


but when it executes ask to me the password and when I write it, second line ('service postgresql.....') doesn't appear and I'm freeze there :/ is there an option to put the pass automatically and continue with the rest of command?

Thanks!

---

### Post by sandyd on 2015-03-04
> **Manuel_Ferrero said:**
> [SIZE=2][FONT=arial]hi, i've downloaded ODOO ARGENTINA ([http://odooargentina.com](http://odooargentina.com)) ERP system. Now, for run it i've to open a terminal and write ```
sudo docker run --rm -ti -p 8069:8069 adhoc/odoo-all-in-one /bin/bash
``` and then ```
service postgresql start && sudo -H -u odoo /opt/odoo/server/odoo.py -c /opt/odoo/odoo.conf
```. What I wanna do is to create a file in desktop which allows me to run the ODOO ERP system by simply double clicking... 

Thanks! and sorry for my english ;)

[/FONT][/SIZE]PD: I tried with gedit but it doesn't works... 


I wrote this:


```
#!/bin/bash


echo CYBERTECH Soluciones Informáticas


echo ..dentro 1 seg se iniciará el sistema de gestión empresarial.


sleep 1s


sudo docker run --rm -ti -p 8069:8069 adhoc/odoo-all-in-one /bin/bash


service postgresql start && sudo -H -u odoo /opt/odoo/server/odoo.py -c /opt/odoo/odoo.conf
```


and then I select "ask every time" option in files options window...

Go to Unity Dash -> Terminal

Type in
```

cd Desktop
bash *yourscriptname*

```

See what errors it has.

What I suspect is that you have not navigated to the directory holding your docker container (at the line with adhoc/odoo-all-in-one)

---

### Post by Manuel_Ferrero on 2015-03-04
mmmh I'm more confused now... when I write the firs line ('sudo docker....') it says that the port is already allocated....

---

### Post by sandyd on 2015-03-04
> **Manuel_Ferrero said:**
> mmmh I'm more confused now... when I write the firs line ('sudo docker....') it says that the port is already allocated....

check if docker is already running the app.
See [https://docs.docker.com/userguide/usingdocker/](https://docs.docker.com/userguide/usingdocker/)

---

### Post by Manuel_Ferrero on 2015-03-04
well I restarted linux and it works now but only if I write the lines in terminal... the script doesn't work yet...

---

