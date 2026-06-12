---
title: "apt-get can't acquire w32codecs"
date: 2005-10-02
forum: General Help
---

### Post by chess007 on 2005-10-02
sudo apt-get install w32codecs won't work for me. :P It says,"

Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not avaliable, but isreferred to by another package. This may mean that the package is missing, has been obsoleted, or is only avaliable from another source.
E: Package w32codecs has no installation candidate


How can I get this to install? I have updated the apt sources list according to the ubuntu starter guide.

How can I get this to install? I have updated the apt sources list according to the ubuntu starter guide. I also added

deb [http://public.planetmirror.com/pub/ubuntu-backports](http://public.planetmirror.com/pub/ubuntu-backports) hoary-extras main universe multiverse restricted

which I found on a google search as the place where the w32codecs package for Ubuntu would be.

I'm running Ubuntu Hoary 5.04.

---

### Post by PaganHippie on 2005-10-02
Did you run 'sudo apt-get update' after changing the sources.list file?

---

### Post by Zelut on 2005-10-02
w32codecs is no longer available thru the repositories.  Its a legal issue from what I hear.  You can find it if you do a search, and I've kept a local copy for future use.  If ya'll need it you can PM me and I'll see about sending you a copy.

---

### Post by bored2k on 2005-10-02
w32codecs and others: [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)

*** Read carefully.**

---

### Post by chess007 on 2005-10-03
what is the user name and the password? its so frustrating that I can't get this.. :P

---

