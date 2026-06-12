---
title: "Problems installing java"
date: 2006-11-24
forum: General Help
---

### Post by wvcaudill2 on 2006-11-24
Hello, im trying to install java from this page: [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

But, its not working because I need to CHMOD the /java/ directory I just created, but I dont know how. It also says I need root access, but some people on one of my other threads said its not a good idea. Please help!

---

### Post by taurus on 2006-11-24
Why not use Automatix to install it?  It's fast and easy...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by wvcaudill2 on 2006-11-24
Oh, ive never heard of automatix. Im getting it though. Installed1 Thanks for your help :)

---

### Post by burek on 2006-11-24
automatix2 is there : [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Delkster on 2006-11-24
A better solution:
1. Install Sun Java Runtime Environment as [instructed in the Ubuntu wiki](https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956). If you use Ubuntu (with the Gnome desktop), you can search for "sun java" in Add/Remove Applications. Be sure to check both the Java 5.0 Runtime and the corresponding plugin. If you can't seem to find the packages, make sure that you have all available applications shown, not only officially supported ones.

2. Open a terminal (in Gnome, that's Applications > Accessories > Terminal). On the terminal command line, enter the following command (this is also [instructed in the wiki](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)):

```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

