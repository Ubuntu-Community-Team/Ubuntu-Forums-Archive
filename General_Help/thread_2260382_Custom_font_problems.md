---
title: "Custom font problems"
date: 2015-01-11
forum: General Help
---

### Post by Neil_Annett on 2015-01-11
I've installed a number of custom fonts on Ubuntu 14.10. I did this by extracting the contents of the zipped files, then double-clicking on each font file to open it in Font Viewer, then clicking 'Install'.

This has worked fine until recently, although I have no idea where the custom fonts are located on the system – they are *not* in home/username/.fonts, usr/local/share/fonts, anywhere in usr/share/fonts (which contains the subfolders cmap, opentype, truetype, type1 and X11) nor anywhere else I can find. Nonetheless, they are available for use in all my apps.


 Anyway, I just got a new font-family, installed it as usual, and several times whilst doing this Font Viewer froze. After forcing a quit, Font Viewer showed them as installed, and they worked properly in some of my apps but not, crucially, GIMP 2.8. Here, two font names are each repeated four times in the font menu; these two fonts work, though switching between the different duplicated entries makes no difference. Of the other fonts in the family there is no sign.

If nothing else I'd like to remove the installed fonts so I can start again – but since I can't find them on the system, I can't remove them! Font Manager doesn't help – it shows the whole family as installed, but doesn't display all of them, and the remove option is greyed out.  

 How do I get rid of these fonts!?


 Thanks in advance.

---

### Post by Dennis N on 2015-01-11
If you install **fontmatrix**, it will inform you where the font file is located. The files often have different names than the actual font name:

Example:

[FONT=Courier New]Font Name: Cataneo BT Regular
File Information: /home/dmn/.fonts/TT0952M_.TTF
[/FONT]

To get file information, double click on the font in the main window, then open the Info Tab. To remove a font, delete its file. Files in /usr/share/fonts will require use of sudo to delete the files. 

In the future, to install fonts, it is sufficient to just put the font file into ~/.fonts and do nothing else. They are easy to remove if there (no sudo). All your applications will detect them. Fonts in /usr/share/fonts are accessible to all users; those in ~/.fonts are accessible by user who installed them.

---

### Post by Neil_Annett on 2015-01-11
Many thanks Dennis, this has worked. Font Matrix showed all my custom fonts in the directory ~/.local/share/fonts . I haven't seen this directory mentioned anywhere before! Anyway, most of my problems have been solved. GIMP is still a problem - I guess this is to do with the app rather than the font. As a workaround I've just installed the font I need to work on in GIMP for now.

Thanks for your help!

---

### Post by Ko_Char on 2015-01-11
~/.fonts is deprecated or going to be deprecated in the future. 

```
cat /etc/fonts/fonts.conf

<!-- Font directory list -->

    <dir>/usr/share/fonts</dir>
    <dir>/usr/local/share/fonts</dir>
    <dir prefix="xdg">fonts</dir>
    <!-- the following element will be removed in the future -->
    <dir>~/.fonts</dir>

```

For Ubuntu 12.04, the place is ~/.fonts
For Ubuntu 14.xx, the place should be ~/.local/share/fonts

---

### Post by Dennis N on 2015-01-11
> Many thanks Dennis, this has worked.
Thanks for your feedback. I have also found Fontmatrix very useful.

---

### Post by Dennis N on 2015-01-11
> ~/.fonts is deprecated or going to be deprecated in the future. 

Thanks for the information. I hadn't heard or read of that. Do you know the reason, and when it will happen? ~/.fonts is still working in 14.04, so we are ok for now (and I would guess until 2019?).

EDIT:
I did a search and coudn't find any confirming evidence of this. I don't think we can rely on a comment line in a configuration file as having much weight.

---

### Post by Ko_Char on 2015-01-13
Sorry. I'm busy these days, and can't reply you. 
The only thing I can find is this mailing list. 
[http://lists.freedesktop.org/archives/fontconfig/2014-July/005269.html]("http://lists.freedesktop.org/archives/fontconfig/2014-July/005269.html")

The changes in in 12.10 or something. It was not working at that time.
But it looks like ~/.fonts is working in 14.04. 
So may be you can continue using in 14.04. 
You can check with

```
fc-cache -fv
```

---

### Post by Dennis N on 2015-01-14
Tested ~/.local/share/fonts and confirm it is a possible font location. But it is not on the list shown in /etc/fonts/fonts.conf so another list somewhere else? And I am not familiar with the notation <dir prefix="xdg">fonts</dir> and what place it indicates.

Checked /etc/fonts/fonts.conf in 14.10 and it shows the identical list for font directories which still includes ~/.fonts.

The follow up to the linked question suggests "Use $XDG_DATA_HOME/fonts instead where [which?] is ~/.local/share/fonts in most cases" but for Ubuntu that yields /fonts which does not exist.

---

### Post by Ko_Char on 2015-01-14
I found this one.  

where is $XDG_DATA_HOME
[http://askubuntu.com/questions/13779/why-is-there-no-more-trash](http://askubuntu.com/questions/13779/why-is-there-no-more-trash)

```

$XDG_DATA_HOME defines the base directory relative to which user specific data files should be stored. If $XDG_DATA_HOME is either not set or empty, a default equal to $HOME/.local/share should be used.
```
ref: [http://standards.freedesktop.org/basedir-spec/latest/ar01s03.html](http://standards.freedesktop.org/basedir-spec/latest/ar01s03.html)

```
<dir prefix="default">
This  element contains a directory name which will be scanned for font files to include in the set of available fonts. If 'prefix' is set to "xdg",  the value in the XDG_DATA_HOME environment variable will be added as the  path prefix. please see XDG Base Directory Specification for more  details.   
```
ref: [http://www.freedesktop.org/software/fontconfig/fontconfig-user.html](http://www.freedesktop.org/software/fontconfig/fontconfig-user.html)

---

### Post by Dennis N on 2015-01-14
Well, those references give the necessary information to clear things up:

Looking to see if XDG_DATA_HOME is defined:

```
dmn@Daphne:~$ printenv | grep XDG_DATA
XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share
dmn@Daphne:~$

dmn@Daphne:~$ printenv | grep XDG_DATA_HOME
dmn@Daphne:~$

```
**XDG_DATA_HOME** is empty, so the default **HOME/.local/share is used** (I assume this is policy from the Freedesktop.org pages)

Many thanks for your information. I definitely learned a few new facts here.

---

