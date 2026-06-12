---
title: "sensible-browser"
date: 2007-09-16
forum: General Help
---

### Post by Hoffmann on 2007-09-16
Hi,

For several programs, I see the documentation their documentation on sensible-browser, instead of  on Firefox, Notice that I set Firefox as my default browser. So, how can I disable sensible-browser, without removing debian-utils?

Thanks!

---

### Post by kerry_s on 2007-09-16
> **Hoffmann said:**
> Hi,

For several programs, I see the documentation their documentation on sensible-browser, instead of  on Firefox, Notice that I set Firefox as my default browser. So, how can I disable sensible-browser, without removing debian-utils?

Thanks!

huh? if you set firefox as your preferred app, sensible-browser will be a link to firefox.

---

### Post by Hoffmann on 2007-09-16
> **kerry_s said:**
> huh? if you set firefox as your preferred app, sensible-browser will be a link to firefox.

SO?

---

### Post by kerry_s on 2007-09-16
> **Hoffmann said:**
> SO?

so, i just looked at it, it's just a script to look for browser's.
if you don't want it, you can delete it or rename it.
so just> gksu nautilus /usr/bin
and have your way with it.

---

### Post by Hoffmann on 2007-09-16
> **kerry_s said:**
> so, i just looked at it, it's just a script to look for browser's.
if you don't want it, you can delete it or rename it.
so just> gksu nautilus /usr/bin
and have your way with it.

Sure. Let me explain better. I renamed sensible-browser (keeping Firefox as my default browser). However, the documentation of my program was not launched -  got a error message that says that sensible-browser was not found. So, I rename sensible-browser back to its original name, and I set Opera as my default browser. This way, the documentation of my program was nicely launched on Opera. 
Why that doesn't work with Firefox?

---

### Post by kerry_s on 2007-09-16
**sudo update-alternatives --config /usr/bin/www-browser**
that is the manual way
but i think there should be a gui, to select you preferred app and that should be used.

i don't have any browsers installed, i'm simple running the firefox.tgz from my home account, so i chose "other" and pointed it the right place.
pic example, i use xfce4, but you should have a similar->

---

### Post by Hoffmann on 2007-09-16
> **kerry_s said:**
> **sudo update-alternatives --config /usr/bin/www-browser**
that is the manual way
but i think there should be a gui, to select you preferred app and that should be used.

i don't have any browsers installed, i'm simple running the firefox.tgz from my home account, so i chose "other" and pointed it the right place.
pic example, i use xfce4, but you should have a similar->

Hi kerry_s,

Unfortunately, I didn't get it working with Firefox. So, I changed my default browser to Opera. 
Thanks a lot for your attention. I appreciated that!  :smile:

---

