---
title: "Installing all MS Fonts"
date: 2018-12-15
forum: General Help
---

### Post by G0at1 on 2018-12-15
Hi!

I'm trying to install all MS fonts and need some help. I ran some commands but I believe I didn't get more than 25-30 fonts. I also have copied over 500 fonts from my C:/Windows/Fonts folder to my Ubuntu desktop. How do I copy everything to Ubuntu? I searched for "calibri" in the forums but got 2 pages of non-font related posts. So far, I've done this:

```
sudo apt update 
sudo apt-get install ttf-mscorefonts-installer
mkdir .fonts
wget -qO- [http://plasmasturm.org/code/vistafonts-installer/vistafonts-installer](http://plasmasturm.org/code/vistafonts-installer/vistafonts-installer) | bash                           
sudo fc-cache -f -v
```
  
Thank you

---

### Post by HermanAB on 2018-12-15
There is no need for loading MS fonts anymore.  Red Hat created the Freedom Fonts years ago, which are equivalent to the MS True Type fonts.

---

### Post by Holger_Gehrke on 2018-12-15
@HermanAB: while the Liberation fonts are *metrically* identical to the MS fonts, they don't look *exactly* identical - there are subtle differences (mostly to avoid plagiarism or copyright problems). If you're working in an environment where the use of specific fonts is mandated (think 'corporate identity'), you need to use those.

@onavida: If you did use the commands you've quoted correctly, you should have a folder '.fonts' in your home directory. If you don't see that folder in your file manager, check whether it's set to display hidden files; files and directories whose name starts with a '.' are considered hidden and will only be shown in file managers and the shell if you explicitly tell them to show those files. That mechanism is not any kind of secrecy or security mechanism, it's meant to avoid cluttering up your view with stuff you rarely need to manipulate yourself. If you just copy the font files to that folder they should be available for use in all applications.

Holger

---

### Post by G0at1 on 2018-12-16
Thank you Holger! Copy/pasting to the fonts folder worked.

---

### Post by HermanAB on 2018-12-17
"they don't look exactly identical" - How many people can actually see those differences?

---

### Post by Holger_Gehrke on 2018-12-17
> **HermanAB said:**
> How many people can actually see those differences?

If you're comparing them side by side the differences are quite pronounced (serifs at an angle to the horizontal on vertical strokes in Times, horizontal serifs in Liberation; drop-like ends on some curves (top of "a" and "f", bottom of "y") in Times, serifs in Liberation); visibly different angles at which some strokes meet ("a" and "d"). The basic shapes are the same, but a lot of small details are different.

Holger

---

