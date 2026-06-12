---
title: "The Numix gtk theme in 16.04"
date: 2016-04-29
forum: General Help
---

### Post by vasa1 on 2016-04-29
Several creators of gtk3 themes are using a format (for want of the correct term) that makes it more difficult to modify than previously possible.

***Please note that I'm excluding Adwaita from consideration here.***

gtk3 themes in 14.04 had a simple structure: gtk.css, gtk-widgets.css, an apps folder with app-specific css files and an assets folder with png (or svg) images. (I don't know what went on in 14.10, 15.04, and 15.10.) All the css files could be easily edited.

More recently, I can't say when, some gtk3 themes have a different structure. Even though you'll see most of the files and folders I mentioned above, there may also be gtk.gresource, and gtk.gresource.xml, a folder called scss containing *.scss files and more folders.

The point is that with such themes, you can't get away, IMO, by editing any .css file. Now, again IMO, the procedure to tweak anything is different and more complicated.

I'll stop here because I haven't gone there so far but thought I'd post this because of a thread started here: [Can't Change Selected_bg]("http://ubuntuforums.org/showthread.php?t=2322691") and the poster mentioned Numix.

The much-talked about Arc theme has the new format as well.

Xubuntu 16.04 users have the shimmer-themes package installed by default. In that, Greybird is still conventional whereas Numix has the new format.

---

### Post by vasa1 on 2016-05-03
[Easily Create Your Own Numix-Based GTK Themes With Oomox]("http://www.webupd8.org/2016/05/easily-create-your-own-numix-based-gtk.html")
From there:> As far as Ubuntu is concerned, Ubuntu GNOME, Xubuntu, Ubuntu MATE, Lubuntu and Ubuntu (with Unity) are supported. Since it requires GTK 3.16 or newer, than means you need to be using an Ubuntu 15.10 or 16.04 flavor for the themes to work.

An easier way to change theme colors would be GTK Theme Preferences but unfortunately, this tool no longer works with some themes. For instance, in Ubuntu 16.04, GTK Theme Preferences can change both GTK2 and GTK3 theme colors for Ambiance and Radiance themes, but it doesn't work with the Numix GTK3 theme. 

---

### Post by Dennis N on 2016-05-03
> More recently, I can't say when, some gtk3 themes have a different structure. Even though you'll see most of the files and folders I mentioned above, there may also be gtk.gresource, and gtk.gresource.xml, a folder called scss containing *.scss files and more folders.

These are probably themes which support gtk 3.20. To support 3.20, themes needed to be largely rewritten, from what I have read. Manjaro already is moving to gtk-3.20 and there are just a few themes that work correctly with it. 

From Manjaro forum, regarding last update:

> With this we updated Gnome and GTK to 3.20. This will break most of the themes, which will be fixed if and when their developers decide to update them.

They are providing a Vertex theme which supports gtk-3.20.

---

### Post by vasa1 on 2016-05-04
> **Dennis N said:**
> These are probably themes which support gtk 3.20. To support 3.20, themes needed to be largely rewritten, from what I have read. Manjaro already is moving to gtk-3.20 and there are just a few themes that work correctly with it. 
...
Two points ...
The use of scss, etc was possible from 15.04 onward with whichever gtk version was present. [This page about the Arc theme]("https://github.com/horst3180/arc-theme/") makes it clear:> Requirements

    Gnome/GTK **3.14, 3.16, 3.18 or 3.20**
    The gnome-themes-standard package
    The murrine engine. This has different names depending on your distro.
        gtk-engine-murrine (Arch Linux)
        gtk2-engines-murrine (Debian, Ubuntu, elementary OS)
        gtk-murrine-engine (Fedora)
        gtk2-engine-murrine (openSUSE)
        gtk-engines-murrine (Gentoo)

Main distributions that meet these requirements are

    Arch Linux and Arch Linux based distros
    Ubuntu **15.04, 15.10 and 16.04** (Ubuntu 14.04 and 14.10 are not supported)
    elementary OS Freya
    Debian 8, Testing or Unstable
    Gentoo
    Fedora 21 - 24
    openSUSE 13.2, Leap 42.1 and Tumbleweed

Derivatives of these distributions should work, as well.



gtk-3.20 has brought in *even more* changes. Just like Manjaro, the [Arch Linux guys are also complaining]("https://bbs.archlinux.org/viewtopic.php?pid=1618729#p1618729") about themes breaking in 3.20.

---

### Post by vasa1 on 2016-05-13
I found this: [https://github.com/horst3180/arc-theme/blob/master/HACKING.md](https://github.com/horst3180/arc-theme/blob/master/HACKING.md)

> This theme uses node-sass/libsass to process the various .scss files. Never edit any of the .css files manually.

And then the author goes on to describe the procedure. Some additional software needs to be installed. Judging from the names, each of the new-age themes (for want of a better term) seems to have its own procedure for hacking (aka tweaking) the theme.

---

### Post by vasa1 on 2016-06-20
**Oomox** is now available as a ppa: [http://www.webupd8.org/2016/06/tool-to-customize-numix-theme-colors.html](http://www.webupd8.org/2016/06/tool-to-customize-numix-theme-colors.html)

Keeping in mind that ...> The required GTK version is 3.16 or newer - as far as Ubuntu is concerned, that means Oomox supports Ubuntu (and derivatives: Ubuntu GNOME, Xubuntu, Ubuntu MATE and Lubuntu) 15.10 and 16.04.

---

