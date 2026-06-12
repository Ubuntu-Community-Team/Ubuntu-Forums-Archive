---
title: "Printing Images in GIMP"
date: 2005-04-29
forum: General Help
---

### Post by Saptarshi Guha on 2005-04-29
Hi,
 This question has been asked, but i have not seen an answer that works. I have an HP PSC 1315(which is now recognized). I initially was using the HPLIP package, but then i moved to HPOJ. On *both*  packages, i tried the making gimp to print correctly(all other apps print ok). But nothing happens! I tried removing the -oraw option(nothing), tried forcing to Postscript 1 (again nothing). 
I have all the gimp-print related packages installed.

I have been using gtklp for some time now, but would like to get it working from gimp.

Thanks in advance for your time.
Saptarshi

---

### Post by deathburger on 2005-04-29
Not exactly a fix, but I just save the image and print from the default image viewer. It doesn't solve the problem, but it gets the images printed.

---

### Post by neighborlee on 2005-05-10
[QUOTE=deathburger]Not exactly a fix, but I just save the image and print from the default image viewer. It doesn't solve the problem, but it gets the images printed.[/QUOTE]
-------
does anyone know what is causing this behavior..i hear others able to print when they used mdk ( same for me with same printer) yet here in ubuntu gimp printing wont work..while from this poster it seems that gtklp or default viewer will get around it it would be nice to know whats causing this ..

thx anyone
neighborlee

---

### Post by tgomas on 2005-05-23
I use a HP PSC 1610 and I can print with gimp.
I let the printer defined as Postscript 2 but I set the command to lpr without any option.

However the images printed with gimp are too clear. I attempted to adjust gamma and luminosity on print preview window in gimp but results were never so good than printing with firefox.

---

### Post by tomp88 on 2005-05-23
I use Turboprint, which handles my Canon i560 very nicely.  Even if you don't use this (commercial) package, their user manual may give helpful hints on printing from Gimp.   Go to their web site which is 
[www.turboprint.de](www.turboprint.de) and on their first page you will find the user manual.  There is a section called "printing from applications".  That section covers KDE, Koffice, GIMP, etc.  In the GIMP section you will find fairly specific instructions.  As long as you have your .ppd file set up for your driver, you should be in business, whether you use CUPS or not.  

It's worth a look.

---

### Post by joele on 2005-05-23
Unfortunately Turboprint is about the only way to get the most from your printer with Linux, depending on your printer.... It is an area that really needs some effort IMO

---

### Post by tgomas on 2005-05-24
[QUOTE=tomp88]Go to their web site which is [www.turboprint.de](www.turboprint.de) and on their first page you will find the user manual.  There is a section called "printing from applications".[/QUOTE]

here was the solution to my problem.
I had to adjust gamma and saturation instead luminosity.
good values are 0.75 for gamma and 1.2 for saturation.

thank you tomp88

---

