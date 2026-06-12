---
title: "Microsoft Core Fonts?"
date: 2006-12-15
forum: General Help
---

### Post by raid517 on 2006-12-15
Hi I installed a package for Microsoft Core Fonts, but I can't see them or use them in any of my applications.

Can anyone tell me how to get them to show up and display correctly?

Thanks...

---

### Post by d3v1ant_0n3 on 2006-12-15
I just had a quick check, and my Microsoft Core fonts are in /usr/share/fonts/truetype/msttcorefonts

Might want to check that they are there.

There may also be a folder in your home directory called .fonts -I had quite a decent selection of fonts on one of our windows boxes, so I just copied them into that folder and they show up fine in apps.

---

### Post by bodhi.zazen on 2006-12-15
See this link:

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by raid517 on 2006-12-15
Thanks... I'm not sure if that worked, in fact I'm pretty sure it didn't. I however now have a huge selection of fonts - but I don't have any fonts specifically referring to MS (as in MS Sans Serif, MS Tahoma etc (in fact there is only one mention of MS in all the fonts that I have. I mention this as I seem to recall that in Suse several fonts had 'MS' next to them).

I also seem to remember that the last time I used Linux regularly, you needed to enter the path to the true type fonts in your Xorg.conf file - but I have forgotten how to do this and can't seem to find much information on it either.

Really, I just want the fonts mostly for Firefox, - as there are quite a few web pages which don't display characters correctly without them.

Any input on how to achieve this would be appreciated.

---

### Post by shining on 2006-12-15
> **raid517 said:**
> Thanks... I'm not sure if that worked, in fact I'm pretty sure it didn't. I however now have a huge selection of fonts - but I don't have any fonts specifically referring to MS (as in MS Sans Serif, MS Tahoma etc (in fact there is only one mention of MS in all the fonts that I have. I mention this as I seem to recall that in Suse several fonts had 'MS' next to them).

I also seem to remember that the last time I used Linux regularly, you needed to enter the path to the true type fonts in your Xorg.conf file - but I have forgotten how to do this and can't seem to find much information on it either.

Really, I just want the fonts mostly for Firefox, - as there are quite a few web pages which don't display characters correctly without them.

Any input on how to achieve this would be appreciated.

Tahoma isn't part of the core fonts package. But anyway, afaik that font was designed for using with the desktop, not the web.
I'm not sure which ones are though, but you could try Arial or Verdana as Sans Serif fonts and Times or Georgia as Serif fonts, which should be part of core fonts.

---

### Post by bodhi.zazen on 2006-12-15
> **raid517 said:**
> Thanks... I'm not sure if that worked, in fact I'm pretty sure it didn't. I however now have a huge selection of fonts - but I don't have any fonts specifically referring to MS (as in MS Sans Serif, MS Tahoma etc (in fact there is only one mention of MS in all the fonts that I have. I mention this as I seem to recall that in Suse several fonts had 'MS' next to them).

I also seem to remember that the last time I used Linux regularly, you needed to enter the path to the true type fonts in your Xorg.conf file - but I have forgotten how to do this and can't seem to find much information on it either.

Really, I just want the fonts mostly for Firefox, - as there are quite a few web pages which don't display characters correctly without them.

Any input on how to achieve this would be appreciated.

```
gksudo gedit /etc/X11/xorg.conf
```

In the fonts section be sure you have an entry like this:> FontPath "/usr/share/fonts/truetype/msttcorefonts"

---

