---
title: "Argus not found"
date: 2008-01-27
forum: General Help
---

### Post by homecomputeraid on 2008-01-27
I'm trying to use a program called Argus to analyze a log file for a class I'm taking.  I've tried to install Argus several times.  I've uninstalled, and reinstalled, but can't get it to run.  Please see transcript below:

ted@ted-desktop:~/scan27$ argus -X -r sotm27 -w sotm27.argus
The program 'argus' is currently not installed.  You can install it by typing:
sudo apt-get install argus-server
bash: argus: command not found
ted@ted-desktop:~/scan27$ 
ted@ted-desktop:~/scan27$ sudo apt-get install argus-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
argus-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ted@ted-desktop:~/scan27$ argus -X -r sotm27 -w sotm27.argus
The program 'argus' is currently not installed.  You can install it by typing:
sudo apt-get install argus-server
bash: argus: command not found
ted@ted-desktop:~/scan27$ 

I'm running Ubuntu 7.10 in a VMware Workstation 6.02 virtual machine on a Windows XP Professional laptop.

I need this to work for a presentation on Monday if possible.

Thanks!

---

### Post by gvartser on 2008-01-27
try:
```
sudo apt-get install argus-client
```

/g

---

### Post by homecomputeraid on 2008-01-27
I have client installed too.

Thanks

---

### Post by gvartser on 2008-01-27
The thing is that argus-server installs the binary "argus" into /usr/sbin.

Maby this is not in your path:

try:
```
/usr/sbin/argus -X -r sotm27 -w sotm27.argus
```


To find out the files owned by a installed package you can execute the following command:
```
dpkg-query -L <package-name>
```

/G

---

### Post by gvartser on 2008-01-27
Oops, something is wrong with the package i guess.

Just checked the 
/usr/sbin/argus, this is soft link to /usr/sbin/argus_linux" , but this file does not exist.
So running argus wont be possible anyways. 

Sorry about that..

This must be a package bug, maby there is an later release that you can download and compile.


I tested to download an older version (.deb) package and installed. That one seamed to work.
But then I don not know what to do with the program, so I cant test it properly. But now i can run the executable.. ;)

[http://packages.debian.org/etch/argus-server](http://packages.debian.org/etch/argus-server)

While downloading choose to open with "Package Installer" and this will do the rest.

NOTE!
Remove the previous installation of argus-server before proceeding.
```
apt-get remove argus-server
```

/g

---

