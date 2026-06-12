---
title: "themes and customization"
date: 2014-02-20
forum: General Help
---

### Post by beelzebufo on 2014-02-20
I am just wondering if the devs are working on fixing how difficult it is to customize our themes.  Even just the ability to change the color would suffice for most of us.  I have seen a lot of threads regarding this, and I believe that simply adding the ability to change color would create a much welcomed return to the customization that we used to love with gnome.  I have literally spent hours in the past simply trying to change the orange to blue.  I am not sure if I am putting this in the right place, but I think that most of us relatively new guys.. and experienced guys alike would agree that this needs to change.  I appreciate that orange is the official color of ubuntu, but I hate it.  One of the things I loved so much about ubuntu was that it felt like MY operating system and I feel like that is changing, please allow us to change our themes and colors to our liking without having to spend hours trying to find a theme package that will both function with unity and looks the way we like.  

if there is anything that I can do to help this come to fruition, please let me know.

thanks
beelze

---

### Post by grahammechanical on 2014-02-20
You should direct your request to your beloved Gnome developers. They are the ones that have made this change. After all, we are using gnome utilities, are we not?

We sometimes forget that Ubuntu is also a community developed project. Space is left by the official Ubuntu developers for others to have a share. And this is the most unlikely place to put this request. It is just a user forum. That is all.

Regards.

---

### Post by mcduck on 2014-02-20
It took about 10 years for the Gnome devs to add basic color editing support to GTK2, and that was right before everything moved into Gnome3 and GTK3. I wouldn't really expect the color changing to become an option any time soon, if ever.

That being said, it should be possible to write a theme with color editor for it. To some degree that's what the Ubuntu themes package already does when installing the default themes so it's pretty much a question of creating a GUI to change the colors rather than defining them in the install script.

Anyway, you can already change the theme to whatever you want, it's just creating the themes that's difficult. So the easy option is to just head to gnome-look.org and pick any recent GTK3 theme you like... ;)

---

### Post by vasa1 on 2014-02-20
> **beelzebufo said:**
> I am just wondering ...
```
$ apt-cache show gtk-theme-config
Package: gtk-theme-config
Priority: optional
Section: universe/gnome
Installed-Size: 128
Maintainer: Xubuntu Developers <xubuntu-devel@lists.ubuntu.com>
Architecture: amd64
Version: 1.0-1
Depends: gconf2, gsettings-desktop-schemas, libc6 (>= 2.3.4), libglib2.0-0 (>= 2.35.9), libgtk-3-0 (>= 3.4.2)
Recommends: xfconf
Filename: pool/universe/g/gtk-theme-config/gtk-theme-config_1.0-1_amd64.deb
Size: 22684
MD5sum: 6f895241c45788a1c0bc6dcc4d48f447
SHA1: 1292cd635d2807af6ebfcee97e141341dfe5cef2
SHA256: 2bce54ca124840eacba8c25823514927e9954ae6552fd81ee1d3fcd60d3b364a
Description-en: simple interface to change GTK+ themes
 Change some basic elements of a GTK+ theme easily (both GTK2 and GTK3)
 with a simple interface.
Description-md5: f39e1d037031e524e23ba795bcae1f7e
Homepage: https://github.com/satya164/gtk-theme-config
Description-md5: f39e1d037031e524e23ba795bcae1f7e
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: xubuntu-desktop

```
may help

---

### Post by vasa1 on 2014-02-20
> **beelzebufo said:**
> ...  I have literally **spent hours in the past** simply trying to change the orange to blue.  ...
if there is anything that I can do to help this come to fruition, please let me know.
...
Yes, please provide any links to where you have asked in this forum for specific help re. changing orange to blue.
I just looked at your history but didn't find any at all :(

---

### Post by Frogs Hair on 2014-02-20
I have been using this application . [http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html](http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html)

---

### Post by beelzebufo on 2014-02-20
vasa1, this is strange, I have posted several times over the last year or so about it (I reinstall a lot) but the earliest post that is listed for my posts is this one. [http://ubuntuforums.org/showthread.php?t=2202603](http://ubuntuforums.org/showthread.php?t=2202603) Which was written at about 4 am after banging my head against the wall for a few hours trying to change things to blue, so it's not titled correctly and the question isn't very clear.  To be clear, I have gotten my theme close enough to the way i want it.  I am not messing with it anymore, I will lose my mind if I have to deal with trying to change it again.  But I saw a post on the beginner's forum with the same problem, I have seen the same frustrated posts again and again, so I just wanted to see if anyone knew if they were doing anything about it...  It doesn't seem like allowing for color change would be that difficult, but, I am no expert.  As far as just doing the gnome look thing, I have had a lot of problems with doing it that way, I frequently end up with this weird unreadable color scheme on the drop down menus, anyway, thanks for the responses, and I will try that app frogs hair, I don't think I have seen that one before.

edit: I tried that link you posted frog, and I can't connect to the page, I have had a lot of repo issues and just problems in general with webupd8 lately, not sure why, it's all a conspiracy, "Beelzebufo must NEVER have a blue theme!!!!! mwahahahahaha!!"

thanks again guys, if you are app writers, write a color change app, I would gladly pay for it.

---

### Post by vasa1 on 2014-02-20
> **beelzebufo said:**
> ... edit: I tried that link you posted frog, and I can't connect to the page, ...
No need for a ppa or for that link. Just install what I posted earlier; it is the same thing. Looks like you didn't read carefully enough ;)

```
$ apt-cache show gtk-theme-config
Package: **gtk-theme-config** <<<<<<<<<<<<<<<<<<
.
.
.
.
.
[B]Description-en: simple interface to change GTK+ themes <<<<<<<<<<<<<<<<<<<<
 Change some basic elements of a GTK+ theme easily (both GTK2 and GTK3) <<<<<<<<<
 with a simple interface.[/B] <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
Description-md5: f39e1d037031e524e23ba795bcae1f7e
Homepage: https://github.
```
So just run ```
sudo apt-get install gtk-theme-config
``` and then you can start changing at least some colors!

---

### Post by vasa1 on 2014-02-22
I forgot to mention lxappearance. It is in the software center and allows a limited amount of editing under the "color" tab.

---

### Post by Frogs Hair on 2014-02-22
> [COLOR=#000000]: I tried that link you posted frog, and I can't connect to the page.[/COLOR]

Sorry the link works fine here, but if you can get the same application without a PPA even better.

---

