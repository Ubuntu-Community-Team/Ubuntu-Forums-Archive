---
title: "How to login to MySQL in XAMPP"
date: 2006-11-12
forum: General Help
---

### Post by thenetduck on 2006-11-12
Hi, 
  I am trying to learn about databases and installed xamp to do this. I don't know how to connect to my mysql database so I can play around with it. Does anyone know how I can do this? I have everything running, I just don't know how to access anything. Thanks,
   
The Net Duck

---

### Post by insulae on 2006-11-12
you must to start lampp, go to the lampp directory and run:

```
sudo ./lampp start 
```

then open a webbrowser (firefox, konqueror, etc) and put in the address:

```
http://localhost or http://127.0.0.1
```

at this moment you must see a XAMPP logo, chose your language.
after that you will see a "local xampp web page" go to the "phpMyAdmin" option, with this tool you can use MySQL.

(sorry for my english :) )

---

### Post by thenetduck on 2006-11-14
Thanks, 
  Is there a way to just navigate to the sql databases and edit them through the terminal ?
 
 The Net Duck

---

### Post by insulae on 2006-11-15
yes, you can use all mysql command with XAMPP, you must to change the command path only.

for example: i have my XAMPP in /opt/lampp/ so if i want to login (from console) into mysql i must run:
```
/opt/lampp/bin/mysql -u root -p
``` or i can go to ```
/opt/lampp/bin
``` and run there ```
./mysql -u root -p
```

Regards
insulae

---

### Post by j1n3l0 on 2007-04-06
hi,

i'd like to add another question along the same lines! i have xampp installed at location

```
/opt/lampp 
```

and i access mysql from the shell by typing

```
/opt/lampp/bin/mysql -u root -p
```

my question is how can i set my PATH or whatever i need to do so that i can access mysql from any where on the shell like so

```
/home/mysql -u root -p
```

your help is much appreciated

Nelo

---

### Post by j1n3l0 on 2007-04-12
I found the answer! :D 

I tried it and it works on other executables (even an executable hello.pl script). Just do the following:

step 1: change to your local bin directory

```
cd /usr/local/bin
```

step 2: in this directory, create a symbolic link to the executable script

```
sudo ln -s /path/to/executable.script
```

And that's it! Now test it from any old directory ;)

---

### Post by DouglasAWh on 2008-03-17
mark solved?

---

