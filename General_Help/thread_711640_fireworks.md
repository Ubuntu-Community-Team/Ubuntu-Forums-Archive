---
title: "fireworks?"
date: 2008-02-29
forum: General Help
---

### Post by japephillips on 2008-02-29
one of the problems with being new to Linux is you get settled in and then find there is windows software you miss badly - i need a Fireworks equivalent BADLY, mainly for web buttons, rollovers. Specially with text shading, metallic, soft edges etc.. MUST have slice.
I can't seem to find this stuff in Gimp

---

### Post by Shazaam on 2008-02-29
Have you tried running it with wine?

[http://www.winehq.org/](http://www.winehq.org/)

and...
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Install wine through Synaptic (System>Administration>Synaptic)

---

### Post by boombox1387 on 2008-02-29
I was also going to suggest trying to install it with wine.  I got Photoshop and Dreamweaver working with wine today and according to [these tests]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=665"), Fireworks should be possible too.

If you'd rather use an open source editor, you may want to try Xara Xtreme.  Inkscape Vector Illustrator is another nice tool that draws vector graphics, but I haven't used it much for web images.  Both are available in Add/Remove if you feel like trying them.

---

### Post by japephillips on 2008-02-29
thanks, i have downloaded xara but it says it needs image magick, so i got the .tar archive of that but it extracts and does nothing, tried it in synaptics and it downloads but then does nothing. unless i am missing something!
um, where do i look for the equiv. to an exe file to click on?
well, i said i was new ...
THAT BIT is a separate problem so i have posted it as a thread 
i wanted to avoid emulators like wine so will try inkscape and xara further
thanks a lot

---

### Post by boombox1387 on 2008-03-01
When you say "downloaded xara" where did you download it from?  

If you go to Applications > Add/Remove...  search "All available applications" for Xara, check the box, and "Apply Changes," it should do all the work for you.

If that doesn't work for you, you may need to add other software sources (which would probably be a good thing to do anyway).  System > Administration > Software Sources.  Make sure the boxes are checked for main, universe, restricted, and multiverse.

If you feel like using terminal, Xara can be installed pretty easily by typing:

```
sudo apt-get install xaralx
```
and
```
sudo apt-get install imagemagick
```

Any of these methods should then add a working version of Xera Xtreme to the Applications > Graphics menu.

Hope this helps.

---

### Post by japephillips on 2008-03-01
i used add/remove which worked for Xara but after install there was a message saying it was not fully functional as 'imagemagick' was missing, so i searched for and found that on the 'net but could not get it to install from .tar

how do you get an install from a .tar file/ it extracted but i saw no setup programme to run

---

### Post by dr.silly on 2008-03-01
works fine in wine

---

### Post by boombox1387 on 2008-03-01
> **japephillips said:**
> 
how do you get an install from a .tar file/ it extracted but i saw no setup programme to run

I'm not at my Ubuntu computer right now, so I can't really try out the .tar at the moment, but you could install imagemagick by opening terminal and typing:

```
sudo apt-get install imagemagick
```

That should download and install imagemagick for you and you don't have to worry about the messy .tar download.

---

### Post by japephillips on 2008-03-02
guess it is me being new, that terminal method tells me it is already installed so i just have to find it, lol

---

### Post by 3rdalbum on 2008-03-02
Japephillips: The terminal tells you "it is already installed". Which part - Imagemagick, or Xara?

---

### Post by japephillips on 2008-03-02
xara installed ok from add/remove but there was a message saying it needed image magick, which i then got from a mirror site and extracted. couldnt find it afterwards so assumed it was not installed! i then tried the terminal method above (aptget) and during that command processing it said I had the latest version of imagemagick installed. A search only shows the extracted files and i don't know what to 'click' on to run image magick. i suppose Xara will have what it needed now though?
I have spent the time I should have been using xara (in place of fireworks) doing this and other stuff but during the next few days will try and do the actual work! That will tell if I need anything else i suppose.
btw the link you have 'where did my installed program go' is helpful to we newbies used to windows as we find our way around the new OS

---

