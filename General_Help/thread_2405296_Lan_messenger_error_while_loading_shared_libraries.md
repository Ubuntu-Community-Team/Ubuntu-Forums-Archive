---
title: "Lan messenger: error while loading shared libraries: libgstapp-0.10.so.0"
date: 2018-11-03
forum: General Help
---

### Post by shati on 2018-11-03
Dear All, 

I am trying to install Lan messenger ([http://lanmsngr.sourceforge.net/index.php](http://lanmsngr.sourceforge.net/index.php)) on Ubuntu 18.04.
I tried to provide the required libraries during installation but now I am getting following error and so far i am unable to address this issue. 

ERROR Text 
[I][B]This is not a Canonical "designed" product.
/usr/lib/lmc/lan-messenger: error while loading shared libraries: libgstapp-0.10.so.0: cannot open shared object file: No such file or directory[/B][/I]

I checked (packages.ubuntu.com) for ibgstapp-0.10.so.0 for bionic suite but i get the following message 

[I][B]You have searched for files named libgstapp-0.10.so.0 in suite bionic, all sections, and all architectures. 
Sorry, your search gave no results[/B][/I]

I was wondeing if anyone else has gone through a similar problem or have tried lan messenger on ubuntu 18.04 or can suggest any other ubuntu based free lan messenger which can connect me to other pc(s) on network which are using windows. 

all solutions, tips, tweaks and comments are welcomed. 

I will also share the update if I come around some solutions.

---

### Post by l33ch on 2018-11-04
What I would try and looking for that missing file. According to that error: "/usr/lib/lmc/lan-messenger: error while loading shared libraries: libgstapp-0.10.so.0: cannot open shared object file: No such file or directory"

In /usr/lib/lmc/lan-messenger , that libgstapp-9.10.so.0 file is missing. I would use google and search ubuntu packages to downloaded just that one file (may have to extract it from main package, if it exists), and copy it in /usr/lib/lmc/lan-messenger  and see what happens.

Now, I did try a quick search for it: [https://packages.ubuntu.com/search?suite=trusty&arch=any&mode=exactfilename&searchon=contents&keywords=libgstapp-0.10.so.0](https://packages.ubuntu.com/search?suite=trusty&arch=any&mode=exactfilename&searchon=contents&keywords=libgstapp-0.10.so.0) and it seems I cannot download them due to a server error on ubuntu's side. That could be related to why you do may not have the file on your system, maybe. I got an " 500 Internal Server Error" even when I tried to download it via wget and via web page.

---

### Post by mc4man on 2018-11-04
Your app uses gstreamer0.10 which is no longer in use in 18.04. 
You need one that uses or gstreamer1.0 or use Ubuntu 16.04 which has limited gstreamer0.10 support.

---

### Post by Holger_Gehrke on 2018-11-04
You could go to [https://lanmessenger.github.io/](https://lanmessenger.github.io/) and try a two year old version of this software instead of one from six years ago (which at least starts on 18.04, can't tell if it actually works)

Or you could use the server-less chat in pidgin, uses Bonjour / Avahi afaik ...

---

