---
title: "Apt not updating (Focal)"
date: 2021-05-12
forum: General Help
---

### Post by electroconvulsive on 2021-05-12
I have a problem with one of machines where it says that it is always up to date. It only happens on this one computer. I have a laptop that runs focal as well and the problem is not reproduced there.
When I run sudo apt update I get the following output. 
```
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```
As you can see it just hits the main server address and that is it. I have had this problem in the past and was advised to change the update server to the main server which worked back then. This is using the main server and I have tried several other mirrors without success. Thanks in advance for any help given.

---

### Post by dino99 on 2021-05-13
You might glance at its /etc/apt/sources.list to be sure none of the entry lines are blacklisted

---

### Post by electroconvulsive on 2021-05-13
The output of my sources list
```
cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu focal universe restricted multiverse main
```
All of the sources except for source code are selected under the Ubuntu Software tab in Software and Updates.

Edit: I updated my sources.list from this thread. 
[https://askubuntu.com/questions/443036/what-is-the-correct-output-of-cat-etc-apt-sources-list](https://askubuntu.com/questions/443036/what-is-the-correct-output-of-cat-etc-apt-sources-list)
It seems to have solved the problem. It is now updating

---

### Post by ajgreeny on 2021-05-13
> **electroconvulsive said:**
> The output of my sources list
```
cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu focal universe restricted multiverse main
```
All of the sources except for source code are selected under the Ubuntu Software tab in Software and Updates.
Is that all of it?

There should be many more entries in the sources.list file than just that single line.
Here's my version with all .src lines omitted along with a few manually added extras.
NB:  I use the gb archives, being in the UK
```
deb http://gb.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ focal universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

```
You could try replacing your sources.list file with mine temporarily (delete the ***gb.*** from lines if you want to use the main repos) and see if that works for you.
Alternatively there is an example sources.list file at /usr/share/doc/apt/examples/sources.list that you could try.
```
# See sources.list(5) manpage for more information
# Remember that CD-ROMs, DVDs and such are managed through the apt-cdrom tool.
deb http://us.archive.ubuntu.com/ubuntu focal main restricted
deb-src http://us.archive.ubuntu.com/ubuntu focal main restricted

deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb-src http://security.ubuntu.com/ubuntu focal-security main restricted

deb http://us.archive.ubuntu.com/ubuntu focal-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu focal-updates main restricted
```

EDIT:
Too late I see!

Please mark as SOLVED  from the Thread Tools at the top of this thread.
It's a great help to other users searching the forum.

---

