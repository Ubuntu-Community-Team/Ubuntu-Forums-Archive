---
title: "J2se Jdk"
date: 2005-06-07
forum: General Help
---

### Post by mightymartianca on 2005-06-07
I'm looking to install Netbeans 4.1, and need the J2SE JDK.  It doesn't look too bad to install, but I was wondering of there was an Ubuntu or Debian version of the package out there?  If not, then I guess about the only thing I need to do is update the Java plugin in Firefox, correct?

---

### Post by xao on 2005-06-07
point your browser to:

 [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) 

follow the instructions he gives (i dont remember if you need to add repositories, but he tells you how).

its a pretty simple process once you ahve his instructions. it installs the plugin for firefox as well as java app support for anything that requires java.


xao

---

### Post by mightymartianca on 2005-06-07
[QUOTE=xao]point your browser to:

 [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) 

follow the instructions he gives (i dont remember if you need to add repositories, but he tells you how).

its a pretty simple process once you ahve his instructions. it installs the plugin for firefox as well as java app support for anything that requires java.


xao[/QUOTE]

I've already installed that, but I'm looking to install the SDK.

---

### Post by CospeFogo on 2005-06-07
[QUOTE=mightymartianca]I'm looking to install Netbeans 4.1, and need the J2SE JDK.  It doesn't look too bad to install, but I was wondering of there was an Ubuntu or Debian version of the package out there?  If not, then I guess about the only thing I need to do is update the Java plugin in Firefox, correct?[/QUOTE]
 Go for the standard package you find at Sun. It is really simple to install. It takes 2 commands: 
1st chmod it:

```
chmod 755 jdk-1_5_03-nb-4_1-linux.bin
```

2nd run it:

```
./jdk-1_5_03-nb-4_1-linux.bin
```

---

### Post by jobezone on 2005-06-07
Perhaps this is the package you need: sun-j2sdk1.5 
It's in backports, the hoary-extras branch.

---

### Post by [pl]ice on 2005-06-07
get it from backports; i had problems with installing it by hand, i think i wasn't linked fully.

---

### Post by omegasoul on 2005-06-08
I use netbeans for all my java programming needs, (apps, handheld, networking and DIP). When I  decided to leave Windows for Ubuntu I found it very easy to just install netbeans and the JDK from netbeans.org. I was a linux user for about two weeks when I installed netbeans.

---

