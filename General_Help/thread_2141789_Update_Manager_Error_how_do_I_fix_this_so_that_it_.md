---
title: "Update Manager Error how do I fix this so that it works again"
date: 2013-05-03
forum: General Help
---

### Post by Bushcraft Bill on 2013-05-03
below is the error I am getting update Manager crashes and gives me this below...
Is their a fix I can try or am I hooped and have to reinstall really dont want to loose all the work I got into getting things setup now
I am running ubuntu 12.04
===========================================================
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 2 in source list /etc/apt/sources.list.d/openshot_developers-ppa-precise.list'

---

### Post by matt_symes on 2013-05-03
Hi

Open a terminal and type (or copy and paste) this into it.

```
cat /etc/apt/sources.list.d/openshot_developers-ppa-precise.list
```

Copy and paste the results from the terminal back into you next post (highlight text -> right click-> copy).

This file is malformed and we'll see what state it's actually in.

Kind regards

---

### Post by Bushcraft Bill on 2013-05-03
This is result I got
===============================================

deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) precise main
ain

---

### Post by matt_symes on 2013-05-03
Hi

> **Bushcraft Bill said:**
> This is result I got
===============================================

deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) precise main
ain

The 'ain' on the second line needs to be deleted.

Open a terminal and type (or copy and paste)

```
sudo sed -i '2d' /etc/apt/sources.list.d/openshot_developers-ppa-precise.list
```

Enter your password. It will not be echoed to the screen. This is normal. 

That will delete the second line (2d).

Then type

```
sudo apt-get update
```

Kind regards

---

