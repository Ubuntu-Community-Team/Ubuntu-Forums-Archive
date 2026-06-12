---
title: "Openoffice file not recovered"
date: 2008-02-06
forum: General Help
---

### Post by kolibri on 2008-02-06
I downloaded an openoffice.org spreadsheet from an email attachment and was working on it.  I hit save religiously, but forgot that I hadn't initially downloaded it to the proper folder. 
 
Openoffice.org crashed.

A dialog box opened saying that two files would be recovered the next time open.org was opened.  However, this window only opened to show the upper left corner of the window, so any dialog buttons were obscured, and the x in the upper right corner would not close this window, and it would not allow any box resizing.  It is still open.

I re-opened openoffice.org spreadsheet, but did not get a recovered file or dialog.

I did a file search for all files modified in the last day and could not find my missing spreadsheet.

?- Where would the file have saved to automatically?  Where is the 'temp' folder for this sort of thing?

?- If I turn off the computer before I recover the document, will the temp file be purged?  i.e, would it be a bad idea to shutdown the computer to get rid of the dialog box, hoping that closing that box initiates the recover?

?-why isn't the file showing up in  'search for files' ?

Thanks I put in alot of hours today on that document, and really can't face doing all that work again (I swear, I hit save obsessively, I just can't find where it saved.

---

### Post by pointone on 2008-02-06
It should be in /tmp. /tmp is erased when you restart your computer.

---

### Post by kolibri on 2008-02-06
thanks, I've been looking in .tmp.

There are some .pdf files that I opened in evince from firefox, but no .ods files, and no  files saved at the proper times.

I opened the file from Thunderbird, if that helps.  But i closed thunderbird before I went looking for the file.

---

### Post by kolibri on 2008-02-06
I just made a test-

I opened another .ods file from thunderbird.  It appeared in my /tmp folder.  I saved it, and it updated in my .tmp folder.  I then closed thunderbird and it disappeared from my .tmp folder.

So, it appears thunderbird clears the .tmp folder when thunderbird is closed, not when the system is rebooted.

Am I screwed?  :(

---

### Post by Hagar Delest on 2008-02-07
Yes you are.

You should never modify a file directly opening it from the mail client because of that behavior. Save it in yours documents folders.

---

