---
title: "Changing permissions in terminal"
date: 2007-02-19
forum: General Help
---

### Post by jtreach on 2007-02-19
I've been trying to create a virtual windows machine on my linux box. I've created the virtual machine but it's set so that only the root can do anything with it. Hence the fact I can't change the permissions within the gui.

How do I set it so that I can do everything (read write execute) with it using terminal?

:confused:

---

### Post by Rippey on 2007-02-19
sudo chmod -R 777 </folder/of/the/machine>

---

### Post by taurus on 2007-02-19
> **Rippey said:**
> sudo chmod -R 777 </folder/of/the/machine>

You need to take _extreme caution_ when you run that command because if you change 777 to the whole system, things will break and there is no going back.

---

### Post by jtreach on 2007-02-20
Okay thanks I've figured it out now. Thanks alot. Got it running. :]

---

