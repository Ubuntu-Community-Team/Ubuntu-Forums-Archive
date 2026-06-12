---
title: "How to install Java *without* apt-get?"
date: 2008-06-30
forum: General Help
---

### Post by yamokosk on 2008-06-30
Riddle me this.. how am I suppose to install Java support in Hardy without apt-get. Why no apt-get? My company uses a Java applet to authenticate users on the network.. No java on my system -> No java plugin -> No internet access -> No apt-get.

I tried downloading all of the required sun-java packages and the installing was going fine until I hit sun-java6-jre and sun-java6-bin.. which seem to have inter-dependencies on each other:

[http://packages.ubuntu.com/hardy/sun-java6-jre](http://packages.ubuntu.com/hardy/sun-java6-jre) 

[http://packages.ubuntu.com/hardy/sun-java6-bin](http://packages.ubuntu.com/hardy/sun-java6-bin)

So what's the answer? I thought about burning a DVD of all the entire Hardy release but isn't there something easier?

---

### Post by prince_niceguy on 2008-06-30
download jre from sun and run the file using root. then it should configure your browser.

---

### Post by prince_niceguy on 2008-06-30
better still... download and follow the instruction [here]("http://www.java.com/en/download/help/5000010500.xml#100")...

---

### Post by forger on 2008-06-30
If you have a usable desktop running hardy, the following should download the packages to the current directory:
```
sudo aptitude download sun-java6-jre unixodbc java-common sun-java6-bin

```

I believe that's what you will need to transfer to your work and install in this order:
java-common
unixodbc
sun-java6-bin
sun-java6-jre

---

### Post by forger on 2008-07-01
(ignore this post)

---

### Post by kuja on 2008-07-01
> **yamokosk said:**
> Riddle me this.. how am I suppose to install Java support in Hardy without apt-get. Why no apt-get? My company uses a Java applet to authenticate users on the network.. No java on my system -> No java plugin -> No internet access -> No apt-get.

I tried downloading all of the required sun-java packages and the installing was going fine until I hit sun-java6-jre and sun-java6-bin.. which seem to have inter-dependencies on each other:

[http://packages.ubuntu.com/hardy/sun-java6-jre](http://packages.ubuntu.com/hardy/sun-java6-jre) 

[http://packages.ubuntu.com/hardy/sun-java6-bin](http://packages.ubuntu.com/hardy/sun-java6-bin)

So what's the answer? I thought about burning a DVD of all the entire Hardy release but isn't there something easier?

try adding both of them to the install line, ie: sudo dpkg --install packageone.deb packagetwo.deb. That might work.

---

### Post by forger on 2008-07-01
> **kuja said:**
> try adding both of them to the install line, ie: sudo dpkg --install packageone.deb packagetwo.deb. That might work.

true, but he needs dependencies such as java-common and several others

---

### Post by kuja on 2008-07-01
> **forger said:**
> true, but he needs dependencies such as java-common and several others

Throw them on the line too :)

---

### Post by prince_niceguy on 2008-07-01
it would be much easier to install using #3 and see if it works. i understand the purpose of using repo is to have supported software, but wihtout internet i have found it too big problem to resolve all the dependency and download them on other comp.

---

### Post by forger on 2008-07-01
> **prince_niceguy said:**
> it would be much easier to install using #3 and see if it works. i understand the purpose of using repo is to have supported software, but wihtout internet i have found it too big problem to resolve all the dependency and download them on other comp.

By the way, do you have sudo / superuser / administrator priviledges on that computer? Because if you don't, you won't be able to install anything!

---

### Post by dburnett77 on 2008-07-01
Use synaptic and select jre.  That's the run-time environment.  It'll grab everything.

---

### Post by jamesstansell on 2008-07-03
> **yamokosk said:**
> 
I tried downloading all of the required sun-java packages and the installing was going fine until I hit sun-java6-jre and sun-java6-bin.. which seem to have inter-dependencies on each other:


The key package you need is sun-java6-plugin.  Did you get that one?

Also, if you have icedtea-gcjwebplugin installed you should remove it so firefox doesn't run that plugin instead.

I agree that getting the bin file from java.com would likely be your easiest route to installing a working plugin.

---

