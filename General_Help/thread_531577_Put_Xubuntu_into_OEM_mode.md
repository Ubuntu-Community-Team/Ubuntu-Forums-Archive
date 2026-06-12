---
title: "Put Xubuntu into OEM mode"
date: 2007-08-21
forum: General Help
---

### Post by j_ririe20 on 2007-08-21
[FONT="Arial"]I have an Xubuntu computer that I want to put into OEM mode so I can sell it. I want it to start up the first time for the person who buys it and they put in their own username and password. 

I heard that all you have to do is type in a command into the terminal and it's all set. What command is this, or does it even exist?[/FONT]

---

### Post by pyrokenx on 2007-08-21
I think the oem-config package is what you want.. open up a terminal and do the following.


```

sudo apt-get install oem-config &&  sudo apt-get install oem-config-gtk
```

then I would assume run oem-config-gtk after that

---

### Post by j_ririe20 on 2007-08-23
Thanks, that worked great. I used the oem-config-prepare code instead, though.

---

