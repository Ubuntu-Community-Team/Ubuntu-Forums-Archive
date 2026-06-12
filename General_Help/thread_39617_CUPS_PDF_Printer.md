---
title: "CUPS PDF Printer"
date: 2005-06-05
forum: General Help
---

### Post by oritpro on 2005-06-05
Has anybody figured out how to get this working?

It would appear to provide the same functionality as Adobes PDF print driver for Windows.  When you try and set it up, it asks for a driver.  IS there a specific driver that should be used for this?

I'd like to be able to print directly out to a PDF file with minimal hassle..

---

### Post by az on 2005-06-05
What do you mean it asks for a driver?  In my case, it woked out of the box.


EDIT:

I see what you mean,  I cannot print to pdf from firefox, but It works from abiword.


Hmmm....

---

### Post by az on 2005-06-05
Quote Leszek Tarkowski:

You have to edit /etc/cups/cupsd.conf
sudo nano /etc/cups/cupsd.conf
change RunAsUser from Yes to No.
sudo /etc/init.d/cupsys restart
Restart cups: sudo /etc/init.d/cupsys restart

It is up to you to decide if this is wise... 


I created a cups printer with a raw driver.

Everything you print-to-pdf gets pu into a folder named cups-pdf in your home drive...

---

### Post by oritpro on 2005-06-05
You da man!

Works like a charm, thanks  \\:D/

---

### Post by rwabel on 2005-08-09
[QUOTE=azz]Quote Leszek Tarkowski:

You have to edit /etc/cups/cupsd.conf
sudo nano /etc/cups/cupsd.conf
change RunAsUser from Yes to No.
sudo /etc/init.d/cupsys restart
Restart cups: sudo /etc/init.d/cupsys restart

It is up to you to decide if this is wise... 


I created a cups printer with a raw driver.

Everything you print-to-pdf gets pu into a folder named cups-pdf in your home drive...[/QUOTE]
What raw driver? I can choose from generic and then some postscript drivers. I've cups-pdf installed, but can only print ps files

---

### Post by lonetree on 2005-10-26
Hi, 

unfortunately, in breezy, cups-pdf does not put the output to cups-pdf in the home folder anymore, it just dump the result in the home folder, no cups-pdf folder is created by default. Is there a way to edit any conf file or anything?

regards,

---

### Post by anil_robo on 2006-03-07
[quote=oritpro]You da man!

Works like a charm, thanks  \\:D/[/quote] 
I think it prints pdf files for me, but where are the files??? I can't see them anywhere, not can I find them in search!!! :(

Edit: The instructions were a little unclear or I am a little more noob than I think. I had to setup a new printer using the newly installed virtual pdf printer:

1. Install cups-pdf package
2. Now restart your computer or do a virtual reset of cups driver by sudo /etc/init.d/cupsys restart
3. Then go to System--> Administration--> Printing
4. Add printer
5. Select "Local Printer" and use a "detected printer--> PDF printer".
6. Manufacturer--> Generic,
7. Model-->PostScript Color Printer,
8. Driver-->Should come preselected with a green dot (rev3a)
9. Apply
 10. Your pdf printer should be up and running by now... test it by printing a page from firefox or openoffice.
 NOTE: **The printed files go to your home/PDF/ folder. **

---

