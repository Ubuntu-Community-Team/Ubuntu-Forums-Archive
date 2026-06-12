---
title: "Printing a colour target to colour manage a printer"
date: 2017-02-18
forum: General Help
---

### Post by dmkonlinux on 2017-02-18
Dipping my toe in the murky waters of colour management. I've got hold of an i1pro to profile my photography workflow. I think I have got the display done using displaycal / argyll, but the printer (an Epson R360 with generic inks) is worrying me. With argyll I simply use two commands to create a target : targen and printarg. The problem is how to print this target. There are loads of guides on the net that gloss over this part by saying you must print the target with the settings for paper etc that you will eventually use but without an icc profile being applied. None of them seem to say how you achieve this simply. The favourites are use adobe color printer utility or turboprint. Adobe is out of the question and I would rather not download a programme with a 30 day limit. I'd hope to leave all that behind when I moved to linux.
I would like either a simple command to follow on from targen and printarg or a cups / gutenprint / gimp solution if possible.
Any ideas?

---

### Post by efflandt on 2017-02-18
Not sure what file types you are generating, but if it is a regular  image type you could open it using either the image viewer or gimp and  print it from there. It has been years since I printed directly from the  shell or a script, so I cannot provide details of that off the top of  my head.

When I got a Lexmark colour laser printer that was  printing too bold (like for a brochure) I downloaded a reference image  from the Internet that was a busy outdoor scene at a fair with lots of  colours, and I adjusted default settings on the printer itself until the  printed image most photo perfectly matched the image on my screen.  Those same default settings programmed into a similar printer we got at  work also worked perfectly for Windows computers there. So I can print  what look like photographically perfect images to me, on plain paper.

---

### Post by dmkonlinux on 2017-02-19
Thanks for the reply efflandt,
Correcting the colour by trial and error sounds like a tough ride with a lot of ink and paper usage, but probably not less than what I have ended up using in my efforts.
Argyll's printarg command can output either a "PostScript or TIFF     raster test file that can printed on the device"  (argyll site).
I should say I'm looking for a solution that will be transferable between computers. My dispcal / argyll system is on a bootable USB lubuntu setup.
The solution may lie in this from [URL="http://blog.worldlabel.com/2010/quality-printing-with-gimp.html"]http://blog.worldlabel.com/2010/quality-printing-with-gimp.html :
[/URL]> Unfortunately, Gutenprint does not yet support color management, so you need to apply the color transformation yourself. The LittleCMS  package includes two utilities, tifficc and jpegicc, which you can run  on the command line to do a color transformation. The basic syntax is tifficc -i *inoutprofile.icc* -o *outputprofile.icc* -t *intent* -c *quality* -b input.tiff output.tiff.[URL="http://blog.worldlabel.com/2010/quality-printing-with-gimp.html"]
[/URL]
This is actually one of the sources of my confusion when using Ubuntu. Cups / Gutenprint is not colour managed but gnome color manager assigns the printer a profile automatically "defaultRGB" or "defaultGRAY" I think from memory. Which printouts are colour managed and which are not? My understanding is that the USB lubuntu setup has no colour management therefore if I install CUPS / GUTENPRINT I will print with high quality apart from colour management. The driver has an option for "color correction : uncorrected" which is recommended if ...
> Uncorrected

 Do not apply any color correction to the output beyond generating linear 
output.  This is the best setting to use when utilizing external color management and 
generating your own profile; the high accuracy modes employ correction algorithms that
may not work well with color management.
Note:
 if you use color management with ColorSync or ICC profiles you should use profiles 
created with Gutenprint and with the exact settings that you plan to print with.  We recommend 
using the Uncorrected setting for color correction in this situation, both when creating the 
profile and when printing.  Profiles provided by the printer vendor are calibrated for the 
vendor's driver, which may not be identical to Gutenprint's calibration.  In addition, profiles 
created using Gimp-Print 4.2 or earlier will generally not perform well with Gutenprint 5.2.  
Profiles created using Gutenprint 5.0 may or may not perform well with Gutenprint 5.2, 
depending upon the printer and settings; you will need to experiment.


So if I print from the lubuntu installation with "lp filename" it should print to the cups defaults which I can set to have no colour management and all the settings I need for my paper etc?

---

