---
title: "Libre office writer"
date: 2016-02-12
forum: General Help
---

### Post by arranskye on 2016-02-12
Hi     every time I try to open an existing document I get the recovery screen.  This also happens when I create a new document, name and save it and immediately try to open it again. The recovery screen offers the option to "start recovery"  I click this and the status shows "recovery failed" however the document opens.
 
Also when I open Libre from the launch icon, instead of coming up with a new blank document as it used to do, the screen opens with the set list of liber programmes:  text doc, spreadsheet, presentation etc.

To the best of my knowledge I have not shut down the PC before closing all open documents 

All help much appreciate.  Thanks.

---

### Post by grahammechanical on 2016-02-12
Which version of Ubuntu? Which version of Libreoffice?

Sometimes, when we get an upgrade to Libreoffice we do get the presentation of the list of Libreoffice applications. It seems that the launcher icon is linked to Libreoffice and not to Writer or Calc. Have you tried opening Libreoffice, selecting to open a new, blank Writer document and then locking that icon to the launcher and then using that icon to launch Writer each time?  

As you have noticed, shutting down the OS without saving and closing Libreoffice documents will present a recovery option when we next open Libreoffice. Recovery can fail if we have have documents on another partition that has not yet been mounted. Then we get a kind of loop. I have had this happen to me.

Try Copy and Paste the information into a new document and saving it with the same name. Why this should happen with a new document that has been saved I do not know. I cannot help you with that.

Regards.

---

### Post by amanchesterman on 2016-02-12
I think your second problem occurs simply because your launch icon starts Libre Office: the 'Office' suite includes all the programmes (Writer, Calc, Impress etc.), so they are all displayed for you to use.
On my system -- which is Xubuntu -- my start menu has **separate** start icons for each of the programmes as well as for 'Libre Office' itself. If I choose the Office icon I see the full set of programmes, just as you do, but if (for example) I choose Writer then I only see a new blank document.
So your remedy is probably to create a start icon for Writer, not for the whole office suite. How you do that in the Unity desktop I don't know because I don't use it, but there are plenty of tutorials about.

---

### Post by drs305 on 2016-02-12
The recovery option may not be for your current document, but for an older one. Check the name of the file that LibreOffice is asking to recover.

Also, if you don't really need to recover the 'damaged' file, there might also be an option to 'discard' the recovery data, which may stop the recovery prompts when restarting LibreOffice.

---

### Post by Bucky Ball on 2016-02-12
*Thread moved to **General Help**.*

***New to Ubuntu*** is primarily for beginners who need 'first steps' help with the OS. (It was once called ***Absolute Beginners***.)

---

### Post by ptn107 on 2016-02-16
You can try clearing out the settings. Close Libreoffice, pop open a terminal, and run this:

```
rm -rf ~/.config/libreoffice/
```

Try opening a document now.

---

