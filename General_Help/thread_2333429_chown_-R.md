---
title: "chown -R"
date: 2016-08-10
forum: General Help
---

### Post by abdul225 on 2016-08-10
HI team,
during the installation of ocats on my ubuntu machine while i perform the following command "    [COLOR=#17365d][FONT=Consolas]chown jboss:jboss –R /var/www/html/cats/config/[/FONT][/COLOR]

" 
I'm getting the following error please help me debug this issue:
root@abdul-Veriton-M200-A780:/home/abdul/Documents/cats-master/ocats-vision# chown jboss:jboss –R /var/www/html/cats/config/
chown: cannot access ‘–R’: No such file or directory

---

### Post by howefield on 2016-08-10
That looks like a long dash in your command rather than a short dash. How did you type it ?

```
chown jboss:jboss &#8211;R /var/www/html/cats/config/
```

is different to

```
chown jboss:jboss -R /var/www/html/cats/config/
```

---

### Post by abdul225 on 2016-08-11
> **howefield said:**
> That looks like a long dash in your command rather than a short dash. How did you type it ?

```
chown jboss:jboss –R /var/www/html/cats/config/
```

is different to

```
chown jboss:jboss -R /var/www/html/cats/config/
```


this solved my issue thanks

---

### Post by howefield on 2016-08-11
> **abdul225 said:**
> this solved my issue thanks

Cool, you are very welcome.

---

