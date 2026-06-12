---
title: "OCR Applications"
date: 2022-01-27
forum: General Help
---

### Post by angel mike on 2022-01-27
Has anyone used an OCR application that works on scanned text images and is relatively easy to install on Ubuntu 20.04 ?

---

### Post by Holger_Gehrke on 2022-01-27
Tesseract, possibly with gImageReader as a front-end. It's in the repositories. As long as the image quality and resolution is good and the layout of the document is not too crazy you'll get "good enough" results.

Holger

---

### Post by angel mike on 2022-01-27
Thanks[COLOR=#000000] [/COLOR][[COLOR=#000000]Holger_Gehrke[/COLOR]]("https://ubuntuforums.org/member.php?u=1961578")[COLOR=#000000] - will look into that. Not too familiar with bolting  it all together and running it though.[/COLOR]

---

### Post by Holger_Gehrke on 2022-01-27
No "bolting it all together" required. Just 'sudo apt install gimagereader'. This will install the front end and the libraries from tesseract it needs to work. If you want the command line version of Tesseract too, just run 'sudo apt install tesseract-ocr'. You might need some additional packages if you want to use languages beyond English (for example I've got 'tesseract-ocr-deu' installed for obvious reasons (deu->Deutsch - files for OCR in German)) or scripts different from the Latin alphabet. Do 'apt search tesseract' to see what's available.

You can also use whatever graphical tool for installation of packages your flavour of Ubuntu comes with but I usually describe the command line way of doing it because it always works the same everywhere, no matter what Desktop environment or language you use.

Holger

---

### Post by angel mike on 2022-01-28
Thanks again  				 				 					 						 	[[COLOR=#000000]Holger_Gehrke[/COLOR][COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=1961578") - will mark as solved

---

