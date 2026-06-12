---
title: "Mac OS X theme for Lubuntu does not change the look of Window Borders"
date: 2016-08-24
forum: General Help
---

### Post by johnbross on 2016-08-24
So I found this really good looking theme in [here]("https://www.linuxslaves.com/2016/05/macbuntu-mac-os-x-yosmite-theme-for-ubuntu1604.html") :

I followed the steps, and instead of installing and using unity-theme-utility I used

    Preferences > Customize Look and Feel

However, even do that theme was LXDE compatible, I did not get the result I expected, indeed the window borders do not look like in the first link:

[http://i.stack.imgur.com/d6QBJ.png](http://i.stack.imgur.com/d6QBJ.png)
How do I solve this problem? Do I have to install additional software?

---

### Post by &amp;KyT$0P# on 2016-08-24
The window manager is Openbox.  Openbox theming is separate, you need to install or make a Openbox theme that you like with that and then configure Openbox to use it.

---

### Post by johnbross on 2016-08-24
> **halogen2 said:**
> The window manager is Openbox.  Openbox theming is separate, you need to install or make a Openbox theme that you like with that and then configure Openbox to use it.

Can I convert that particular theme into one that is compatible with Openbox?

---

### Post by &amp;KyT$0P# on 2016-08-24
I don't know.  I have made Openbox themes before, basically I just looked online (mostly ended up at [this site]("https://www.box-look.org/")) for Openbox theme that was close to what I wanted, renamed it and then edited it.  Some of this is art rather than technical stuff.
I've found that being able to actually look at windows that look like what you want (either in screenshots or VMs) makes it easier to design the theme.

There is lots of good [documentation]("http://openbox.org/wiki/Help:Themes") on Openbox theming.

---

### Post by vasa1 on 2016-08-24
> **johnbross said:**
> So I found this really good looking theme ... LXDE compatible, I did not get the result I expected, indeed the window borders do not look like in the first link: ...
How do I solve this problem? Do I have to install additional software?
What do you mean by "LXDE compatible"? Nowhere in that link does it mention Openbox. Themes that support Openbox have a subfolder titled "openbox-3" containing a file called "themerc" and possibly some images. Does this theme have such a folder?

When you say "the window borders do not look like in the first link", are you referring to the shadows? Do you have a compositing manager installed? Lubuntu, if that's what you're using, doesn't come with a compositor. You need to install, and configure, one.

---

### Post by johnbross on 2016-08-25
> What do you mean by "LXDE compatible"?

I was actually wrong, it supports Unity, Gnome, Cinnamon, Mate and Xfce.

> Themes that support Openbox have a subfolder titled "openbox-3"  containing a file called "themerc" and possibly some images. Does this  theme have such a folder?

No sir.

> 
When you say "the window borders do not look like in the first link", are you referring to the shadows?

Not the shadows, but literally the window borders, which include the "Exit, maximize, minimize" buttons and how they look ... etc

> Do you have a compositing manager installed? Lubuntu, if that's what  you're using, doesn't come with a compositor. You need to install, and  configure, one.

I have compiz, but the theme seems to not be compatible with LXDE, should I instead install and move to Xfce? Would that be a good suggestion?

---

### Post by vasa1 on 2016-08-25
> **johnbross said:**
> ..., should I instead install and move to Xfce? Would that be a good suggestion?
Use what you feel comfortable with and whatever your computer supports. You can figure that out by trying various distros as Live USBs without actually installing them.

---

### Post by leunam12 on 2016-08-25
Why are you on LXDE, what kind of hardware do you have? I would try Ubuntu Mate if your hardware supports it.

---

### Post by johnbross on 2016-08-25
> **leunam12 said:**
> Why are you on LXDE, what kind of hardware do you have? I would try Ubuntu Mate if your hardware supports it.

I installed it on a very old laptop (from 2003). Yeah, should've used Ubuntu Mate.

I installed Xfce and now the theme works just fine. I think I'll just stick with that. Thanks for all the support. :)

---

