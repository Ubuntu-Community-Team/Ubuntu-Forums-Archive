---
title: "office under wine?"
date: 2007-09-10
forum: General Help
---

### Post by yon2501 on 2007-09-10
so i have to use microsoft office 2007 for a class and i was just wondering if it will be able to run under wine? and before anyone suggests it no i cant use open office because the book teaches office 2007 so dont even bother suggesting it.

---

### Post by Maestro23 on 2007-09-10
Check here: [http://appdb.winehq.org/appview.php?iAppId=31](http://appdb.winehq.org/appview.php?iAppId=31)

---

### Post by bodhi.zazen on 2007-09-10
My advice is Crossover office :

[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Maestro23 on 2007-09-10
> **bodhi.zazen said:**
> My advice is Crossover office :

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Forgot about Crossover. Good catch.

---

### Post by yon2501 on 2007-09-10
ok yeah i think ill try crossover looks good.

---

### Post by yon2501 on 2007-09-12
ok so i tried to install the crossover trial using the install guide [here]("http://www.codeweavers.com/support/docs/crossover-standard-demo/install#install-mode") but on where it says to enter something into terminal for the first install type i get this message
>  mypc@mypc-laptop:~$ sh install-crossover-standard-demo-6.1.0.sh
sh: Can't open install-crossover-standard-demo-6.1.0.sh
so how do i install =\

---

### Post by Maestro23 on 2007-09-12
> **yon2501 said:**
> ok so i tried to install the crossover trial using the install guide [here]("http://www.codeweavers.com/support/docs/crossover-standard-demo/install#install-mode") but on where it says to enter something into terminal for the first install type i get this message

so how do i install =\

Try:

>  chmod +x filename.sh
 ./filename.sh

*filename = name of file you're trying to install.

The chmod command makes the file executable.

---

### Post by yon2501 on 2007-09-12
> **Maestro23 said:**
> Try:



*filename = name of file you're trying to install.

The chmod command makes the file executable.

well this is the file name 
> install-crossover-standard-demo-6.1.0.sh
and its in the temp folder so would i put the directory too (/temp/install-crossover-standard-demo-6.1.0.sh) ?
sorry i just want to be clear last time i wasnt clear i ended up fixing my computer for a day or two

---

### Post by Maestro23 on 2007-09-12
> **yon2501 said:**
> well this is the file name 

and its in the temp folder so would i put the directory too (/temp/install-crossover-standard-demo-6.1.0.sh) ?
sorry i just want to be clear last time i wasnt clear i ended up fixing my computer for a day or two

Yeah, or you could change directory to /temp (cd /temp) and then run the command.

I'm not sure where the program is going to install, you might want to copy the file over to your home directory and then execute it.

> cp install-crossover-standard-demo-6.1.0.sh /home/username

---

### Post by yon2501 on 2007-09-12
well code weavers says its suposed to install in "~/cxoffice." so i guess it makes a directory when it installs

---

### Post by yon2501 on 2007-09-12
ah ha that was it i just had to change the directory....im not good with terminal yet so i never would have thought of that, thanks man

---

### Post by Maestro23 on 2007-09-12
> **yon2501 said:**
> well code weavers says its suposed to install in "~/cxoffice." so i guess it makes a directory when it installs

Cool.  Run with it man. :guitar:

---

