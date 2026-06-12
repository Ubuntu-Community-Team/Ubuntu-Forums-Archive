---
title: "where do TTF fonts install (location)?"
date: 2013-09-13
forum: General Help
---

### Post by Coder88 on 2013-09-13
I installed some ttf fonts, double clicking on them to see a window pop up showing the font face with a button to Install. So i click the Install button and the font(s) is installed. But to where?!? I searched everywhere I could think of in the filesystem and I do not see them. Not in /usr/share/fonts/truetype   Yet somehow installed apps, for example Trelby or FadeIn, know where they are because I can choose the installed font as a font for word processing. I can work around this by using the font files in my home directory, such as for telling Trelby (screenwriting app) what font to use for generating a PDF, and telling it where the font is to generate the PDF. But I would like to know where ttf fonts install to if not /usr/share/fonts   Also no ~/.fonts folder hidden in my home folder.

---

### Post by Buntu Bunny on 2013-09-13
Well, you could always try the locate command.

---

### Post by Coder88 on 2013-09-15
> **Buntu Bunny said:**
> Well, you could always try the locate command.

Tried that, no result (no location). I do not understand where, i anyplace, ubuntu installs fonts, or if ubuntu simply installs a reference to the location of the font file that I double click to install. I wonder if it is the latter? As I can not find the font anywhere where i would expect it (e.g. /user/share/fonts), I wonder if the actual font file (.tff) stays in its original location-- which in this case is in my Dropbox folder, and maybe that confuses ubuntu give that dropbox syncs to a cloud storage site?

---

### Post by Buntu Bunny on 2013-09-15
That's curious. I recently installed some ttf fonts and they installed in home/.fonts. The original downloads went to my download folder, where those copies still remain. 

Perhaps someone with Dropbox/cloud storage will have a better answer.

---

### Post by Coder88 on 2013-09-15
$ ls ~/.fonts
ls: cannot access /home/beowulf/.fonts: No such file or directory

---

### Post by Buntu Bunny on 2013-09-15
Try

```
ls .fonts
```

---

### Post by Coder88 on 2013-09-15
> **Buntu Bunny said:**
> Try

```
ls .fonts
```

```
$ ls .fonts
ls: cannot access .fonts: No such file or directory
```

---

### Post by philinux on 2013-09-15
Try this.

sudo updatedb

Then

locate ttf

---

### Post by Buntu Bunny on 2013-09-15
@Coder88, I don't know if you've checked this resource yet, but here is what [Ubuntu Wiki]("https://wiki.ubuntu.com/Fonts") says about installing them

> There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/<username>/.fonts (where <username> is your user name).

The easiest way to install a truetype font is to press alt-F2 and enter the following code (this will open nautilus in the right directory):

gksu nautilus /usr/share/fonts/truetype

Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Copy the fonts into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:

sudo fc-cache -f -v

The article also suggests you can create a .fonts folder if you don't already have one. Then the new fonts can be dragged and dropped to it.

---

### Post by grahammechanical on 2013-09-15
Using the commands provided by philinux they go in /home/username/.local/share/fonts. In a hidden folder (.local) in /home/username/

The files moved to the rubbish bin go there (./local/share/trash/files) as well.

Regards.

---

