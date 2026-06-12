---
title: "Lamp setup"
date: 2006-09-04
forum: General Help
---

### Post by eyedol on 2006-09-04
Hi all,
I have downgraded from php5 to php4 because I'm to do a demonstration on kewl.nextgen which requires php4 to run. In effect of this, I uninstall all php5 and it related extensions I have installed. After, I did,
```
sudo apt-get install php4 libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin
``` when I browse localhost, it prompts me to download php which is because php module is not loaded by apache but I have **libapache2-mod-php4** installed which to me it should work because it just worked with my previous **php5, lipapache2-mod-php5** installed. To cut my long description short, please I want to know why php is not working and how can I make it work? Thanks

---

### Post by cantormath on 2006-09-04
> **eyedol said:**
> Hi all,
I have downgrade from php5 to php4 because I'm to do a demonstration on kewl.nextgen which requires php4 to run. In effect of this, I uninstall all php5 and it related extensions I have installed. After, I did,
```
sudo apt-get install php4 libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin
``` when I browse localhost, it prompts me to download php which is because php module is not loaded by apache but I have **libapache2-mod-php4** installed which to me it should work because it just worked with my previous **php5, lipapache2-mod-php5** installed. To cut my long description short, please I want to know why php is not working and how can I make it work? Thanks

did you uninstall php5?

---

### Post by eyedol on 2006-09-04
Yes I did.

---

