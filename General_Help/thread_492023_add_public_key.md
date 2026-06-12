---
title: "add public key"
date: 2007-07-04
forum: General Help
---

### Post by ronbrooks on 2007-07-04
I am trying to add a public key so I can down load a program and use it but it will not let me add the key as I was instructed to do on their web site. This is the line that it keep telling me to use and it is not working.

    deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main

respectively to your /etc/apt/sources.list file (you can also use edgy or feisty instead of dapper depending on the Ubuntu release you use) and add the public key used for signing wxWidgets packages to the list of keys trusted by apt using the command

    curl [http://www.tt-solutions.com/vz/key.asc](http://www.tt-solutions.com/vz/key.asc) | apt-key add -

and run apt-get update. You can then use apt-cache search --names-only wx\*2.8 command to see the available packages.

I was able to install the source list ok but I can't get the Key to install.  Dose anyone know what I am doing wrong to get the key installed. Is the command wrong on this page to get the key installed.  I am using Ubuntu 7.04. 

Thanks for any help.

---

### Post by Computer-Slave on 2007-07-04
U can generate a public key by commmand

> gpg --gen-key

---

### Post by Nythain on 2007-07-04
try throwing a sudo in front of apt-key add - so it looks more like this

curl [http://www.tt-solutions.com/vz/key.asc](http://www.tt-solutions.com/vz/key.asc) | sudo apt-key add -

---

### Post by ronbrooks on 2007-07-04
This is what I get when I use that command

Password:bash: curl: command not found

I will try the other sugestion and see if that one will work.

---

### Post by mig5 on 2007-07-04
> **ronbrooks said:**
> This is what I get when I use that command

Password:bash: curl: command not found

I will try the other sugestion and see if that one will work.

Do this first:```
 sudo apt-get install curl
```

---

### Post by ronbrooks on 2007-07-04
Mig5 thanks very much that worked and now I will see if I can get the rest loaded and get the program to work. I will keep my fingers crossed on that.

---

