---
title: "Development machine"
date: 2008-05-15
forum: General Help
---

### Post by mashcaster on 2008-05-15
Hello,

I would like to setup a development machine but I'm not sure how. All I need is LAMP, MySQL Query Browser, MySQL Administrator, and Eclipse (with aptana addon).

Any help will be greatly appreciated.

Thanks

---

### Post by AcidHawk on 2008-05-15
Look at UbuntuGuide for a LAMP server

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop")

You can always install eclipse as follows
```

sudo apt-get install eclipse

```

and for MYSQL Query Browser
```

sudo apt-get install mysql-query-browser

```

You will need to search for the Eclipse add-ons and add them to the Help->software Updates->Find and Install... menu option

**Update:**  I just ran 
```
sudo apt-cache search mysql
```
and I found mysql-admin I am not sure if this is what you were looking for but you can simply install it by running ```
sudo apt-get install mysql-admin
```

---

### Post by bobblehat on 2008-05-15
You can open up synaptic and search for packages for mysql, eclipse, etc. You should find most of what you need there (e.g. there are packages for mysql-server, mysql-navigator, etc).

---

