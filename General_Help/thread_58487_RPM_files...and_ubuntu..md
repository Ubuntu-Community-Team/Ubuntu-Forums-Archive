---
title: "RPM files...and ubuntu."
date: 2005-08-20
forum: General Help
---

### Post by floyd27 on 2005-08-20
i have seen in the guide that you can convert RPM files to deb ...
Is this something that is a good idea.
i mean if you can only find/get the RPm is it ok to use it...

Whats the benifit of not compilingfrom source anyway, im just getting used to all the different ways of installing and am now wondering why one way is perfered/better than another.
thanx guy/gals...

---

### Post by heimo on 2005-08-20
First make sure it's not already available as a deb.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

If you really, really have to use RPM, you can use program called alien to do that. It's best to use your distributions native package management from official repositories - other ways may lead to dependency problems. I'd put compiling from source ahead of using RPMs.

---

### Post by nad on 2005-08-20
If the dependencies are not unusual, it is okay. Beware of apps that wish to install different versions of libraries already installed in your system (the linux equivalent of dll hell).

Compiling from source will optimize the binary for your present system. The optimization is typically small and sometimes insignificant, especially if you have not optimized your system from the get go.

These apps will not be managed by your package manager unless you package them and then install the packages through your package manager.

---

### Post by jeremy on 2005-08-20
If you do want to use an .rpm, the command is:
alien -d programme.rpm
this will create programme.deb - then do:
sudo dpkg -i programme.deb to install.

---

### Post by floyd27 on 2005-08-20
thanx for the info guys..
I was wanting a tvlisting program.
i found one but it was RPM. 
im not too good with the dependancies thing.
i will give it a try it it works i will go ahead.
but if it askes me to do something im not too sure of ill let it go..meh..
thanx again..

---

