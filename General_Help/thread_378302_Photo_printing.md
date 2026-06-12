---
title: "Photo printing"
date: 2007-03-07
forum: General Help
---

### Post by spedsta on 2007-03-07
I have a HP 1200 all in one scanner printer. I can see it in the HP toolbox, so thats cool. I can print documents from OOO perfectly. The trouble comes when i want to print photos on 4x7 " photo paper. 

All of my apps fail to print correctly, KDE image viewers included. Gimp fails to print anything, it says printing but nothing gets printed, the printer doesn't even start printing. Some print the photos either cut off on one of the sides, or too big and cut off completely. The closest to printing correctly is with Gwenview, this prints but scaled down , leaving a huge margin on the left side of the paper.

I've spent at least 30 pages or so of photo paper trying different settings. I can't see what I am doing wrong?
:(

---

### Post by spedsta on 2007-03-07
Ok , nobody replying :) . 

Fortunately I have found possible answers(im at work at the moment), 

Heres one to get gimp working:

[COLOR="Blue"]In the GIMP
1) Go to "File | Print"
2) Select "Postscript Level 2" for your printer
3) Modify the print command by removing the "-oraw" option
4) Find the driver for your printer in /etc/cups/ppd and extract the PPD file from the tarball to your home directory. Enter the path and name under which you have saved your PPD file or choose it with the "Browse" button.
5) After closing the dialog with "OK" the fields for the options ("Media Size", "Media Source", ...) will contain the choices according to your printer. Click "Save Settings" to make your setup permanent.

Since you selected "Postscript Level 2" for your printer some of the media/page options may now be greyed out in the GIMP. Just make changes to the printer preferences by going to "System | Administration | Printing", right click on your printer, and choose "Properties" or "Edit".[/COLOR] 

another to maybe get the sizes correct for photo printing, setup your printer to use the correct size in System > administration > printers. Right click on the printer and tell it there which size you want to print on.

Will test these methods again and get back to you, even if it means I'm the only one posting to here :)

---

### Post by spedsta on 2007-03-08
**UPDATE**

I tried both solutions, and had some success , I can now print with gimp, and thats sorta sorted it out.
Although printing photos from other software was still misaligned but at least the whole photo printed without it being cut off.

I think i will stick to gimp for printing my photos for now.

I will try F-spot, but that will happen later, my next problem will be installing ADSL.

Hope this helps someone.
Cheers:popcorn:

---

### Post by jethro10 on 2007-10-26
> **spedsta said:**
> 

Will test these methods again and get back to you, even if it means I'm the only one posting to here :)

Seem like you are, but thanks. This may be my solution

J

---

