---
title: "Xampp / Can't get to the home page typing &quot;http://localhost/&quot;"
date: 2014-04-02
forum: General Help
---

### Post by ian41 on 2014-04-02
Hello,
I have been running Xampp for a month or so and everything was going fine. Latterly I have realised a few weird things:
 - I do not need to start Xampp in the terminal when I switch on my computer, it is already running.
 - When I refresh my browser (Firefox) the changes I maked on my .php document are not always taken into account directly.
 - When I type [http://localhost/](http://localhost/) in my browser I do not get the normal orange page, but I get the page "Index of" followed by all my folders.
Have I deleted a folder I shouldn't have?
Does someone have an idea of what is going on?

Thanks

By the way I a running Xampp on Ubuntu 12.04.

---

### Post by monkeybrain20122 on 2014-04-02
I think you have installed apache2 from the system somehow and that overrides xampp to become your default server. It is actually better than xampp.

---

### Post by ian41 on 2014-04-02
> **monkeybrain20122 said:**
> I think you have installed apache2 from the system somehow and that overrides xampp to become your default server. It is actually better than xampp.

How can I verify this ?

---

### Post by steeldriver on 2014-04-02
To see whether it is installed

```

dpkg -l apache2

apt-cache policy apache2
```

To see whether it's running

```

service apache2 status

sudo netstat -nlp | grep :80

sudo lsof :80
```

Replace 80 if you are not using the default port

---

### Post by ian41 on 2014-04-02
Well, I do not have Apache 2 on my computer. The problem is else where.

---

