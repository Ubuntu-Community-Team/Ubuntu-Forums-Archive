---
title: "Citadel has dependency issues"
date: 2008-04-23
forum: General Help
---

### Post by ChumleyEX on 2008-04-23
Hope this is in the proper area.. Here we go!

sudo apt-get install citadel-suite 

gives me 

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  citadel-suite: Depends: citadel-webcit but it is not going to be installed
E: Broken packages

```

if I 
sudo apt-get install citadel-webcit 
I get 


```
The following packages have unmet dependencies:
  citadel-webcit: Depends: libjs-prototype but it is not installable
E: Broken packages

```

But with the other stuff above it. 

Then I do 

sudo apt-get install libjs-prototype

dun dun dduuuuuun

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libjs-prototype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libjs-prototype has no installation candidate

```

 A brief history..

I added the citadel package to the source list and isntalled it, configured it and even was able to send email out. Then I did something stupid and put the wrong ip somewhere and wasn't able to get into webcit. I didn't know what to do so I uninstalled (using these instructions [http://www.citadel.org/doku.php/faq:installation:how_do_i_uninstall_citadel]("http://www.citadel.org/doku.php/faq:installation:how_do_i_uninstall_citadel")) it all and then tried to reinstall and got this evil most hateful message. 

Help?

---

### Post by I Use Dial on 2008-04-23
I have the exact same problem but I have no previous installation.  Sure looks like a nice app...

---

### Post by ChumleyEX on 2008-04-23
I'm really suprised that their isn't and answer yet.

---

### Post by ChumleyEX on 2008-04-24
I went right to citadels support and they knew what to do. 


Thu Apr 24 2008 09:51:05 AM EDT from dothebart @uncnsrd [Reply] [ReplyQuoted] [Headers][Print]
Subject: Re:I'm having install problems.
hm, i tried to add it from lenny into the repo.. maybe i forgot one of them?

please fetch

 [http://debian.citadel.org/debian/etch/libjs-prototype_1.6.0.2-3_all.deb](http://debian.citadel.org/debian/etch/libjs-prototype_1.6.0.2-3_all.deb)

and do dpkg -i  libjs-prototype_1.6.0.2-3_all.deb

and rerun the apt.

---

