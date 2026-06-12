---
title: "Amarok + MySQL on launch"
date: 2008-04-15
forum: General Help
---

### Post by advoss on 2008-04-15
I currently have Amarok with MySQL running fine.  However I am running on an older system and do miss the resources MySQL requires.  Is there anyway that I can setup MySQL to start when I launch amarok rather than at system boot?

Thanks

---

### Post by pointone on 2008-04-16
```
sudo update-rc.d -f mysqld remove
```

... to stop the MySQL server from starting at boot.

```
sudo /etc/init.d/mysqld start
```

... to start MySQL manually.

```
sudo /etc/init.d/mysqld stop
```

... to stop MySQL manually.

You can create a simple wrapper script for Amarok:

```
#! /bin/bash

sudo /etc/init.d/mysqld start
/usr/bin/amarok
```

... you'll probably want to setup sudo to allow you to start mysqld without a password if you go this route.

---

### Post by advoss on 2008-04-16
Thanks, thats of great help.  One more thing though,the amarok command seems to be a loader that launches amarokapp then terminates.  Is there any reason I can't have my script launch amarokapp, that way I can tack on the command to stop MySQL at the end of my script?

---

### Post by features on 2008-04-16
Hiya,

The correct command to start amarok is 

```
/usr/bin/amarokapp
```

So your script should read:

```
#! /bin/bash

sudo /etc/init.d/mysqld start
/usr/bin/amarokapp 
```


Hope this helps :)

Mark

---

