---
title: "Problem with updating application list"
date: 2007-12-21
forum: General Help
---

### Post by meltbanana on 2007-12-21
Hi everyone,

I am having a problem with updating and installing software and in Add/Remove Programs.

I am connected to the internet by Wireless router and i can browse website fine, but when i try to install software, it comes up with the error:
> The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working Internet connection. 

I click reload to get the list updated and it downloads the package information quickly (seems too quickly) and nothing changes. When i then try to select something to download, it asks to reload the list again.

I havent had this problem before until i installed Gutsy Gibbon. I looked on the forum and none of the suggested fixes worked so i am kind of stumped. 

Any suggestions?

---

### Post by TidusBlade on 2007-12-21
Maybe your sources.list file in /etc/apt/ is faulty... Try the [Source-O-matic](http://www.ubuntu-nl.org/source-o-matic/) to create a new one?

---

### Post by meltbanana on 2007-12-21
Thanks. While snooping around with sources.list i noticed for some reason that it was trying to look for the installation cd for the list. when i unselected this in the add/remove progams preferences and selected which repositories i wished to use, it worked.

never had this problem before until now which is weird since i just did the standard install of ubuntu

---

