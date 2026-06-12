---
title: "Installing fonts?"
date: 2005-11-01
forum: General Help
---

### Post by cataath on 2005-11-01
Greetings all! I'm a new Ubuntu user and am trying to install additional fonts on my system. Following the instructions on the 5.04 Starter Guide I downloaded gsfonts-x11 and msttcorefonts as per section 3, but when I got to the part where I was supposed to create a backup of /usr/fonts/local.conf, the file couldn't be found. 

I also noticed there was no .fonts directory in my home directory either. I created one and dumped a few fonts into it and they now show up in O.o, but I still don't have the x11 or MS fonts.

I'm a little concerned about the local.conf file and the .fonts directory being missing. Any help or ideas? 

Thx.

---

### Post by 23meg on 2005-11-01
If /usr/fonts/local.conf does not exist on your system it's safe to just create it. If things go wrong you can delete it later on.

As for the MS fonts, just install the msttcorefonts package. To add any missing fonts such as Tahoma, you can  put them into /usr/share/fonts/truetype and they'll show up everywhere.

---

### Post by jeremy on 2005-11-01
fonts:///

---

### Post by cataath on 2005-11-01
Well, following the 5.04 Starter Guide, I did the following:

[INDENT]sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
sudo cp /etc/fonts/local.conf /etc/fonts/local.conf_backup[/INDENT]

If I create a local.conf file, what goes into it? The directions say to find a section within that file and edit a few lines there.

Also, none of the MS fonts, Times New Roman, Arial, etc. are listed at fonts:///

Just out of curiosity, where in the file system does fonts:/// take you?

---

### Post by jeremy on 2005-11-01
To be honest, I can't remember, I now use KDE, but in gnome you can open fonts:/// in nautilus and copy true- or open- type fonts there, and they will be available in your programmes.

---

### Post by wylfing on 2005-11-01
[QUOTE=cataath]
Just out of curiosity, where in the file system does fonts:/// take you?[/QUOTE]

It goes to ~/.fonts if I'm not mistaken. (P.S. you can dump PostScript fonts in there too and it works just fine.) The way fonts work on Linux is extremely byzantine, due to historical reasons. Different environments, such as ghostscript and X11, came up with their own font solutions independently. What's worse, Gnome has font functionality that is different from both of these, but also lets you use ghostscript and X fonts as well. So it's a real mess. 

When you install fonts with a package like msttcorefonts, those fonts go into one of the "other" font locations, i.e., not ~/.fonts. Don't worry about it as long as the fonts are available in your applications.

---

### Post by 23meg on 2005-11-01
Just put this into the file:

[http://www.ubuntuguide.org/sample/local.conf_extrafonts](http://www.ubuntuguide.org/sample/local.conf_extrafonts)

---

### Post by cataath on 2005-11-01
Thanks.

I'm liking Ubuntu. And what they say about Linux users being helpful really is true.

---

### Post by l33tc0d34 on 2005-11-01
my linex pc isn't working too well tho. can u help? do i need install fonts to make grafix work?

---

