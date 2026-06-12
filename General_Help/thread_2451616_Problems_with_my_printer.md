---
title: "Problems with my printer"
date: 2020-10-07
forum: General Help
---

### Post by steapasntr on 2020-10-07
I'm having problems making my Epson L3110 printer to work with Lubuntu 64bits.

After installing the drivers I get the following mesage: 

Idle - File "/usr/lib/cups/filter/opt/epson-inkjet-printer-escpr/cups/lib/filter/epson-escpr-wrapper" not available: No such file or directory

The directory do exists, and when I click on the executable "epson-escpr-wrappe" nothing happens. 

Any help?

---

### Post by TygerTung on 2020-10-07
I don't know about this printer, but I have found with my HP 5Si, that there are a number of drivers avaliable in CUPS and I have to use trial and error to see which is the one which works. Some spit out endless blank pages etc.

Are you setting up your printer by typing in "http://localhost:631/" into your browser?

---

### Post by steapasntr on 2020-10-07
No, i'm using the "printers" utility that comes with lubuntu.

---

### Post by TygerTung on 2020-10-07
Try CUPS, it is easy enough to use. Just go to [http://localhost:631/](http://localhost:631/)

---

### Post by guiverc on 2020-10-08
You haven't mentioned your release of Lubuntu, thus which desktop you are using (legacy with LXDE or LXQt as has been on the last four releases of Lubuntu).

I'll provide the Lubuntu manual page for printers, [https://manual.lubuntu.me/stable/3/3.2/3.2.19/Printers.html](https://manual.lubuntu.me/stable/3/3.2/3.2.19/Printers.html) but not know your desktop or release, I'm reluctant to go further.

(from the main menu, type PRI and you'll see printers appear, you can click ADD to add printers etc.. but without release details & knowledge of your desktop, I can't know if this applies to you).

---

### Post by tomchua on 2020-12-09
> **steapasntr said:**
> I'm having problems making my Epson L3110 printer to work with Lubuntu 64bits.

After installing the drivers I get the following mesage: 

Idle - File "/usr/lib/cups/filter/opt/epson-inkjet-printer-escpr/cups/lib/filter/epson-escpr-wrapper" not available: No such file or directory

The directory do exists, and when I click on the executable "epson-escpr-wrappe" nothing happens. 

Any help?
Please select  L310 in Epson drivers database  
it work well~

---

