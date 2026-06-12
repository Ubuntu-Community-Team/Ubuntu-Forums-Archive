---
title: "SVN + Apache2"
date: 2005-07-24
forum: General Help
---

### Post by Sniper PT on 2005-07-24
Someone can help me to install last Subversion version (1.2.1) and web_dav module?

I have try that:

Download the source of SVN 1.2.1
extract
./configure
sudo make
sudo make install

to install apache2 i have make that:
sudo apt-get install apache2

but i'm doing something wrong... someone can say how i install correctly that 2 packages or put here some nice tutorial...  ;-) 

Thanks!

---

### Post by DJ_Max on 2005-07-24
The problem with binaries is that they're build against other binaries. You will probably run into problems when trying to get the mod_dav Apache module to work with SVN, since your Apache installation is a pre-built binary, and your SVN installation isn't. You should either install Apache2 from source, or install SVN from binary.

---

### Post by Sniper PT on 2005-07-24
I'm newbie, so the better solution is use the pre-built binary, but the version 1.2.1 of SVN don't have pre-built binary....

---

### Post by DJ_Max on 2005-07-24
[QUOTE=Sniper PT]I'm newbie, so the better solution is use the pre-built binary, but the version 1.2.1 of SVN don't have pre-built binary....[/QUOTE]
 Have you tried the backports?

---

### Post by Caboto on 2005-07-24
I've tried Subversion some time ago, too. But never got it running with Apache2. Somehow I don't really know, which Module to bind in or what to compile with extra parameters...
I would love to get some help, too. ;) Perhaps with a nice How-To or a easy to understand instruction.

---

### Post by DJ_Max on 2005-07-24
I've installed both subversion & Apache 2 from source on my server, but don't have them bind, because I don't need them to. I would guess you need to install mod_dav. Try to Google around.

---

### Post by Sniper PT on 2005-07-25
I have create a tutorial right now...

See [here](http://www.ubuntuforums.org/showthread.php?p=270756).

---

### Post by Sniper PT on 2005-07-25
[QUOTE=DJ_Max]Have you tried the backports?[/QUOTE]
Yes... the last version is 1.1.3 and not 1.2.1..

---

### Post by Gehaktbal on 2005-07-25
There is no need to install webdav? Libapache2-svn is enough?

---

### Post by Sniper PT on 2005-07-25
Yes... libapache2-svn will install dav_svn.... after that you only need edit dav_svn configuration file and restart apache.

---

