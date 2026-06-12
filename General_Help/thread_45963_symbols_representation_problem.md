---
title: "symbols representation problem"
date: 2005-07-02
forum: General Help
---

### Post by kes on 2005-07-02
sorry, if I'm putting this into the wrong section, but I have a problem with the encoding in OpenOffice (1.1 and 2.0): it seems that neither of them can understand specific scientific characters such as for example *h bar* (Plank's constant), lambda bar (Compton wavelength) and so on. The document was initially created by Microsoft Word XP. 
P.S. And from time to time it cannot show correctly some greek characters as well.... :-? 
any recomendations?
thanks.

---

### Post by kassetra on 2005-08-01
[QUOTE=kes]sorry, if I'm putting this into the wrong section, but I have a problem with the encoding in OpenOffice (1.1 and 2.0): it seems that neither of them can understand specific scientific characters such as for example *h bar* (Plank's constant), lambda bar (Compton wavelength) and so on. The document was initially created by Microsoft Word XP. 
P.S. And from time to time it cannot show correctly some greek characters as well.... :-? 
any recomendations?
thanks.[/QUOTE]

Are you trying to do scientific equations in the Word Processor part of OpenOffice?  Most likely, you want to work with the special OpenOffice Math application: 
 ```
/usr/bin/oomath
``` 
Tools->Catalog has all of the currently loaded symbols available, and you can add to it and customize the catalog quite a bit.  (Formulas/Equations can be copied & pasted into the Word Processor app when you're done.)

If you need to do a LOT of advanced equations - I don't suggest using OpenOffice tools - you'll most likely want to use LaTeX - and if you want a GUI/WYSIWYG application in order to work with LaTeX, install LyX (it's in Synaptic.)

---

