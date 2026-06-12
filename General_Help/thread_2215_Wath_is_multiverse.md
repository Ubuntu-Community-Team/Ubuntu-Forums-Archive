---
title: "Wath is multiverse ?"
date: 2004-10-26
forum: General Help
---

### Post by BlackFenix on 2004-10-26
> The Ubuntu software repository contains thousands of software packages organised into three "components", on the basis of the level of support we can offer them, and whether or not they comply with our Free Software Philosophy. The components are called "main", "restricted" and "universe". 

well... and multiverse ?

---

### Post by Rancoras on 2004-10-26
Multiverse is non-free stuff

---

### Post by flygmaskin on 2004-10-26
[QUOTE=Rancoras]Multiverse is non-free stuff[/QUOTE]
 Then whats the difference between restricted and multiverse?

---

### Post by elwis on 2004-10-26
[QUOTE=flygmaskin]Then whats the difference between restricted and multiverse?[/QUOTE]
 And where do you turn "multiverse" on?

---

### Post by flygmaskin on 2004-10-26
[QUOTE=elwis]And where do you turn "multiverse" on?[/QUOTE]
 deb [http://ftp.acc.umu.se/mirror/ubuntu/](http://ftp.acc.umu.se/mirror/ubuntu/) warty main restricted  multiverse
deb-src [http://ftp.acc.umu.se/mirror/ubuntu/](http://ftp.acc.umu.se/mirror/ubuntu/) warty main restricted multiverse

Or whatever mirror you want to use.

---

### Post by elwis on 2004-10-26
[QUOTE=flygmaskin]deb [http://ftp.acc.umu.se/mirror/ubuntu/](http://ftp.acc.umu.se/mirror/ubuntu/) warty main restricted  multiverse
deb-src [http://ftp.acc.umu.se/mirror/ubuntu/](http://ftp.acc.umu.se/mirror/ubuntu/) warty main restricted multiverse

Or whatever mirror you want to use.[/QUOTE]
 Thanks!
I better get myself another mirror though, this one always stops at 4% whatever it is I try to apt-get.

---

### Post by ubuntu-geek on 2004-10-26
this one works good for me.

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse

---

### Post by Rancoras on 2004-10-26
[QUOTE=flygmaskin]Then whats the difference between restricted and multiverse?[/QUOTE]

Clarification: Restricted is non-free but officially supported
                     Multiverse is non-free and unsupported

---

### Post by flygmaskin on 2004-10-26
[QUOTE=Rancoras]Clarification: Restricted in non-free but officially supported
                     Multiverse is non-free and unsupported[/QUOTE]
 Ah, thanks

---

