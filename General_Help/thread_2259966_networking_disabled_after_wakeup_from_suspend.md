---
title: "networking disabled after wakeup from suspend"
date: 2015-01-08
forum: General Help
---

### Post by safaldasg on 2015-01-08
my acer system
after i wakep from suspend my networking gets disabled .happens after a long sleep
i restart often to enable is this a bug

---

### Post by kurt18947 on 2015-01-08
I wonder if you're having the same issue that affects some Realtek WiFi adapters. The symptom seems very similar to what you're seeing - WiFi is working, suspend the machine, resume the machine and WiFi isn't working.  Disabling then enabling networking in network manager may cause the WiFi to work properly, as will unplugging/replugging a USB adapter.  The problem is that WiFi is not properly suspended when the machine suspends so cannot initialize correctly. At least this is my understanding. The solution I use is as follows. It suspends the wifi module is suspended so wifi is correctly initialized upon resume:

```

sudo gedit /etc/pm/config.d/config
# a new empty file will open
SUSPEND_MODULES="module_name"

```
then save the config file.

"module_name" will depend on which chipset your machine uses.  You should be able to determine that by typing in a terminal
```
lsmod(lowercase L)
```

Here's a snippet of mine:

```

psmouse               106714  0 
pata_atiixp            13271  0 
ahci                   25819  1 
libahci                32716  1 ahci
**r8169                  67581  0 **
mii                    13934  1 r8169

```

If I wanted to be sure the r8169 module suspended, the one line file would look like this:

```

SUSPEND_MODULES="r8169"

```

This machine is using wired ethernet.  The bolded line is the ethernet module.  Yours will be different, obviously. Please post back if this doesn't help or you have further questions.

---

### Post by matt_symes on 2015-01-08
Hi

> **safaldasg said:**
> my acer system
after i wakep from suspend my networking gets disabled .happens after a long sleep
i restart often to enable is this a bug

You never specified if your problem is with wired or wireless or both. That's a pretty critical piece of information.

Kind regards

---

### Post by monkeybrain20122 on 2015-01-08
[http://askubuntu.com/questions/463594/starting-postgresql-server-postgres-user-unknown](http://askubuntu.com/questions/463594/starting-postgresql-server-postgres-user-unknown)

---

