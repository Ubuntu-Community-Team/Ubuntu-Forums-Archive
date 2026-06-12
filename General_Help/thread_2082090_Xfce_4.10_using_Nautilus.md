---
title: "Xfce 4.10 using Nautilus?"
date: 2012-11-08
forum: General Help
---

### Post by Rob Sayer on 2012-11-08
Just updated both laptops to xubuntu 12.10.  Very nice ... fast! ... and pretty uneventful.  Had previously installed xubuntu 12.04 over ubuntu 12.04.

The only thing about xfce is that I hate Thunar.

So far I've been using Nautilus 3.4.2 as default file manager.  Seems to work fine, but I read something that claims running nautilus in xfce is inadvisable.

Is there any truth in this?  You know how some of those blogs are ... 

If so, how about Dolphin?  Tried that a bit.  I'm not 100% pleased with the huge dependencies but if it'll work better ...

---

### Post by 2F4U on 2012-11-08
From this discussion on the XFCE forum it seems as if it is not too difficult to replace Thunar by Nautilus.

[http://forum.xfce.org/viewtopic.php?id=7077](http://forum.xfce.org/viewtopic.php?id=7077)

I don't know what reasons the blog post you mention has, but Nautilus is certainly heavier than Thunar and may bring in some more dependencies (but probably not as many as Dolphin). With XFCE you can still have GTK2 themes, and Nautilus would probably look bad.

---

### Post by Rob Sayer on 2012-11-08
Thanks for the response ... there were no reasons mentioned in that blog for not wanting nautilus.

I don't mind is nautilus or dolphin are heavier than thunar.  There are just too many features missing in thunar I consider essential ... above all it won't remember sorting preferences for each folder.

May as well give both a good going over ...

---

### Post by mardybear on 2012-11-08
Hi Rob...

Although a heavier application, nautilus is feature rich and still my favourite. Especially since is allows for pretty seamless network sharing provided samba/network shares are configured. I have never had any success getting thunar to provide windows network shares.

Assuming you already have nautilus installed, to run it in a desktop environment other than gnome open it via terminal or symbolic link as 'nautilus --no-desktop'. This will prevent nautilus from loading a bunch of gnome-desktop stuff, which you want to avoid since you're using XFCE.

mardybear

---

### Post by pqwoerituytrueiwoq on 2012-11-08
just go into settings -> preferred applications (second tab)
and you can set it
that said what is wrong with thunar it works great (now that [it has tabs]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html"))
[pcmanfm](apt:pcmanfm) is a good file browser also

---

### Post by Rob Sayer on 2012-11-09
Thanks for all the responses ....

Thunar may have tabs now, but it still doesn't seem to be able to remember folder sort options.  This bugs me *way* more than not having tabs.  That's the real deal breaker.

I used ubuntu with unity and gnome classic for a while so nautilus is pretty familiar to me ... it's better than thunar.

But I think I'll use dolphin ... it seems bloated at first but it's really powerful.

And ... I have a partition created on an external Hdd by a 3rd party Windows tool just for redundancy with some files.  Running unity/gnome or xfce/thunar that partition was always invisible under linux.

Since I still have a small (and rarely used it seems) windows 7 partition, I haven't bothered learning how to deal with making it visible.

Guess what?  Running dolphin the system recognizes it.

Good enough for me ...

---

