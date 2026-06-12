---
title: "Zope"
date: 2016-04-28
forum: General Help
---

### Post by asearle on 2016-04-28
Hallo Everyone,

I will be maintaining a Zope website so need to install a test version/copy on my (L)Ubuntu PC and found these instructions specific to Ubuntu ...

<url>https://www.digitalocean.com/community/tutorials/how-to-install-and-use-zope-2-and-postgresql-on-ubuntu-13-10</url>

... which I tried to follow.

But when I ran "pip install" (below), I got a "You must give at least one requirement to install" message ...

<code>
(my_zope)root@alan-xxx:/home/server/my_zope# pip install --pre --index-url=http://download.zope.org/Zope2/index/2.13.24/Zope2
You must give at least one requirement to install (see "pip help install")
</code>

... which has now blocked/stumped me.

So now I am not sure whether I should carry on trying to trouble-shoot this type of (pip) installation?  Or whether I should resort to following the official Zope guidelines ...

<url>http://docs.zope.org/zope2/zope2book/InstallingZope.html</url>

Does anyone out there have experience of this and can give me a tip?  Maybe a link to a sure-fire HOWTO?  Otherwise I will try following the "docs.zope.org" instructions.

Many thanks,
Alan Searle
Cologne

---

### Post by asearle on 2016-04-28
I was making things much too complicated for myself:  Synaptic offers two great packages:  One for Zope2.13 and one for a "Sandbox" installation.  With these two installed you have everything you need with just a couple of clicks!  Bravo Ubuntu!

---

