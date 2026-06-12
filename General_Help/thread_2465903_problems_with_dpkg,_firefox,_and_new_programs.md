---
title: "problems with dpkg, firefox, and new programs"
date: 2021-08-14
forum: General Help
---

### Post by eliyahu22 on 2021-08-14
Hello, I have Ubuntu 20.04, and when I want to install new programs, or when I want to remove firefox, because I have problems with it, I get this message:      	 	 	 	   E: dpkg was interrupted, you must manually run ‘dpkg –configure – a’ to correct the problem

When I type that command in the terminal, I get this:  'error: need an action option'

How do I solve this?

---

### Post by deadflowr on 2021-08-14
Looks like dashes issue.
Yours shows as 
```
dpkg &#8211;configure &#8211; a
```
should be
```
sudo dpkg --configure -a
```
Note the configure has two dashes and the -a option only has one.

---

### Post by eliyahu22 on 2021-08-14
> **deadflowr said:**
> Looks like dashes issue.
Yours shows as 
```
dpkg –configure – a
```
should be
```
sudo dpkg --configure -a
```
Note the configure has two dashes and the -a option only has one.

I tried that, and nothing seems to be happening in the terminal, I just get another command line.   But my comp seems to be behaving better.   I can now install new programs, and I think the problem with firefox was caused by addons.  I disabled almost all of 'm, and firefox is acting normal now. 

Thanks.

---

### Post by Impavidus on 2021-08-15
> **eliyahu22 said:**
> I tried that, and nothing seems to be happening in the terminal, I just get another command line.
That means that dpkg ran, found nothing to fix and terminated.

---

### Post by ActionParsnip on 2021-08-15
Sounds good. What is the output of:
```

sudo apt update
sudo apt -f install
sudo apt upgrade

```

---

### Post by ActionParsnip on 2021-08-15
In Linux, if you get no output then the command ran. No news is good news

---

