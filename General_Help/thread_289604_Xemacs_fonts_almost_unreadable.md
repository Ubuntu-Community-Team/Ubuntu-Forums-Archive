---
title: "Xemacs fonts almost unreadable"
date: 2006-10-31
forum: General Help
---

### Post by ggw10 on 2006-10-31
I upgraded to Edgy from Dapper, and since then Xemacs has become
almost unusable: fonts (both in the windows and the menubar)
are horribly bitmapped. 

Note that:
i) I am getting fonts displayed, and I can select fonts 
under options -> fonts, so I am not suffering from the 
problem that a lot of people have suffered with Xemacs
ii) I'm not suffering from the font problems in other applications
(openoffice, firefox) that a lot of people have suffered from. 
My problem is specific to Xemacs

Any thoughts?

graham

---

### Post by shuttle on 2007-02-09
I'm having a similar problem. I installed Edgy on a brand new computer a few weeks back. I tend to update the system about once a week or so. Last night I hit the update, and this morning I find that my xemacs fonts are horrible ... they are tiny and just absolutely unusable.

So far I've tried the following with no luck:

[LIST=1]
[*]export LANG=C
[*]Uninstall xemacs-mule, re-install xemacs-nomule and tried both the mule and no-mule version
[/LIST]

Any advice would be greatly appreciated.

---

### Post by nardis_Miles1 on 2007-03-05
Using the standard xorg xserver, I have been able to repair the font problem. Here is a snippet of my xorg.conf file:

Section "Files"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/truetype/msttcorefonts"
        FontPath        "/usr/share/fonts/truetype/ttf-bitstream-vera"
        FontPath        "/usr/share/fonts/truetype/freefont"
        FontPath        "/usr/share/fonts/truetype/ttf-xfree86-nonfree"
        FontPath        "/usr/share/fonts/truetype/dustin"
        FontPath        "/usr/share/fonts/truetype/openoffice"
        FontPath        "/usr/share/fonts/truetype/ttf-lucida"
        FontPath        "/usr/share/fonts/truetype/ttf-gentium"
        FontPath        "/usr/share/fonts/truetype/ttf-dejavu"
        FontPath        "/usr/share/fonts/truetype/latex-xft-fonts"
        FontPath        "/usr/share/fonts/type1/gsfonts"
        FontPath        "/usr/share/fonts/type1/gsfonts-other"
        FontPath        "/usr/share/fonts/type1/t1-xfree86-nonfree"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

Note that I put the 75dpi:unscaled fonts first. This seemed crucial. Also, I am using xfs.
If you are on a laptop then you should use the subpixel hinting tools under use anti-aliasing fonts for KDE (similar tools are under fonts, I believe in the preferences menu).

HTH

---

### Post by nardis_Miles1 on 2007-03-05
I now have a problem with both emacs and xemacs under beryl/Xgl. I have tried a couple of the -fp possibilities, but I cannot put the 75dpi:unscaled path without killing Xgl. Any insight would be welcome

---

