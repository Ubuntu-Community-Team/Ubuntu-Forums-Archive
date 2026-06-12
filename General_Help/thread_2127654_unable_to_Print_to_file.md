---
title: "unable to Print to file"
date: 2013-03-20
forum: General Help
---

### Post by nativehound on 2013-03-20
Using a HP F-4180 printer, I can print to the printer (local/lan) but when i try to print to a file from firefox for later bulk printing, the files in ~/Documents are not there. I checked everywhere and the files were never saved or their elsewhere in the file system. I lost about a days work. I tried to save them to my home folder but the same results. The files are not being saved. I have to redownload everything and save it manual to a folder, kinda of pain. On my other Ubuntu systems this not an issue just on Kubuntu 12.10. 

How can I fix this?

---

### Post by cortman on 2013-03-20
The default for my Firefox is to save PDFs in my Home folder, /home/cortman, not in ~/Documents. Did you look there?
Also, you can select which folder to print to in the print dialog. Try a different folder, perhaps.

---

### Post by nativehound on 2013-03-20
yup and i just tried that, it's not being saved. pdf or postscript.

---

### Post by tgalati4 on 2013-03-20
I believe the "Print-to-File" is built into CUPS directly, so you can't simply delete it and make a new print spooler for it.  You might want to check your log files in /var/log/cups and look for errors.  You might have a pathological PDF file (one that just won't print).  It's possible that the errors in the file are suppressed by the HP printer and thus you still get a printout.  You can try installing other "Print-to-File" printers in CUPS, there are a few if look through the list of printer drivers.  

Also, try "Print Preview", look through the preview to see if it renders correctly, then print from that dialog box.

It's possible that your "Print-to-File" backend is damaged and might require a CUPS reinstall.  But before doing that, look though the log files for clues.

I'm not familiar with your particular HP printer, but if it has a card reader, you may be able to print to the card reader, which leaves a file on the SD card.  A crappy work-around, but it may work.

---

### Post by nativehound on 2013-03-22
Ty, tgalati4. Reinstalling cups fixed it.

---

