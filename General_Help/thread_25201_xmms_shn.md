---
title: "xmms shn"
date: 2005-04-09
forum: General Help
---

### Post by dtranche on 2005-04-09
First off new to using xmms,but would like to play shn files with.

How do I go about installing this plugin 

tried apt-get install xmms-shn

Thanks

---

### Post by nad on 2005-04-09
The following repository needs to be add to the file (as root) /etc/apt/sources.list .

## RAREWARES REPOSITORY - xmms plugins
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./ 

Now, run ' apt-get update ' to reload the lists of available packages, then ' apt-get install xmms-shn '.

Dan M

---

### Post by dtranche on 2005-04-09
Dan thanks. 
 am new to debian, but I can't seem to find the deb utility. using kubuntu

I have checked with kynaptic but can't see anything that I would be missing.

Thanks again

Denis

---

### Post by nad on 2005-04-09
I'm afraid that I wasn't clear in my post.

Cut and paste the following two lines into the file ' /etc/apt/sources.list '.

## RAREWARES REPOSITORY - xmms plugins
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

This will add a search of this repository to your available packages list.

Now, run ' apt-get update ' to reload the lists of available packages, then ' apt-get install xmms-shn '.

Dan M

---

### Post by Kamesennin on 2007-08-11
Hi! 
I had the problem that when I try to install the .deb for xmms-shn from [http://www.rarewares.org/debian/packages/unstable]("http://www.rarewares.org/debian/packages/unstable") I saw an error. And I couldn't install the plug-in...
Then I tried to install the shorten plugin since source from xmms.org. I downloaded the tarball and when I configured [./configure] I received a lot of errors. many of them said that I hadn't installed xmms >=1.0.0; glib, gtk, etc. I knew I had installed these but only the binary packages not the devs, I installed each dev package of the errors that I see.. And voilà... The plugin was configured, compiled and installed without problems and now I can hear my Shorten files.\\:D/

---

