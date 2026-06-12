---
title: "upgrade of pidgin"
date: 2008-02-14
forum: General Help
---

### Post by fedex1993 on 2008-02-14
is there anyway i can upgrade from 2.2.1 to 2.3.1 ?

---

### Post by dicecca112 on 2008-02-14
go to getdeb.net, and download the packages for it.  There is like 3 I think

---

### Post by leo5111 on 2008-06-11
ok how do i clean off old pidgin i uninstalled pidgin then i downloaded a package and it said old package was interfering??? :confused: oh im on linux mint daryna 4.0 which ive been told can use same software

---

### Post by Mongo5000 on 2008-07-03
Im in the same boat.  My pidgin says it needed to be upgraded so I did.

What I did was go into synaptic and remove pidgin.  Done.

I then went to getdeb.net and downloaded pidgin from there.  When I go to install, I get this

"Error: Dependency is not satisfiable: libcairo2"

I can't for the life of me figure out how to install libcairo2.  From the 3 packages I downloaded, I get different dependancies errors.  Other one is libglib2.0-0.

Any suggestions?

---

### Post by rrohde on 2008-07-03
Worked for me (I am on Hardy). But I didn't uninstall the previous Pidgin. I just installed those 3 debs, re-enabled my ICQ account, and I was online again - new version and all...

---

### Post by Ryozanpaku Tiger on 2008-07-03
Hardy 8.10 (32 bits). The following has worked for me.

1) Synaptic Package Manager: remove pidgin, pidgin-data, libpurple0 (this was recommended on [www.getdeb.net](www.getdeb.net), where I got the new version of Pidgin)

2) Install pidgin, pidgin-data, libpurple0 from [http://www.getdeb.net/release.php?id=2883](http://www.getdeb.net/release.php?id=2883) (search for Pidgin 2.4.3, in my case for Ubuntu Hardy (32 bits))

3) Launch Pidgin

---

### Post by Mongo5000 on 2008-07-03
tried all suggestions, same as before :(

---

### Post by Jojan on 2008-07-03
> **Ryozanpaku Tiger said:**
> Hardy 8.10 (32 bits). The following has worked for me.

1) Synaptic Package Manager: remove pidgin, pidgin-data, libpurple0 (this was recommended on [www.getdeb.net](www.getdeb.net), where I got the new version of Pidgin)

2) Install pidgin, pidgin-data, libpurple0 from [http://www.getdeb.net/release.php?id=2883](http://www.getdeb.net/release.php?id=2883) (search for Pidgin 2.4.3, in my case for Ubuntu Hardy (32 bits))

3) Launch Pidgin

Worked well for me. I had to press "Re activate", or whatever is says in your.

---

### Post by Sean Heron on 2008-07-03
The update is now also available in the Ubuntu repositories 
(hardy-proposed), so there is now (in my view) an easier way of doing the whole upgrade. Best see the 12th page of  [this thread]("http://ubuntuforums.org/showthread.php?p=5313090#post5313090").

---

