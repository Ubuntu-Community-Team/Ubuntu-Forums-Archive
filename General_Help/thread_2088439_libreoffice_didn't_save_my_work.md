---
title: "libreoffice didn't save my work"
date: 2012-11-26
forum: General Help
---

### Post by greatsirkain on 2012-11-26
I've just spent 9 hours straight doing an assignment that's has to be in today, saved it every hour, when I wentto reopen it to sendthe damn page is blank. There has to be some way of recovering all the data?? I tried opening different editors and getting recent documents but it's the same blank page, can anyone help?

---

### Post by Mark Phelps on 2012-11-26
OH OH, I fear the worst for you ...

You need to see if the file is now zero-size.  You can do that by looking at the file properties in Nautilus of by opening a terminal and enter "ls -l filename" (lowercase L, filename = name of the file).

If it IS zero size, then it is gone.

I had the same happen to me -- and was able to determine that this was a BUG in Open Office.  Which is why I quite using it.  It looks like the same bug may have carried over to LibreOffice.

---

### Post by Vaphell on 2012-11-26
i know it's too late but never work on single copies of important documents. Create 'snapshots' too so you have something to fall back on, also they prove useful when you want to roll back to some earlier version.
In preferences look for autosave/autobackup option (i think it's disabled by default)

---

### Post by greatsirkain on 2012-11-26
from what I've read in other threads libreoffice has a nervous breakdown if you try to save in .docx, I don't really see the point of having an option that not only doesn't work but robs precious hours of your life from you. Bah, phoned tutor, got a 24 hour extension.
So openoffice does the same? Great lol.
I didn't mean to just close it like that without copying and pasting it into something else, I was just that tired & thought oh well at least it's saved. Nevermind stuff happens.

---

### Post by rs99cool on 2013-04-15
I've got the same problem, saved a document today in .docx with LibreOffice and several minutes later needed to go back to it and the document opened with a blank page!  This was an important document that my wife needed and I couldn't figure out how to get it back.  The strange thing is that the saved document shows the time it was saved, correctly, and it shows the file is 4.7 kb in size, not zero, so everything thinks the document is there, everything except LibreOffice!  Anybody got any ideas on how to bring the document back?  I don't have any other programs installed that can read .docx files ... but I do have my wife's computer with Windows and MS Word on it.  So, I've copied the file to a thumb drive, loaded it onto my wife's computer ... and by golly it's there, IN WORD!  The formatting is a little screwed up, thanks to LibreOffice not being able to get all the parts of the .docx puzzle in place, but all the information is there.  OK, guys, I'm stumped.  What a great workaround!  When LibreOffice doesn't save something correctly, just go find a Windows computer with MS Word on it, and open the file up there.  What insanity!
           :confused:

---

### Post by Vaphell on 2013-04-15
as a general rule try to work with the native formats of the program, and only then create knockoff copy in a foreign one. When working with open/libreoffice I'd save the work-in-progress doc as .odt and only then export to .docx. 2 different formats = 2 times safer ;)

---

### Post by kurt18947 on 2013-04-16
I've not had the 'pleasure' of this occurence.  I'd read of it and thought it happened on ext4 file systems, not on ext3 systems.  My thought was to save a backup on something like a FAT32 flash drive.  I don't know if it would help though.

---

