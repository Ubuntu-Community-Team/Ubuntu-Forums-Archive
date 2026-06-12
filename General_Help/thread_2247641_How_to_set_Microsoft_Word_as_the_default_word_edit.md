---
title: "How to set Microsoft Word as the default word editor on Xubuntu"
date: 2014-10-09
forum: General Help
---

### Post by neilajarn on 2014-10-09
[FONT=comic sans ms]I've installed Microsoft Office 2010 using PlayonLinux on Xubuntu 14.04.1

I would now like to set Microsoft word as the default editor for word files. Previously I had Libre Office installed and this was the default editor, so I removed Libre office but after,  when right clicking and selecting open with on a word file, there is no option to select open with Microsoft Word.

Any tips appreciated. 

Thanks.[/FONT]

---

### Post by nerdtron on 2014-10-09
Does microsoft word shows in the open with option?

Right click on a doc file > Open With: > Open With Other  Application... > (select and check "Use as default for this kind of  file")

I have tried this before not sure if it works now. I don't set wine applications as my default applications since they are slow to load up.

---

### Post by ajgreeny on 2014-10-09
It's a long time since I used wine but I think you can use the right click **"Properties ->Open with->Open with other application"** then choose the **"Custom command"** and add in whatever the command is to start MS Word, probably something like **wine /home/***username***/.wine/drive_c/path/to/word.exe**

I may have got the first part of the pathway completely wrong but I just can't remember the pathways that wine uses any more.

---

### Post by neilajarn on 2014-10-10
[FONT=comic sans ms]Many thanks ajgreeny, that should fix my problem.[/FONT]

---

### Post by neilajarn on 2014-10-14
Yes that works very well. I copied and pasted the path to the winword.exe file from the existing shortcut for Mircosoft Word on the desktop and it worked. It is a bit slow to open up but the people who needed this prefer to work with Microsoft Word as they are more familiar with it. Thanks again.

---

### Post by LinuXoDus on 2014-10-17
Hi,

got stuck at the same thing... I would like to open PDFs with DPF-XChange Editor by default.
It works perfectly fine if I double click on the icon on my desktop placed by the wine installer and I am able to view PDFs.

However, if I right-click on a PDF file and follow the above **"Properties ->Open with->Open with other application"** I do not see anything such as **"Custom command".**
Is this somehow hidden or am I doing something silly?
Thanks for your help.

PS: I just noticed that you talk about  Xubuntu while I am on Ubuntu. Would this explain the difference and  where do I find "Custom command" in Ubuntu if so?

---

### Post by neilajarn on 2014-10-25
In Xubuntu first right click on the file, then select "Open with other Application" you are then presented with a window which lists applications and at the bottom of the window you can click on "Use a custom command", this is where you enter the path for the application to open with. 

I've not done this on Ubuntu, presumably its the same though ?

---

