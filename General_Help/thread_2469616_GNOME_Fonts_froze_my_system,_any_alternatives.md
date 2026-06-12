---
title: "GNOME Fonts froze my system, any alternatives?"
date: 2021-12-03
forum: General Help
---

### Post by ardouronerous on 2021-12-03
I'm running Xubuntu 20.04 and GNOME Fonts (gnome-font-viewer) has frozen my system. I clicked on Accessories -> Fonts, and when I tried to search for a font, my entire system hang, my mouse still worked, but when I tried to click on my Start menu, nothing happened and when I tried to click other things, nothing happened, so my system was frozen, forcing me to shut off my computer and turn it on again.

Are there alternatives to GNOME Fonts? Thanks.

---

### Post by ardouronerous on 2021-12-04
I found this: [https://www.flathub.org/apps/details/com.github.fontmatrix.Fontmatrix](https://www.flathub.org/apps/details/com.github.fontmatrix.Fontmatrix)

Works well, but still, I want to know why Xubuntu's default font manager is malfunctioning though.

---

### Post by tea for one on 2021-12-05
Did you add gnome-font-viewer after your Xubuntu installation?

Can you not access fonts via Appearance > Fonts?
That should be the usual xfce4 setting for fonts?

---

### Post by ardouronerous on 2021-12-06
> **tea for one said:**
> Did you add gnome-font-viewer after your Xubuntu installation?

gnome-font-viewer came preinstalled with Xubuntu.

> Can you not access fonts via Appearance > Fonts?
That should be the usual xfce4 setting for fonts?

Yes, I can, but as soon as I start scrolling through the fonts, the program freezes or my system freezes.

---

### Post by tea for one on 2021-12-06
> **ardouronerous said:**
> gnome-font-viewer came preinstalled with Xubuntu.
Yes, I can, but as soon as I start scrolling through the fonts, the program freezes or my system freezes.

It's a bit surprising that a pre-installed utility is freezing your system.
I didn't realise gnome-font-viewer was an automatic inclusion in Xubuntu 20.04

I have a little netbook, where I have installed [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/) and then added my choice of applications.
This ISO does not include gnome-font viewer and I use the xfce4 font utility (although I don't know exactly what it is called)

---

### Post by Skaperen on 2021-12-06
my Xubuntu 18.04.6 (last upgraded yesterday) has it.  i have never used it or an xfce4 one (although I don't know exactly what it is called, either).

---

### Post by ardouronerous on 2021-12-06
> **Skaperen said:**
> my Xubuntu 18.04.6 (last upgraded yesterday) has it.  i have never used it or an xfce4 one (although I don't know exactly what it is called, either).  I thought Xubuntu 18.04 had reached it's end of life already?

---

### Post by ardouronerous on 2021-12-06
> **tea for one said:**
> It's a bit surprising that a pre-installed utility is freezing your system.
I didn't realise gnome-font-viewer was an automatic inclusion in Xubuntu 20.04

I have a little netbook, where I have installed [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/) and then added my choice of applications.
This ISO does not include gnome-font viewer and I use the xfce4 font utility (although I don't know exactly what it is called)

Fontmatrix was needless complicated and so I switched over to [GNOME Fonts via Flathub]("https://www.flathub.org/apps/details/org.gnome.font-viewer") and it works well and doesn't freeze my system.

---

### Post by ardouronerous on 2021-12-06
> **tea for one said:**
> It's a bit surprising that a pre-installed utility is freezing your system.
I didn't realise gnome-font-viewer was an automatic inclusion in Xubuntu 20.04

I have a little netbook, where I have installed [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/) and then added my choice of applications.
This ISO does not include gnome-font viewer and I use the xfce4 font utility (although I don't know exactly what it is called)

Not sure if this is related but Flathub's GNOME Fonts crashed:

```
~$ flatpak run org.gnome.font-viewer

(gnome-font-viewer:2): Gdk-WARNING **: 12:41:49.635: The program 'gnome-font-viewer' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 1044 error_code 128 request_code 130 (MIT-SHM) minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by KBar on 2021-12-07
The crash is the result of [this](https://bugs.launchpad.net/ubuntu/+source/gnome-font-viewer/+bug/1845362) bug. [Comment #19](https://bugs.launchpad.net/ubuntu/+source/gnome-font-viewer/+bug/1845362/comments/19) mentions that it "isn't an essential software" and the bug was triaged as rls-ii-notfixing.

Perhaps you could try *font-manager*.

---

### Post by Dennis N on 2021-12-07
I also would suggest Font Manager.

---

### Post by ardouronerous on 2021-12-08
> **kbar said:**
> The crash is the result of [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-font-viewer/+bug/1845362") bug. [Comment #19]("https://bugs.launchpad.net/ubuntu/+source/gnome-font-viewer/+bug/1845362/comments/19") mentions that it "isn't an essential software" and the bug was triaged as rls-ii-notfixing.

This bug is huge since it can freeze the entire system. If this is a bug that they won't fix, then I would suggest that Ubuntu and all it's flavors to remove gnome-font-viewer as a default application due to this bug, since it affects the system.

> **kbar said:**
> Perhaps you could try *font-manager*.

> **Dennis N said:**
> I also would suggest Font Manager.

Thanks for the suggestion guys.

---

