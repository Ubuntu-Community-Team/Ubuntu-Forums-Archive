---
title: "problem when installing software"
date: 2007-06-06
forum: General Help
---

### Post by seedsca on 2007-06-06
A while back I was doing a software update and my computer crashed (I think that's how it began)
Now whenever I use adept manager or any other package mannager I get errors.

in adept manager the out put is this:

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.. 

konsole output when doing a:

sudo dpkg --configure -a
Setting up libmagic1 (4.17-2ubuntu1.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libmagic1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of file:
 file depends on libmagic1 (= 4.17-2ubuntu1.1); however:
  Package libmagic1 is not configured yet.
 file depends on libmagic1; however:
  Package libmagic1 is not configured yet.
dpkg: error processing file (--configure):
 dependency problems - leaving unconfigured
Setting up avidemux (2.3.0-0.0ubuntu3~edgy1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing avidemux (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libtool:
 libtool depends on file; however:
  Package file is not configured yet.
dpkg: error processing libtool (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmagic1
 file
 avidemux
 libtool

all the software installs fine but I get these messages EVERY time. very annoying... 
anyone ever encounter this?

---

### Post by NeoLithium on 2007-06-06
Are you able to dkpg --configure libmagic1 first?  It might work, I have no idea, but it's just a shot in the dark ;)

---

### Post by seedsca on 2007-06-07
It did not work either, but thanks

# dpkg --configure libmagic1
Setting up libmagic1 (4.17-2ubuntu1.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libmagic1 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libmagic1

---

### Post by seedsca on 2007-06-09
I'll see if I can find some logs or something. Or I guess I just might have to re-install.

---

