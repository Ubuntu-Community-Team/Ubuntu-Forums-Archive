---
title: "Can't copy my synch file to /etc/eciadsl help pleas..."
date: 2007-07-23
forum: General Help
---

### Post by bar8080 on 2007-07-23
I downloaded and installed all usb/adsl drivers but i can't get the synch file into the /etc/eciadsl folder because i need permission please help, how can I fix this?

---

### Post by stchman on 2007-07-23
> **bar8080 said:**
> I downloaded and installed all usb/adsl drivers but i can't get the synch file into the /etc/eciadsl folder because i need permission please help, how can I fix this?

The /etc folder cannot be written to by users only root can.

Put a sudo in front of your copy statement.

---

### Post by bar8080 on 2007-07-23
what should the copy statement be? the file format is xxx.tar.tar.. thanks

---

### Post by stchman on 2007-07-23
suppose the file you wish to copy is in your home folder

sudo cp ~/<file you wish to copy> /etc/eciadsl

---

