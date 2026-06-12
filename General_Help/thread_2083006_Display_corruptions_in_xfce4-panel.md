---
title: "Display corruptions in xfce4-panel"
date: 2012-11-11
forum: General Help
---

### Post by sbw87 on 2012-11-11
Hi,
I don't know if this applies to user display managers as well, therefore I'm posting here in the general forum. I've got the rather strange problem, using Xubuntu 12.04, that sometimes some bits of the program menu remain on the screen even when the menu itself has disappeared. This can only be resolved by killing and restarting xfce4-panel. A similar corruption occurs when someone is trying to call me on Skype: I can't take the other person's call because the small Skype window in the bottom-right corner doesn't get rendered correctly.

Attached is a screenshot of the menu issue.

Thanks for your help!

[IMG]http://sandrobauer.eu/stuff/photo.png[/IMG]

---

### Post by pqwoerituytrueiwoq on 2012-11-11
what gpu do you have? and what driver?
settings -> window manager tweeks -> Compositor
uncheck 1st box should fix it, at least till you sort out the real issue

---

### Post by sbw87 on 2012-11-11
Amazing, thanks for your help. 

I have this notebook:

[http://shop.lenovo.com/deweb/DE/de/learn/products/laptops/thinkpad/x-series/x1/index.html](http://shop.lenovo.com/deweb/DE/de/learn/products/laptops/thinkpad/x-series/x1/index.html)

...and lspci says:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

Please let me know if you need any more details.

---

### Post by pqwoerituytrueiwoq on 2012-11-11
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```
is on my notebook
i had a issue like that, i ppa-purged the xorg edgers ppa and it was good
running 12.10 xubuntu

---

### Post by sbw87 on 2012-11-13
Thanks -- but I don't seem to have that ppa installed.

---

