---
title: "Can't install any packages,"
date: 2007-12-02
forum: General Help
---

### Post by Emperor.Travis on 2007-12-02
Alright, here's the problem. Nothing I've tried to install has worked. It will always say either A.) The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator. 
 Or B.) There has been a problem during the installation of the following piece of software  and it never lists the software  

 So far the only things I've tried to install are, Kubuntu, Gstreamer extra plugins, and Flash Player 9. 
 
Anyone know the solution?

---

### Post by Mithrilhall on 2007-12-02
How are you trying to install said software; adept, terminal, etc.?

What is the output you're getting (errors)?

---

### Post by zvacet on 2007-12-03
It´s look like you don´t have admin privileges.Boot in recovry mode and type

```
adduser username admin
```


** username=your username**

---

