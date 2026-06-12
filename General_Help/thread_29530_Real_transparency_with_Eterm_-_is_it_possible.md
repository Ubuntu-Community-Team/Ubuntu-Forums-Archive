---
title: "Real transparency with Eterm - is it possible?"
date: 2005-04-24
forum: General Help
---

### Post by void_false on 2005-04-24
Hey there!
I´m trying to customize my desktop to be uberrocking one. Like on those sexy screenshots. Is it possible to make Eterm half transparent so it will be 50% opaque and i´ll be able to see windows below it half shaded?
TIA!

---

### Post by Xerampelinae on 2005-04-24
It might be possible with some bleeding edge features in xorg, which could cause instability and/or slowness, depending upon your video card.

Still, here's a relevant link from my quick google search:
[http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency)

---

### Post by void_false on 2005-04-24
THX mate. Now it will be real pain in the a$$ to convert gentoo´s commands into debian ones. I´m not a guru but i think i´m able to handle it. ;)

---

### Post by void_false on 2005-05-02
> echo "x11-misc/transset ~x86" >> /etc/portage/package.keywords 
How do I translate it into Ubuntu?

---

### Post by Leigh on 2005-05-02
I'm not sure if this will help you, but have a look at this link ( [http://www.ubuntuforums.org/showthread.php?t=20769&highlight=compositing](http://www.ubuntuforums.org/showthread.php?t=20769&highlight=compositing) ) as it explains how to get transparency in any window. It's writtein for Ubuntu Hoary, so may be more user friendly.

---

### Post by Xerampelinae on 2005-05-02
[QUOTE=void_false]How do I translate it into Ubuntu?[/QUOTE]
 Yeah, that other guide may be better.  But to answer your question, it's a specific gentoo thing that allows you to install programs that are still in testing.  You can safely ignore it.

Specifically it's preparing the program "transset" to allow the testing version to be installed.  The next command is probably "emerge transset" which would install the program.

---

### Post by void_false on 2005-05-02
Well. I´m unlucky guy. First of all these eye candy hits performance really hard. And second it hangs my PC after about 5 minutes of work.  :|  :cry:

---

