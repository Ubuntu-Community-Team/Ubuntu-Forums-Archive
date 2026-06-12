---
title: "error installing J2DK documentation."
date: 2007-11-07
forum: General Help
---

### Post by 127.0.0.1 on 2007-11-07
Hello ubuntu forums! i am trying to install wine, so i can run some of my windows applications in ubuntu (is that legal?) anyway, before that i installed sun java, apperently there was an error installing one of the files java worked fine anyway so i ignored it. however sudo still wants to install the file and is unable to:

```
root@Homebox:~# sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
The following packages were automatically installed and are no longer required:
  ktip kdeprint kpager klipper ksmserver ksysguard kmenuedit ksplash arts
  poster khelpcenter ksysguardd psutils kpersonalizer kdelibs kappfinder
  kdepasswd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java5-doc (1.5.0-13-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.5.0/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

a soloution is needed thank you :)

---

### Post by 127.0.0.1 on 2007-11-07
could really use some help on this.

---

### Post by 127.0.0.1 on 2007-11-08
Hello, cant install anything from sudo or synaptic package manager here! need a solution!

---

### Post by mariusdumi on 2007-11-10
Did you try 
```
sudo apt-get autoremove
```
and if so, could you post the result ?

---

