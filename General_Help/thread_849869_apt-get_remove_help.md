---
title: "apt-get remove help"
date: 2008-07-04
forum: General Help
---

### Post by SidewinderX on 2008-07-04
When I do the following command ```
john@pluto:~$ sudo apt-get remove php5-
``` and press tab, it will display ```
php5-cli     php5-common  php5-curl    php5-gd      php5-mysql
``` However, when I do attempt to remove one of those packages, it says it is not installed. How come this is? ```
john@pluto:~$ sudo apt-get remove php5-cli 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php5-cli is not installed, so not removed


0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded.
```

Thank you,
John

---

### Post by VMC on 2008-07-04
What's the output of this command:

```
sudo dpkg --get-selections | grep php
```

---

### Post by SidewinderX on 2008-07-04
```
john@pluto:~$ sudo dpkg --get-selections | grep php
libapache2-mod-php5                             deinstall
php5-cli                                        deinstall
php5-common                                     deinstall
php5-curl                                       deinstall
php5-gd                                         deinstall
php5-mysql                                      deinstall

```

---

### Post by VMC on 2008-07-05
> **SidewinderX said:**
> ```
john@pluto:~$ sudo dpkg --get-selections | grep php
libapache2-mod-php5                             deinstall
php5-cli                                        deinstall
php5-common                                     deinstall
php5-curl                                       deinstall
php5-gd                                         deinstall
php5-mysql                                      deinstall

```

That's telling you it's already uninstalled. Are their directories you want removed. You can do search for them.

---

### Post by Bubba64 on 2008-07-05
These php5 packages are in synaptic I would look there and see if any are ticked on, I think if you want to remove anyone specifically in terminal you have to be more specific.

---

### Post by SidewinderX on 2008-07-05
> **VMC said:**
> That's telling you it's already uninstalled. Are their directories you want removed. You can do search for them.
I don't believe there are any directories: ```
john@pluto:~$ whereis php5
php5:

``` I do suppose they are uninstalled, its just odd that apt find(?) them as packages to uninstall - maybe im missing something.




> **Bubba64 said:**
> These php5 packages are in synaptic I would look there and see if any are ticked on, I think if you want to remove anyone specifically in terminal you have to be more specific. None of them are selected in the Synaptic Package Manager. What do you mean, be more specific?

---

### Post by Elfy on 2008-07-05
They might be floating about as residual configs - open synaptic and then use status in left pane to see if you have any residual configurations, if so mark them for complete removal.

In terminal you can use purge instead of remove, I think that gets rid of the configs as well

sudo apt-get purge package

---

### Post by SidewinderX on 2008-07-05
> **forestpixie said:**
> They might be floating about as residual configs - open synaptic and then use status in left pane to see if you have any residual configurations, if so mark them for complete removal.

In terminal you can use purge instead of remove, I think that gets rid of the configs as well

sudo apt-get purge package

That did it! Thank you.

---

