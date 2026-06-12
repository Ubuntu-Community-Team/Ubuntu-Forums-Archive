---
title: "About X window"
date: 2006-10-30
forum: General Help
---

### Post by satimis on 2006-10-30
Hi folks,

Ubuntu-6.06.1-LAMP server-amd64

I'm now configuring the LAMP server for test purpose.  There is no X running on it.  I run "elinks", the text browser, and find it hard to natvigate as well difficult reading webpages.  I even ecountered difficulty login to a website.  I rely heavily on web browsing to search Internet in case of technical problem.

Is there any clue?  Installing X first to run firefox and remove X after finishing configuration of the server?  If YES how to make group-installation of X as well as Gnome desktop (one desktop only).

Please advise.  TIA.

B.R.
satimis

---

### Post by nereid on 2006-10-30
You could use [links2](http://en.wikipedia.org/wiki/Links_%28web_browser%29) with framebuffer support or SVGAlib to display graphics. You don't need X for this.

---

### Post by satimis on 2006-10-30
Hi nereid,

Tks for your advice and link.

Just having a brief browsed on;
[http://en.wikipedia.org/wiki/Links_%28web_browser%29](http://en.wikipedia.org/wiki/Links_%28web_browser%29)```

....
Links Hacked is another version of the Links browser which has merged Elinks features into Links 2.
....

```

Would "links hacked" better suit me.  I have "elinks" running.

$ sudo apt-cache search links2
$ sudo apt-cache search "links hacked"
both w/o printer.  Would they be on "universe" repo?

TIA

> ...with framebuffer support or SVGAlib to display graphics.
Pls explain in more detail.  Whether I need to install "framebuffer" or "SVGAlib" in addition.  Tks.

B.R.
satimis

---

### Post by nereid on 2006-10-30
If links2 is in the repos you don't have to solve the dependencies. A quick apt-cache search links2 results in a package. Just sudo apt-get install links2 and everything should be fine.

---

### Post by satimis on 2006-10-30
Hi nereid,

> A quick apt-cache search links2 results in a package. Just sudo apt-get install links2 and everything should be fine.
I tried before;

$ sudo apt-get install links2```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package links2

```

I also enabled "universe" repo without result.


B.R.
satimis

---

### Post by nereid on 2006-10-30
Than I have some more repos enabled than you ;) According to my package of links2 it is available from universe/net.

---

### Post by satimis on 2006-10-30
Hi nereid,

I have links2 installed.  

$ which links2
/usr/bin/links2

But it can't work.
$ links2 yahoo.com```

Error
This version of Links does not contain SSL/TSL support
[Close]

```

satimis

---

