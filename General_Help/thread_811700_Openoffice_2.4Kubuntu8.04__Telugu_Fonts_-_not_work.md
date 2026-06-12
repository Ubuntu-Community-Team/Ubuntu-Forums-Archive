---
title: "Openoffice 2.4/Kubuntu8.04  Telugu Fonts - not working..."
date: 2008-05-29
forum: General Help
---

### Post by ddrake on 2008-05-29
Hello

 Am using openoffice 2.4 on Kubuntu 8.04.

 Am helping a friend use telugu language in openoffice.

My problem: After installing ttf-telugu-fonts (from adept manager), I have
the telugu Font POTHANA2000 installed. 

 After adding telugu keyboard language support, when I type some
telugu content in POTHANA2000 font in openoffice writer, I get it
in another font (Vemana).  Am unable to convert a telugu text piece
to the POTHANA2000 font.

Am able to successfully do this on Kubuntu 7.10 using openoffice 2.3.

POTHANA2000 being a popular font, this problem is turning to be a BIG
turnoff for some new users of HARDY HERON.

Can someone help please..........


thanks a ton
DDRAKE

---

### Post by ddrake on 2008-05-30
Hi

 A **workaround **that I did was to remove the vemana font from the system (in kubuntu 8.04 I moved it out of /usr/share/fonts/truetype  folder.  then did a 'fc-cache -fv' to update the fonts cache).

This ensured that POTHANA2000 fonts were truely used.

Also, I then copied the Vemana fonts into my home folder's .fonts directory and did a 'fc-cache -fv' ... and the problem reappeared.


Kindly help fix this problem

thanks a ton
Ddrake

---

### Post by Frogbarf on 2010-06-09
I looked at the Vemana font with Font Viewer under Ubuntu 8.04 Hardy Heron, and noted that the "name" is Vemana2000, but the "Style" is Pothana2000. Styles are normally things like regular, bold, italic, and so on.

It wouldn't surprise me at all that having a "style" that is the same as another font's "name" causes trouble.

Anyone troubled with this problem may want to use Fontforge to change the style of Vemana to "regular" and see if that resolves the problems they are experiencing. Don't forget to rebuild the font cache via fc-cache -fv afterwards and restart your applications. (I haven't tried this myself.)

Ubuntu 8.04 provides v. 1.1 of Vemana, dated 2005. The font gallery at [www.wazu.jp](www.wazu.jp) implies this is the current version of Vemana.

PS: I opened Vemana.ttf with Fontforge. (You have to lie and say you have a license to fiddle with the font.) Under Element>Font Info>TTF Names, "UniqueID", "Fullname", and "Preferred Styles", it reads "Pothana2000". I suspect that this is the root of the problem, not the misleading style "Pothana2000" that Font Viewer shows.

Unfortunately, since ttf-indic-fonts-core is a Synaptic package, and installation of a font package involves obscure files other than the directory and the .ttf files in it, directly editing Vemana.ttf may cause problems. If you try direct editing and start having difficulties, uninstall ttf-indic-fonts-core completely using Synaptic, then reinstall it to get back to where you started.

If anyone tries this, give us a report back.

---

