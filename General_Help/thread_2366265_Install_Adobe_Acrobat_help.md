---
title: "Install Adobe Acrobat help"
date: 2017-07-15
forum: General Help
---

### Post by Camilia on 2017-07-15
I am trying to install adobe acrobat. I followed instructions from [here]("https://askubuntu.com/questions/767937/how-to-install-adobe-acrobat-in-ubuntu-16-04") with no results. The commands in the terminal gave me no suggestions. I have ubuntu 16.04. My knowledge of computer language is slim so please be specific with info. Thus please don't give me abbreviations.

---

### Post by monkeybrain20122 on 2017-07-15
> **Camilia said:**
> I am trying to install adobe acrobat. I followed instructions from [here]("https://askubuntu.com/questions/767937/how-to-install-adobe-acrobat-in-ubuntu-16-04") with no results. The commands in the terminal gave me no suggestions. I have ubuntu 16.04. My knowledge of computer language is slim so please be specific with info. Thus please don't give me abbreviations.

Adobe acrobat does not support Linux any more and that trick won't work because precise has reached eol and its repository has been removed. Why do you want Acrobat? If you can describe your need maybe others can suggest alternatives.

---

### Post by Camilia on 2017-07-15
I want to make a pdf fillable. Suggestion were to use office draw and writer. None work for me.

---

### Post by monkeybrain20122 on 2017-07-15
> **Camilia said:**
> I want to make a pdf fillable. Suggestion were to use office draw and writer. None work for me.

Okular works, so does qpdfview and evince, but with some limitations because of the poppler lib they use as backend. Other[ suggestions]("https://wiki.archlinux.org/index.php/PDF_forms")

If these don't work you can run pdf-xchange-viewer in wine. It is a Windows freeware that works very well in wine, and very light as well, I have tested it on many forms including those with scripts and it works on all of them.  Adobe is bulky, resource hungry and slow. I would prefer pdf-xchange  even if Adobe is available. Just google it. Forum rules forbids me to post a link since it is commercial.

---

### Post by #&amp;thj^% on 2017-07-15
I have used this when needed: [https://www.pdffiller.com/](https://www.pdffiller.com/)

---

### Post by speartip on 2017-07-16
Master PDF Editor.
[https://code-industry.net/free-pdf-editor/#get](https://code-industry.net/free-pdf-editor/#get)

---

### Post by Camilia on 2017-07-19
> **speartip said:**
> 
[https://code-industry.net/free-pdf-editor/#get](https://code-industry.net/free-pdf-editor/#get) [https://www.pdffiller.com/](https://www.pdffiller.com/)
With both of these the pdf got uploaded upside down.  Was able to turn the document viewed in Master PDF editor. 

Thanks everyone!

---

### Post by mastablasta on 2017-07-20
aside form a small bug writer actually does work when creating fillable PDFs.

---

### Post by Camilia on 2017-07-20
Now trying to delete text with in the document. I can't get it to work. [Here]("https://code-industry.net/masterpdfeditor-help/edit-pdf-text/#editing-text") Instructions to click on select text icon and then can change text. After outlining text to be removed can do nothing. Any suggestions?

---

### Post by #&amp;thj^% on 2017-07-20
> **Camilia said:**
> Now trying to delete text with in the document. I can't get it to work. [Here]("https://code-industry.net/masterpdfeditor-help/edit-pdf-text/#editing-text") Instructions to click on select text icon and then can change text. After outlining text to be removed can do nothing. Any suggestions?

At the top of Master PDF Editor you see tools click on that next click Edit Text.
Now with the mouse hight-lite the text/Line you want removed...and use your Delete key.

---

### Post by Camilia on 2017-07-20
> **1fallen said:**
> At the top of Master PDF Editor you see tools click on that next click Edit Text.
Now with the mouse high-lite the text/Line you want removed...and use your Delete key.
That works with text I entered on master PDF editor but not with text on the pdf. Can't get it to high light the text which was originally on the pdf

---

### Post by #&amp;thj^% on 2017-07-20
> **Camilia said:**
> That works with text I entered on master PDF editor but not with text on the pdf. Can't get it to high light the text which was originally on the pdf

The only time I have had those issues is with protected PDF's like Government (Legal) or Financial Statements from Banks and such. 
Not much to be done if those are the case.

---

### Post by Camilia on 2017-07-20
> **1fallen said:**
> The only time I have had those issues is with protected PDF's like Government (Legal) or Financial Statements from Banks and such. 
Not much to be done if those are the case.
The PDF is not a legal document. It is work week schedule.

---

### Post by #&amp;thj^% on 2017-07-20
Is it possible to attach the PDF in question here. Maybe just a blank one with just the original text intact.
EDIT: It is possible also to use the keyboard combo of while holding them down <ctrl+x> then Highlight what you need to remove then hit Delete.
Got to jet for the evening good luck.

---

### Post by Camilia on 2017-07-20
> **1fallen said:**
> Is it possible to attach the PDF in question here. Maybe just a blank one with just the original text intact.
Ok
I just want to remove my signature at the top line. I did 1 time but now can't remember how I did it. I have never attached a file at this website. Having a problem doing it. Get message that it is to big to attach. Tried to delete some of the pdf but unsuccessful. Will put it in a flickr account and link it tomorrow.

Thanks

---

### Post by #&amp;thj^% on 2017-07-21
Huh? That would have to be one big PDF then...."Get message that it is to big to attach"
Have you tried to compress the file....Right Click on the PDF and you will or should see "Create Archive" then it will wrap the PDF in a .tar.gz format that you now should be able to Attach here>
BTW did you ever try my suggestion using the keyboard combo of <ctrl+x> then Highlight what you need to remove then hit Delete.

---

