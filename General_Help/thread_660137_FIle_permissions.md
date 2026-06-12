---
title: "FIle permissions"
date: 2008-01-06
forum: General Help
---

### Post by Mr.popo on 2008-01-06
I need to copy some python modules to /usr/lib/python2.5 but it doesnt allow me to. The message tells me that I have permission. But i dont understand because theres only one account and thats me so shouldnt i be admin or root.

PLease can you help me sort this out.

Thanks

---

### Post by bodhi.zazen on 2008-01-06
use sudo (sudo cp source destination)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksu for graphical applications

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Omnios on 2008-01-06
Root is dome by using the sudo command before the mv command. Also there are some Nautilus scripts that will allow varies root commands such as open with root gedit and I have one that will launch root Nautilus.

---

### Post by PeterJS on 2008-01-06
Even with an admin account you don't have admin rights for everyday actions unless you explicitly request them with sudo.

---

### Post by pdub on 2008-01-06
Are you using sudo to execute the copy as root?

sudo cp /file_1 /file_2

---

### Post by Mr.popo on 2008-01-06
I was just trying to drag and drop.

Thankyou

---

### Post by bodhi.zazen on 2008-01-06
You can drag and drop with nautilus running as root :

```
gksu nautilus
```

---

