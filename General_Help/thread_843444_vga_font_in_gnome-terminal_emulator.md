---
title: "vga font in gnome-terminal emulator"
date: 2008-06-28
forum: General Help
---

### Post by BattlePanic on 2008-06-28
I would like to use the classic, bitmapped "vga" font inside of gnome-terminal.  I find this font looks the best in a terminal window.

I have configured the console framebuffer to display text using the vga font (it's configured to use "fixed" by default).  I did this by issuing the command:

```
sudo dpkg-reconfigure console-setup
```

My virtual consoles now use the vga font that I liked, so this vga font must exist somewhere on my system.  I'm just not sure where.

I have also enabled bitmapped fonts to be used under gnome by issuing the command:

```
sudo dpkg-reconfigure fontconfig-config
```

Even now that bitmapped fonts are enabled, gnome-terminal does not make the vga font available in it's configuration menu.  I'm wanting to know what this vga font is named, where it's located on my system, and most importantly, how I can set gnome-terminal to use it.  Thanks for any help.

---

### Post by Forlong on 2008-06-29
I don't think that "vga font" is accessible in a graphical environment.
I guess you just have to look for a real font that looks similar to it.

Unfortunately, I have no idea what it looks like.

---

### Post by BattlePanic on 2008-06-29
Thanks for the advice.  "Fixed" is the only other choice presented when reconfiguring the console font.  "Fixed" does also show up as an available font for gnome-terminal, so long as you've enabled bitmapped fonts.  The "VGA" font is nowhere to be found, though.

If anyone can shed some light I'd be very grateful.  Surely there must be a way to use the "VGA" bitmapped font under gnome.

---

### Post by BattlePanic on 2008-06-29
After a bit of searching I found some [framebuffer documentation]("http://docs.blackfin.uclinux.org/doku.php?id=the_framebuffer_console") that seems to suggest that the fonts made available to the framebuffer console are compiled-in.  In other words, these fonts hard-coded into the framebuffer console itself and not read from a font file.  This might explain why I can't find the VGA font I'm looking for.

---

### Post by BattlePanic on 2008-07-01
After some further hunting I've managed to find the location of console fonts on my system.  It seems that console fonts are gzipped and in the .psf format.  I found these files in /etc/console-setup/ and /usr/share/consolefonts.

The particular font I wanted was /etc/console-setup/Uni1-VGA14.psf.gz.  I copied this file to my home directory, unzipped it to an uncompressed .psf file and then got to work figuring out how to make it available under gnome.

Turns out I needed to use a program called gbdfed which can be found in the Hardy repositories.  gbdfed is an X windows font editing program which among it's many features, allows the importing and manipulation of console .psf fonts.  To install it, type the following command in a terminal window:

```
sudo apt-get install gbdfed
```

Using gbdfed I imported the font and found I had to edit the resulting font's properties so that it specified the proper character set the font was for and all that good stuff.  Honestly, I'm not completely sure what was what.  Using gdfed I just opened an X font that I knew was already available to my system and used that as a reference for filling in the font properties.  If you want more detailed info on font properties, I found [this pdf file online]("h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V51B_ACRO_SUP/XLFD.PDF") that should provide some insight.  Do a google search for XLFD or XLFD.pdf if the link I gave you is dead.


Once I had the font properties changed to what I thought seemed reasonable, I then saved the font as a .bdf file and moved it to my .fonts/ directory.  Finally, I updated by font cache by issuing the command:

```
sudo fc-cache -fv
```

I then tried to set gnome-terminal to use my newly created font and to my surprise it actually showed up in the list of available fonts.  Hooray.

---

