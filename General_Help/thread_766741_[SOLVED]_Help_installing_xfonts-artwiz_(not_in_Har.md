---
title: "[SOLVED] Help installing xfonts-artwiz (not in Hardy repo)"
date: 2008-04-25
forum: General Help
---

### Post by ilych on 2008-04-25
Hello,

I am trying to install the package "xfonts-artiwz", which is in the Gutsy universe repository:
[http://packages.ubuntu.com/search?keywords=artwiz&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=artwiz&searchon=names&suite=gutsy&section=all)

It isn't in the Hardy repository, and multiple people on the #ubuntu @ Freenode irc channel also do not recommend adding a gutsy repository line in my hardy sources.list.

So is there any way I can install this package, or should I just install the font manually?

Thanks,
ilych

---

### Post by ilych on 2008-04-25
Okay, I installed "xfonts-artwiz_1.3-5_all.deb" from packages.ubuntu.com and  also enabled bitmapped fonts using "sudo dpkg-reconfigure fontconfig-config".

After a restart, I don't see the fonts show up anywhere (e.g., System > Preferences &#65310; Appearance > Fonts, OpenOffice) Did I do something wrong, or will a .deb from the Gutsy repository not work? I also ensured that I have the packages "xfonts-artwiz" depends on.

The Package Installer for "xfonts-artwiz" lists the following in the "Included Files" tab:

```
./
usr/
usr/share/
usr/share/fonts/
usr/share/fonts/X11/
usr/share/fonts/X11/misc/
usr/share/fonts/X11/misc/aqui.pcf.gz
usr/share/fonts/X11/misc/drift.pcf.gz
usr/share/fonts/X11/misc/fkp.pcf.gz
usr/share/fonts/X11/misc/glisp-bold.pcf.gz
usr/share/fonts/X11/misc/glisp.pcf.gz
usr/share/fonts/X11/misc/kates7x14.pcf.gz
usr/share/fonts/X11/misc/lime.pcf.gz
usr/share/fonts/X11/misc/runt.pcf.gz
usr/share/fonts/X11/misc/smooth.pcf.gz
usr/share/fonts/X11/misc/smoothansi.pcf.gz
usr/share/fonts/X11/misc/tixus.pcf.gz
usr/share/fonts/X11/misc/anorexia.pcf.gz
usr/share/fonts/X11/misc/cure.pcf.gz
usr/share/fonts/X11/misc/edges.pcf.gz
usr/share/fonts/X11/misc/gelly.pcf.gz
usr/share/fonts/X11/misc/kates.pcf.gz
usr/share/fonts/X11/misc/mints-mild.pcf.gz
usr/share/fonts/X11/misc/mints-strong.pcf.gz
usr/share/fonts/X11/misc/nu.pcf.gz
usr/share/fonts/X11/misc/snap.pcf.gz
usr/share/fonts/X11/misc/anorexia.de.pcf.gz
usr/share/fonts/X11/misc/aqui.de.pcf.gz
usr/share/fonts/X11/misc/cure.de.pcf.gz
usr/share/fonts/X11/misc/drift.de.pcf.gz
usr/share/fonts/X11/misc/edges.de.pcf.gz
usr/share/fonts/X11/misc/fkp.de.pcf.gz
usr/share/fonts/X11/misc/gelly.de.pcf.gz
usr/share/fonts/X11/misc/glisp-bold.de.pcf.gz
usr/share/fonts/X11/misc/glisp.de.pcf.gz
usr/share/fonts/X11/misc/kates.de.pcf.gz
usr/share/fonts/X11/misc/lime.de.pcf.gz
usr/share/fonts/X11/misc/mints-mild.de.pcf.gz
usr/share/fonts/X11/misc/mints-strong.de.pcf.gz
usr/share/fonts/X11/misc/nu.de.pcf.gz
usr/share/fonts/X11/misc/smoothansi.de.pcf.gz
usr/share/fonts/X11/misc/snap.de.pcf.gz
usr/share/fonts/X11/misc/anorexia.se.pcf.gz
usr/share/fonts/X11/misc/aqui.se.pcf.gz
usr/share/fonts/X11/misc/cure.se.pcf.gz
usr/share/fonts/X11/misc/drift.se.pcf.gz
usr/share/fonts/X11/misc/edges.se.pcf.gz
usr/share/fonts/X11/misc/fkp.se.pcf.gz
usr/share/fonts/X11/misc/gelly.se.pcf.gz
usr/share/fonts/X11/misc/glisp-bold.se.pcf.gz
usr/share/fonts/X11/misc/glisp.se.pcf.gz
usr/share/fonts/X11/misc/kates.se.pcf.gz
usr/share/fonts/X11/misc/lime.se.pcf.gz
usr/share/fonts/X11/misc/mints-mild.se.pcf.gz
usr/share/fonts/X11/misc/mints-strong.se.pcf.gz
usr/share/fonts/X11/misc/nu.se.pcf.gz
usr/share/fonts/X11/misc/smoothansi.se.pcf.gz
usr/share/fonts/X11/misc/snap.se.pcf.gz
usr/share/fonts/X11/misc/anorexia-koi8-r.pcf.gz
usr/share/fonts/X11/misc/anorexia-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/cure-koi8-r.pcf.gz
usr/share/fonts/X11/misc/cure-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/edges-koi8-r.pcf.gz
usr/share/fonts/X11/misc/edges-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/gelly-koi8-r.pcf.gz
usr/share/fonts/X11/misc/gelly-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/glisp-koi8-r.pcf.gz
usr/share/fonts/X11/misc/glisp-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/mints-mild-koi8-r.pcf.gz
usr/share/fonts/X11/misc/mints-mild-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/mints-strong-koi8-r.pcf.gz
usr/share/fonts/X11/misc/mints-strong-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/nu-koi8-r.pcf.gz
usr/share/fonts/X11/misc/nu-microsoft-cp1251.pcf.gz
usr/share/fonts/X11/misc/snap-koi8-r.pcf.gz
usr/share/fonts/X11/misc/snap-microsoft-cp1251.pcf.gz
usr/share/lintian/
usr/share/lintian/overrides/
usr/share/doc/
usr/share/doc/xfonts-artwiz/
usr/share/doc/xfonts-artwiz/copyright
usr/share/doc/xfonts-artwiz/changelog.Debian.gz
etc/
etc/X11/
etc/X11/fonts/
etc/X11/fonts/X11R7/
etc/X11/fonts/X11R7/misc/
etc/X11/fonts/X11R7/misc/xfonts-artwiz.alias
```

It seems like these files were correctly extracted from the .deb...

Thanks for any help.

EDIT: The artwiz package shows up in xfontsel.. strange

---

### Post by HandyAndy on 2008-04-30
I'm trying to make the artwiz fonts available to the Fluxbox styles that use them.

I've got them in ~/.fonts
I've done 'mkfontdir ~/.fonts'
I've done 'fc-cache -fv'
I've done 'dpkg-reconfigure fontconfig-config'

No joy. They don't show up anywhere.

I've tried to follow 3 or 4 different HowTo's, but the directories and files they refer to aren't the same as mine and I don't know enough to adapt the instructions.

I'd be grateful for any help. I probably shouldn't be using Fluxbox because I haven't really got the knowledge - but I've fallen in love with it :)

I'm using 8.04 and Fluxbox 1.0.0 from the repos.

---

### Post by jonlorusso on 2008-05-02
Is there any reason why this package is not in the Hardy repository?

---

### Post by HandyAndy on 2008-05-03
Success! I got my artwiz fonts working.

The instructions in the following HowTo on the Fluxbox wiki are basically what you want, but I had to interpret them in terms of my set-up.

[http://fluxbox-wiki.org/index.php/Install_fonts]("http://fluxbox-wiki.org/index.php/Install_fonts")

I started at 4, because I'd already done the preceding steps - see my previous post. 

At 4, the file I needed to edit is **/etc/X11/xorg.conf**.
I had no **FontPath** element to change, nor the **"Files"** Section it lives in, so I had to create both:

```
Section "Files"
      FontPath "/home/andy/.fonts/"
EndSection
```

At 5, my **local.conf** is in **/etc/fonts/conf.d/** and in **etc/fonts/conf.avail/**. I only edited one and they both changed.

That, along with the rest of the instructions in the HowTo, worked. My Fluxbox styles can now find and use the artwiz fonts.

A couple of other things I learned along the way apply to the **sid** styles, but I guess they could apply equally to other styles you download.

Having successfully made the fonts available, most of my styles picked them up ok - but not all. I found I had to tinker with some of the styles files themselves. For example, one of the styles specified the **mints-strong** font, but it wasn't working. Everything looked ok because the name of the font .pcf file was as it was in the style file - with the hyphen. But when I looked at its properties, the font's 'real' name is **mintsstrong**. I changed it to that in the style file and it worked.

My styles weren't setting their specified backgrounds either. That, I found out, is because the styles pre-dated the change from **rootCommand** to **background** to set the background.
I replaced the **rootCommand** line in the style files with the appropriate **background** settings and they all work now.

An explanation and instructions on how to use **background** is also in the wiki:

[http://fluxbox-wiki.org/index.php/Background]("http://fluxbox-wiki.org/index.php/Background")

It goes without saying, but I backed up all the files I was going to change before I touched them. So the worst that could happen is I'd be back where I started. And being new to this stuff, that safety-net gave me the confidence to implement the bits that I'd worked out for myself because they weren't fully documented for my set-up.

I hope this helps anyone else new to the wonderful world of Fluxbox and configuring by hand :)

Andy

---

