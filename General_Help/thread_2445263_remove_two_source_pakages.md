---
title: "remove two source pakages"
date: 2020-06-11
forum: General Help
---

### Post by Hotchilli on 2020-06-11
with the command apt-get build-dep libapache2-mod-python libapache2-mod-wsgi 
these were installed

what is the command to remove them?

---

### Post by CelticWarrior on 2020-06-11
The command to install was actually 'apt-get install <package>'.
The command to uninstall is therefore 'apt-get remove <package>.

---

### Post by Hotchilli on 2020-06-17
ok thankyou however if you read the first post in this thread i wrote



   " with the command apt-get build-dep libapache2-mod-python libapache2-mod-wsgi "

note build-dep and NOT install

so when i run

root@mail:~# sudo apt-get remove libapache2-mod-python libapache2-mod-wsgi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libapache2-mod-python' is not installed, so not removed
Package 'libapache2-mod-wsgi' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.


how to remove these two packages please?

---

### Post by CelticWarrior on 2020-06-17
"not installed, so not removed" means it's not installed therefore it doesn't need to be removed.

[https://askubuntu.com/questions/324845/whats-the-difference-between-apt-get-install-and-apt-get-build-dep](https://askubuntu.com/questions/324845/whats-the-difference-between-apt-get-install-and-apt-get-build-dep)

Please pay attention to the terminal output, namely error messages.

---

### Post by Hotchilli on 2020-06-19
thankyou for the url

thing ever since doing this command

build-dep libapache2-mod-python libapache2-mod-wsgi 

for some reason apache2 will not restart

i was following this a howto to get mod_python installed 

so maybe the best way forward is to remove apache2 as its onlly the "it work" page
and then intall again and hope the problem resolves itself

---

