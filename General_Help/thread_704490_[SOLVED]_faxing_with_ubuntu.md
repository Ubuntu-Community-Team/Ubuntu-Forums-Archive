---
title: "[SOLVED] faxing with ubuntu"
date: 2008-02-22
forum: General Help
---

### Post by lsmobrian on 2008-02-22
I have Gutsy installed on a HP v6000.  When windows was installed I had faxed with it.  I know it doesnt come up that often but does anyone know how to fax with linux.  I have looked at ubuntu's wiki and still havent been able to send anything.  I normally use ethernet for Internet so I dont even know if my modem works under ubuntu.


Anything I check to see if my modem works, any tutorials for faxing, or any other ideas besides efax-gtk or gfax would be helpful

Thanks



I can post output from gfax if that would be helpful, maybe I've set up gfax wrong

---

### Post by kwilliam on 2008-02-22
I know in KDE there is an option in the print dialog to "print" to a fax machine.  I haven't tried it though.  Maybe there is something similar in the Gnome print dialog?

---

### Post by maljaros on 2008-03-02
For Efax one needs to first print the document as a postscript file.  The Oop Help says you do this by:
  1. Installing a PostScript printer driver, such as the Apple LaserWriter driver.
  2.Print the document with the File - Print menu command.
  3.Select the PostScript printer in the dialog and mark the *Print to file* check box. A PostScript file will be created.
I tried to substitute a pdf file (Cups offers Export to pdf file as an option) but Efax didn't accept it.
Problem is to load a driver for a printer that I don't have, which I can't figure out how to do through the Xfce GUI.  Presumably it must be done from the command line.  Can anyone tell me how to do this?

---

### Post by maljaros on 2008-03-02
Searching other forums I keep getting the message to run spadmin or a later look-alike called oopadmin, neither of which are part of my Gutsy install.  Have they been replaced by something else or do I accept that Gutsy has lost the plot with regard to sending faxes?

---

### Post by lsmobrian on 2008-03-03
[http://ubuntuforums.org/showthread.php?t=320534](http://ubuntuforums.org/showthread.php?t=320534)    

followed second post, worked great

---

