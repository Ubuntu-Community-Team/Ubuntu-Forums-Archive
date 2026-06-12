---
title: "[SOLVED] All Texts replaced by blocks"
date: 2008-03-19
forum: General Help
---

### Post by yghannam7388 on 2008-03-19
Hello all, I've been using Ubuntu 7.10 now for a couple of weeks. Today I was installing some packages when all of a sudden Firefox would load. So I logged out and back in only to find that all the text in the OS have changed to blocks. The only thing that is normal is the terminal. I first uninstalled the last package I installed before everything when wrong and that was "libttf-dev", I think. Then I tried reconfiguring xserver with

dpkg-reconfigure xserver-xorg

That didn't work so I tried reinstalling gnome because one guy online said that worked for him. When I did that I got a message from the terminal that gnome wasn't even installed so I went ahead and installed it anyway. But that didn't work. 

So does anyone have any ideas?
Thanks.

---

### Post by moore.bryan on 2008-03-19
it sounds like you don't have any fonts installed... try ```
sudo aptitude install xfonts-base
```

---

### Post by forestpixie on 2008-03-19
could try the font cache thing

```
sudo fc-cache -fv
```

especially if you've been installing something to do with fonts which I guess libttf is

---

### Post by yghannam7388 on 2008-03-19
Thanks for the quick responses.

When I did the first suggestions the terminal just said that I had the newest version of xfonts. The second suggestion finished successfully but didn't fix my problem. Thanks for the help though.

Any other suggestions?

Ubuntu comes with gnome installed right? Because I'm still kind of wondering why the terminal told me that gnome wasn't installed at all. Also, is there a way to uninstall all the graphical interface stuff and reinstall it?

---

### Post by yghannam7388 on 2008-03-19
*bump*

---

### Post by yghannam7388 on 2008-03-19
So I installed Xfce and it works perfectly. You guys were right about the fonts and when I tried to run gedit in the terminal I got a bunch of errors about Pango and its fonts. Is there anyway to reinstall Pango to its original settings or should I just stick with Xfce and forget Gnome?

---

### Post by moore.bryan on 2008-03-21
what exactly were the errors?

---

### Post by yghannam7388 on 2008-03-22
Actually what I was found was it was Pango that was causing the errors. I don't remember what they were to be honest. I wanted to compile and install the latest version of GTK and in order to do that I needed to have Pango installed. So I compiled and install Pango and that is what caused the errors. I tried different version but they all did the same thing. Oh and it turns out that when I in xubuntu-desktop it removed Pango from my system and when I restarted I was still using Gnome but everything worked.

It was kind of a weird scenario.

---

### Post by moore.bryan on 2008-03-22
> **yghannam7388 said:**
> It was kind of a weird scenario.
i'll say! ;-)
happy ubuntu-ing.

---

