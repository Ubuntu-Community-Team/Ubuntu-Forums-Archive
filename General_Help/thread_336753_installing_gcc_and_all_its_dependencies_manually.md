---
title: "installing gcc and all its dependencies manually"
date: 2007-01-12
forum: General Help
---

### Post by fouadk on 2007-01-12
hey all

i installed ubuntu and i have a pppoe connection but it doesnt work with pppoeconfig, i have to install for it roaring penguin but roaring penguin require gcc so i have to install that manually because i cant install it using synaptic....

how can i know what packages to download inorder to install them because gcc require other dependant packages to run so my question is is there is some way to know requersively all the packages needed by gcc ????

Thanks in advance

---

### Post by swatkatzin on 2007-01-29
i too am facing the same problem. i want to configure my internet connection using rp-pppoe.

the ./go-gui in rp-pppoe fails beacuse of inavailablity of C compiler.

i have searched the forum for the problem, but the soln i found>synaptic didnt work.

I need help in installing compilers and getting my internet cnnection working,

Please shed some light on this.
Thanks so much

This is my first post here....this forum rocks!

---

### Post by taurus on 2007-01-29
You don't need internet connection to install gcc.  It's on the CD.

Insert the CD into the drive and open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by swatkatzin on 2007-01-30
THanks

i managed to install rp-pppoe and gcc

the GUi comes up but when i enter my id and password and start connection

it says timed out 

i am not able to ping anything

I have entered a static ip in networking(Administration)

Please help...

---

