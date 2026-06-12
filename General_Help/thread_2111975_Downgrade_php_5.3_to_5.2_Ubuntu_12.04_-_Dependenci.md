---
title: "Downgrade php 5.3 to 5.2 Ubuntu 12.04 - Dependencies error"
date: 2013-02-03
forum: General Help
---

### Post by pcrio2 on 2013-02-03
Hello, im trying to downgrade php to 5.2 following a tutorial:

put the attached karmic.list in /etc/apt/sources.list.d and the attached "php" into /etc/apt/preferences.d.

```
sudo apt-get update
sudo apt-get remove php5 libapache2-mod-php5 php5-xsl php5-gd php-pear php5-mysql php5-curl php5-memcache
sudo apt-get install php5 libapache2-mod-php5 php5-xsl php5-gd php-pear  php5-mysql php5-curl php5-memcache
```When i run the command to  install php 5.2 this error appears (Sorry, its in portuguese, i will try  to translate it) :

```
Os pacotes a seguir têm dependências desencontradas:
 libapache2-mod-php5 : Depende: php5-common (= 5.3.10-1ubuntu3) mas 5.2.10.dfsg.1-2ubuntu6 está para ser instalado
E: Impossível corrigir problemas, você manteve (hold) pacotes quebrados.
```[B]
English[/B]

```
The following packages have dependencies found: 
 libapache2-mod-php5 : Depends: php5-common (= 5.3.10-1ubuntu3) but 5.2.10.dfsg.1-2ubuntu6 is going to be installed
E:  Its impossible to fix this problem, you kept (hold) broken packages.
```How do i fix this?

Regards

---

### Post by slickymaster on 2013-02-04
Try to fix the broken packages. Open Synaptic Package Manager and look for messages at the bottom that point to any broken packages or type the following at a terminal window:
```
sudo apt-get install -f
```

Look for that required dependencies packages from ubuntu packages and install them:
```
sudo dpkg -i name.deb
```

---

