---
title: "ssh gui?"
date: 2007-02-09
forum: General Help
---

### Post by b4nsh33 on 2007-02-09
Hi, im looking for a ssh client application, something like secureCRT would be great, what do you recomend?. the command line works, but I have to connect to serveral  routers and i dont want to type the username, ip (and remember that ip!!!) every time i need to connect to them.

thanks

---

### Post by taurus on 2007-02-09
I thought nautilus can connect to your ssh servers.

---

### Post by PartickThistle on 2007-02-09
Write small shell scripts.

For instance;
```

#!/bin/bash
echo "Logging into: Name of Server"
ssh -l UserName 123.123.123.123

```

In your path, save this as **ssh.NameOfServer ** and make it executable.  Repeat for others.

I seem to recall PuTTY working on Wine, if you want to go down that route.

---

### Post by lamego on 2007-02-09
There is native putty for Linux:
[http://linux.softpedia.com/get/System/Networking/PuTTY-347.shtml](http://linux.softpedia.com/get/System/Networking/PuTTY-347.shtml)

---

### Post by b4nsh33 on 2007-02-09
putty is what i was looking for, thanks

---

### Post by stylishpants on 2007-02-09
> **b4nsh33 said:**
> putty is what i was looking for, thanks

Or just use regular ssh, but create the file ~/.ssh/config, and customize your servers uniqely within it.

eg.

```

Host bagend
        Hostname bagend.shirenet.org
        User bilbo
        ForwardX11 yes
        Port 50022

Host forest
        Hostname 192.168.170.254
        User root

Host cave
        Hostname 192.168.170.10
        User smaug

```

Now I can type "ssh bagend" and it will connect to bagend.shirenet.org as user bilbo, on port 8022.  Of course, if you're using ssh authorized keys, you don't need a password either.

---

