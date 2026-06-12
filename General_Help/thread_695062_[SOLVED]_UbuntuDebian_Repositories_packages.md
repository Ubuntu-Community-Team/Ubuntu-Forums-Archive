---
title: "[SOLVED] Ubuntu/Debian Repositories packages"
date: 2008-02-12
forum: General Help
---

### Post by dstein on 2008-02-12
When in Aptitude or any other package managers, how can I see where programs will be installed to? For example, if I want to install package A, how can I see which directories or where on my system it will be after installation? Also, how can I check where a package that I've already installed is on my system.

Although I would like a general answer, the reason I ask is because I installed a package called cl-acl-compat and I have no idea where it is or how to find out.

Thanks for any help.

---

### Post by Sammi on 2008-02-12
All you need to know about software installation in Ubuntu: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by dstein on 2008-02-12
Thank you for the quick reply. I will go through that when I get home. On a similar note, is there any way to find out where programs are installed when compiling on my own using make and makefile? Does this info get recorded somewhere by the operating system, or would I just have to read through the makefiles to see what they are actually doing? Thanks.

---

### Post by PeterJS on 2008-02-12
The Filesystem Hireacical Standard defines what goes where and why:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by PeterJS on 2008-02-12
> **dstein said:**
> Thank you for the quick reply. I will go through that when I get home. On a similar note, is there any way to find out where programs are installed when compiling on my own using make and makefile? Does this info get recorded somewhere by the operating system, or would I just have to read through the makefiles to see what they are actually doing? Thanks.

By itself make won't record anything because it doesn't know how to. But there is a program named checkinstall that will lanuch make install and keep detailed records of what make install does, and then build and install a deb based on that.

---

### Post by zvacet on 2008-02-12
You can find packages you installed with several commands

```
whereis** packagename**
```

```
locate** packagename**
```

Or go to the top of filesystem with** cd /** command and type

```
sudo find / -name ***packagename***
```

---

### Post by oldos2er on 2008-02-12
In Synaptic Package Manager, click Status, Installed, right-click on a package and click Installed Files; this will show you where all the files in an installed package are.

---

### Post by dstein on 2008-02-13
What about removing software from my system that has been installed with a makefile? Is there any automated way of doing this or must I do this manually. Thanks to everyone for the previous replies.

---

### Post by zvacet on 2008-02-13
If you are thinking about compiled programs then easyer way to remove them is to go to the folder form wich you compiled them and run command

```
sudo make uninstall
```

---

### Post by dstein on 2008-02-13
oh perfect. So my last question follows: If I install something by compiling it with a makefile, I should not delete the makefile or the souce code if I would later want to remove the software with make? Actually, I could probably remove the source code if I held onto the makefile? This is my final inquiry on Ubuntu software installation. Thanks again.

---

### Post by zvacet on 2008-02-13
To be able to compile you have to unpack file.That make folder in wich you are compiling.Don´t remove that folder after you compiled program.If you have that folder easyer way to uninstall propgram is to do it from that folder as I described to you.

---

