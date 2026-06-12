---
title: "2 questions regarding desktop cube"
date: 2008-05-28
forum: General Help
---

### Post by sayakb on 2008-05-28
1. How to make it a cylinder (round?)
2. How to install 3D window plugin that puts the Window at different heights?

I'm using Ubuntu Hardy 64-bit.

---

### Post by chewearn on 2008-05-28
[http://forum.compiz-fusion.org/showthread.php?t=8214](http://forum.compiz-fusion.org/showthread.php?t=8214)

---

### Post by wdaniels on 2008-05-28
> **LinuxIsInnovation said:**
> How to install 3D window plugin that puts the Window at different heights?

I don't know about the other one but the 3D Windows plugin is there for me by default (or at least I don't remember installing anything extra for it). In CompizConfig Settings Manager (sudo apt-get install compizconfig-settings-manager) it is first under the "Effects" heading.

---

### Post by sayakb on 2008-05-28
Its not by default. I compiled it in Gutsy and the clean install removed it (naturally)

---

### Post by wdaniels on 2008-05-28
> **LinuxIsInnovation said:**
> Its not by default. I compiled it in Gutsy and the clean install removed it (naturally)

I'm running Hardy so maybe that's the difference? I certainly never compiled and installed a single compiz plugin ever, so if it's not default in Hardy it's in the repos somewhere...

---

### Post by sayakb on 2008-05-28
> **AstalaVista said:**
> [http://forum.compiz-fusion.org/showthread.php?t=8214](http://forum.compiz-fusion.org/showthread.php?t=8214)
That doesn't have the 3D window plugin (not anaglyph) :(

---

### Post by chewearn on 2008-05-28
> **LinuxIsInnovation said:**
> That doesn't have the 3D window plugin (not anaglyph) :(

There is a link to the gibweb in the page, where you can find the location for all plugins.

Here, I find it for you:
[http://gitweb.compiz-fusion.org/?o=age](http://gitweb.compiz-fusion.org/?o=age)

 However, as wdaniels said, the 3d windows should already be included in Hardy. I didn't compile 3d windows, yet I find it in CCSM.

EDIT:
Oh, and I read futher down the page, the cube cylinder does not compile in compiz 0.7.4 (the version with Hardy).  You need to compile latest compiz from git.  A much more serious endeavor.

---

### Post by sayakb on 2008-05-28
Wow.. lets forget cylinder and 3D then.. :(

---

### Post by sayakb on 2008-05-28
> **wdaniels said:**
> I'm running Hardy so maybe that's the difference? I certainly never compiled and installed a single compiz plugin ever, so if it's not default in Hardy it's in the repos somewhere...
I couldn't fint it in the repos either.. Maybe I shouldn't have upgraded to Hardy anyway..

---

### Post by chewearn on 2008-05-28
I dug deeper and find out from this page:
[http://wiki.compiz-fusion.org/Plugins/Cube](http://wiki.compiz-fusion.org/Plugins/Cube)

that 3D windows is part of plugins extra.  So, probably you should install compiz-fusion-plugins-extra package (it's in the repos).

---

### Post by sayakb on 2008-05-28
I already have it installed. I'll try re-installing.

---

