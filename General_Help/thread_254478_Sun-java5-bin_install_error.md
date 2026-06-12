---
title: "Sun-java5-bin install error"
date: 2006-09-10
forum: General Help
---

### Post by ltkun on 2006-09-10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Could not create the Java virtual machine.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-08-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-bin
 sun-java5-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cannot install jdk or jre on dapper or edgy.

---

### Post by lukew on 2006-09-10
Could you show us what packages you are installing?!?

To install type:

sudo apt-get install sun-java5-jre sun-java5-plugin 

or 
sudo apt-get install sun-java5-jdk sun-java5-plugin 

for the jdk. No sure where the sun-java5-bin are.

They should all be in the multiverse!

If you are using jdk then you can download netbeans from sun site, this has the jdk in it or I always prefer JDE (Java Development For Emacs ) alongside ECB (Emacs Class Browser) Be sure to check them out.

I hope

Luke

---

### Post by ltkun on 2006-09-10
I cannot install jdk or jre using sudo apt-get install because of these errors.

---

### Post by lukew on 2006-09-10
I see, 'sun-java5-bin' in the TB, are you sure you are typing sun-java5-jdk.

Can post what you are typing?

Luke

---

### Post by thebasard on 2006-09-15
I'm having a similar problem getting java and jre installed on Edgy.  Here's the output of the apt-get install:

sudo apt-get install sun-java5-jre sun-java5-plugin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jre has no installation candidate

I've enabled all repos and added a few from the Edgy Guide but alas, java isn't available.

Any suggestions?

Cheers,
Clay

---

### Post by welshboy on 2006-09-16
Hi there,

risking a dumb question here but have you ensured that the repositories have been changed to multiverse?  Otherwise they won't install.

welshboy

---

### Post by PingunZ on 2006-09-16
I don't have the packages either on edgy.
And yes, I'm sure multiverse is enabled ;)

Cheers

---

