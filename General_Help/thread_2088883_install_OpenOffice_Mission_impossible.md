---
title: "install OpenOffice: Mission impossible"
date: 2012-11-27
forum: General Help
---

### Post by Tabb on 2012-11-27
So i'm running Ubuntu 12.10 and i'm trying to install OpenOffice.

I downloaded the .tar.gz package and i'm just finding it impossible to find information on how to install it. I got to the ./configure stage in terminal and couldn't get past it as it was coming up with a error.

Can somebody give me a simple method of installing openoffice? It's not in my software center either!

Thanks!

---

### Post by MG&amp;TL on 2012-11-27
Why OpenOffice instead of LibreOffice? (obviously if you've got a reason, good, but otherwise you're probably better with Libre)

What error is it giving? Likely you have not installed all of the required development files. :)

---

### Post by wyliecoyoteuk on 2012-11-27
I think that you will have to remove Libreoffice. Not sure if they can both be installed.

This link has the info you need.

[http://ubuntuforums.org/showthread.php?t=2071020](http://ubuntuforums.org/showthread.php?t=2071020)

---

### Post by sgage on 2012-11-29
> **Tabb said:**
> So i'm running Ubuntu 12.10 and i'm trying to install OpenOffice.

I downloaded the .tar.gz package and i'm just finding it impossible to find information on how to install it. I got to the ./configure stage in terminal and couldn't get past it as it was coming up with a error.

Can somebody give me a simple method of installing openoffice? It's not in my software center either!

Thanks!

When you unpack the tar.gz file, you should find a directory 'DEBS'. In a terminal, cd to that directory and type 'sudo dpkg -i *.deb'. Then cd to directory 'desktop-integration' (which is in DEBS), and do the 'sudo dpkg -i *.debs' again (this gives you the icons and launchers and whatnot).

I know of no easier way of installing it, but it's not really that difficult. You will need to remove Libreoffice first.

---

### Post by vasa1 on 2012-11-29
> **Tabb said:**
> So i'm running Ubuntu 12.10 and i'm trying to install OpenOffice.

I downloaded the .tar.gz package and i'm just finding it impossible to find information on how to install it. I got to the ./configure stage in terminal and couldn't get past it as it was coming up with a error.

Can somebody give me a simple method of installing openoffice? It's not in my software center either!

Thanks!
Which version are you trying to install?
Where did you get it from? [http://www.openoffice.org/download/](http://www.openoffice.org/download/) is the official download site.
After you uncompress the .tar.gz there maybe a README file with instructions.
I'm not sure that it is necessary to uninstall LibreOffice. I understand that recent versions of Apache OpenOffice and LibreOffice can co-exist.

---

### Post by claracc on 2012-11-29
You will have to uninstall libreoffice first.

Here, [http://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=50119](http://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=50119) there is an excellent guide explaining howto install new apache openoffice in ubuntu.

Also I have read that it is possible to install apache openoffice from a ppa: [http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html](http://www.upubuntu.com/2012/05/how-to-install-apache-openoffice-34-via.html). Perhaps this is an easier way but I think you have to uninstall libreoffice too.

---

