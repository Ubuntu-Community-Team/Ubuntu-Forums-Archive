---
title: "problem after installation  Pidgin 2.4.0"
date: 2008-03-07
forum: General Help
---

### Post by scoo007 on 2008-03-07
root@david-laptop:/home/david/Desktop/pidgin-2.4.0# pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error

can anyone help please?

---

### Post by Perfect Storm on 2008-03-07
First. Don't run with root access. Especially not IMs.

How did you install the Pidgin? By compiling? If so you may go back to check if any strange or error happen when doing it.

---

### Post by scoo007 on 2008-03-07
yes i installed by compiling.
i have no errors in the compiling.
--------------
i do only the make installation by root

---

### Post by Perfect Storm on 2008-03-07
ok, but you know it's a security risk to start the application up via root ;)


You might check my guide - [http://ubuntuforums.org/showthread.php?t=658244](http://ubuntuforums.org/showthread.php?t=658244)
Note it's a guide and you may enable/disable add/remove what you need etc.

---

### Post by zvacet on 2008-03-07
> **zvacet said:**
> No need for install from source.You can download latest version at [getdeb.](http://www.getdeb.net/)You can add getdeb as repository

```
gksudo gedit /etc/apt/sources.list
```

add this line

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

Save and close file.

```
sudo apt-get update
```

I hope it will work for you.

---

### Post by scoo007 on 2008-03-07
thank you. Ii will do it now!

---

### Post by scoo007 on 2008-03-07
ok.i installed pidgin 2.4.0 and then i have next error:
SSL support is needed for MSN.Please install a supported SSl library

---

### Post by scoo007 on 2008-03-07
please helpp please

---

### Post by kevdog on 2008-03-07
Type this at the command line to see if this helps:

sudo aptitude install libnss3-dev

---

### Post by scoo007 on 2008-03-07
the same error!

---

### Post by vikrant82 on 2008-03-07
I guess the latest debs for pidgin in hardy repos are built without SSL support. 

Pick up 2.4.0 debs from getdeb.net h[ere]("http://www.getdeb.net/app/Pidgin")

---

### Post by scoo007 on 2008-03-07
I Downloaded the files and reinstall.
but i have the same Error!!!

---

### Post by scoo007 on 2008-03-07
also i think that i can Add SSL servers in Certificate Manager???
but where i can fild PEM sertification??

---

### Post by scoo007 on 2008-03-07
Also I reinstall pidgin and there is no new!
the same error!

---

### Post by scoo007 on 2008-03-07
I found the answer!!!
all you nedd is to type 
> ./configure --enable-nss=yes,no,static

and its work!!!!!

---

### Post by steveneddy on 2008-03-07
> **scoo007 said:**
> I found the answer!!!
all you nedd is to type 


and its work!!!!!

Sweet!

---

### Post by samkline on 2008-03-09
Nvm. Sorry :p

---

