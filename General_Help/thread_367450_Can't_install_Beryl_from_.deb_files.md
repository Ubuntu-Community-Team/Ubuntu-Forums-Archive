---
title: "Can't install Beryl from .deb files"
date: 2007-02-22
forum: General Help
---

### Post by jaddi27 on 2007-02-22
Hi,
 
I have downloaded the required Beryl packages (.deb files) from their website. When I try to install Beryl using the beryl.deb package, it lists all the dependencies but doesn't install any of it. If I try to install any of the separate Beryl packages, the dependencies are listed but nothing is installed. Is there any way to install Beryl from the files that I downloaded? I am trying to use the 'dpkg' command to install it. The files that I downloaded, which include all of the dependencies, are all in a folder together.
 
I am using Ubuntu Edgy.
 
Thanks in advance,
 
Joel

---

### Post by maher on 2007-02-22
Hello there,
Installing Beryl is not that difficult, if follow the link below,

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) 

I don't understand why you would choose to perform a manual installation, (unless you don't have a permanent internet connection).
Anyway,
could please be more specific, how did you try to install the packages (dpkg -i ...)
which error did you get.

please copy/paste the messages

---

### Post by capdog on 2007-02-22
Why not just double-click each deb file in nautilus? That will open GDebi which will let you install each deb file one by one. 

There are also detailed installation instructions for edgy on the beryl project site, in the wiki section under installation. Can you try following those instructions to the letter and post your results?

---

### Post by jaddi27 on 2007-02-23
[SIZE=2]Hi,[/SIZE]

[SIZE=2]I am doing a manual installation because I don't have the internet connected to my Ubuntu computer.[/SIZE]

[SIZE=2]The command that I used to install Beryl was:[/SIZE]

[SIZE=2]dpkg -i beryl.deb[/SIZE]

[SIZE=2](The beryl.deb package is a package that installs all the necessary components)[/SIZE]
[SIZE=2]I executed this from a terminal at which the current working directory is set to the folder which contains all the beryl files I downloaded. [/SIZE]
[SIZE=2]The error message that I got listed all the components of beryl that would normally be installed by the beryl.deb package. After the name of each of the components it said that the component was not installed and the installation could not continue.[/SIZE]

[SIZE=2]I will paste the error messages soon, as I need to copy them from my Ubuntu machine.[/SIZE]

[SIZE=2]Joel[/SIZE]

---

### Post by nickoli_02 on 2007-02-23
The errors you're talking about are missing dependencies. Since you don't have an internet connection to your computer you'll have to transfer them all over manually from a computer with an internet connection, and install them all manually.

---

