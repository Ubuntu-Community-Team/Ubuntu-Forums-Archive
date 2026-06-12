---
title: "Open .doc through wine"
date: 2008-01-24
forum: General Help
---

### Post by TrD on 2008-01-24
Hello

Im using Help & Manual 4 from HP in wine. Im making a document with links to .doc, .rtf and .pdf files. 

For testing if the links are working I need to be able to open this files through Help & Manual. I've managed to open .pdf files by installing acrobat reader in wine. Do I need to install the windows version of open office in wine to open the .doc files or is there a way to open them using the linux version of open office?

Thank you.

---

### Post by steeleyuk on 2008-01-24
Openoffice in Linux can open .DOC files. It won't open .DOCX files though...

Just open the Writer and File > Open > Select the document...

---

### Post by DrMega on 2008-01-24
You didn't need to go through Wine to open PDFs. There is a PDF viewer in Ubuntu.

---

### Post by TrD on 2008-01-24
Well, I know that. Maybe I didnt express myself correctly:

What I need is a way to open this files through a program that Im using in wine. Think of it as internet links, when I click a link I want it to open the correct page. In this case I want it to open the correct file, but because "Help and Manual" is running in wine I needed to install the windows version of acrobat reader in wine and now I want to know if there is a script or something that allows wine to open the .doc files in open office.

Sorry, I dont know how to explain better. Hope someone can help.

---

### Post by stchman on 2008-01-24
> **TrD said:**
> Hello

Im using Help & Manual 4 from HP in wine. Im making a document with links to .doc, .rtf and .pdf files. 

For testing if the links are working I need to be able to open this files through Help & Manual. I've managed to open .pdf files by installing acrobat reader in wine. Do I need to install the windows version of open office in wine to open the .doc files or is there a way to open them using the linux version of open office?

Thank you.

You can install Acrobat in Ubuntu using Medibuntu.  Evince PDF reader comes preinstalled on Ubuntu.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Openoffice can open .doc and .rtf files.  Openoffice come preinstalled on Ubuntu.

WINE is for using apps that have no Linux counterpart.  Ubuntu can do pretty much anything Windows can for FREE.

---

### Post by TrD on 2008-01-24
> **stchman said:**
> 
WINE is for using apps that have no Linux counterpart.  Ubuntu can do pretty much anything Windows can for FREE.

Im aware of that. I've been using Ubuntu, open office and evince since Jan 2006. Im not asking how to open these files, Im asking if there is a way to open them through a program that only works in Wine.

Imagine this:

1-You open a program using wine.
2- In this program there is a link that says: [[COLOR="RoyalBlue"]test.doc[/COLOR]](path_to_doc_file)
3- You click on it
4- Nothing happens because wine doesn't know how to open these files.

I know that if I install the Windows version of OpenOffice with wine it should work but I want it to open in the Linux version already installed on my system. Can be done?

I dont know how can I explain better.

---

### Post by rolodoom on 2008-05-13
Hello. Well maybe this is what your looking for, here is an explanation on how to open a propietary flash file on a wine application.
[https://help.ubuntu.com/community/Wine#head-c65dfece90dfd8c4cf9ab68a10a7854e7c81bbe2](https://help.ubuntu.com/community/Wine#head-c65dfece90dfd8c4cf9ab68a10a7854e7c81bbe2)

---

### Post by TrD on 2008-05-13
Thank you rolodoom. I don't need to do this anymore but if I need I'll try to use this method.

I had to install Virtualbox with XP to manage to do my work, unfurtunately. :(

---

