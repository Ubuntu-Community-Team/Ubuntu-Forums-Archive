---
title: "can I install LAMP on Ubuntu Feisty Desktop ?"
date: 2007-05-27
forum: General Help
---

### Post by krypto_wizard on 2007-05-27
I want to play around with server side things and for that I want to install LAMP. I don't have an extra box for that ?

Can I install LAMP on my Ubuntu Feisty Desktop version ? If yes how ? 

Every help is appreciated,

Thanks

---

### Post by coxy on 2007-05-27
Yes you can. Have a read of this on the Ubuntu guide, that should get you going.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)

---

### Post by pbw on 2007-05-27
Sure you can.

```

sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mysql mysql-server mysql-client 

```

You might like phpmyadmin as well for gui database management, up to you of course though.

-- pbw

---

### Post by fragos on 2007-05-27
The simplest way is to open Synaptic, click Edit, Select Marked Packages by Task, and last check LAMP.

---

### Post by pbw on 2007-05-27
> **fragos said:**
> The simplest way is to open Synaptic, click Edit, Select Marked Packages by Task, and last check LAMP.

It is really that hard to type (or just paste) less than a sentence?

Scary.

-- pbw

---

### Post by fragos on 2007-05-28
It's all GUI and mouse clicks -- no typing or command line required.  Each person to their own way.

---

### Post by doubledown99can on 2007-06-11
> **fragos said:**
> The simplest way is to open Synaptic, click Edit, Select Marked Packages by Task, and last check LAMP.

When I tried this, LAMP didn't show up in the list.  The only thing in the list was "Ubuntu Desktop" which was already checkmarked.

---

### Post by fragos on 2007-06-11
> **doubledown99can said:**
> When I tried this, LAMP didn't show up in the list.  The only thing in the list was "Ubuntu Desktop" which was already checkmarked.

Perhaps you're missing a repository.  Assuming Feisty, click System-> Administration-> "Software Sources". In the Ubuntu Software tab make sure main, universe, restricted and multiverse are checked.  I double checked in Synaptic and I still have a LAMP check box.

---

