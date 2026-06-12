---
title: "bug in ooffice writer.?"
date: 2007-09-18
forum: General Help
---

### Post by anaconda on 2007-09-18
Aargh..

I am trying to do a very simple thing in ooffice writer. 

I am trying to change the whole document to use the same font, For some strange reason I have one paragraph with different font. Actually I CAN change it to Times New Roman (which is what the rest of the document is), but if I save it  that change wont stay. 

Other changes get saved, so the problem isn't with read/write permissions, I checked that, and also gave rw permission for everyone, didn't help. 

Any ideas?

---

### Post by drs305 on 2007-09-18
Are you sure it isn't an openoffice style problem? If the file is being saved on the disk, the problem is internal to the document. You can open the styles dialog with F11 or via the menu (Format, Styles & Formatting).

If it's a style problem, you might workaround the problem by copying the problem paragraph, then inserting it a letter or two prior to the end of the previous paragraph using Paste Special, unformatted. That will give the problem paragraph the same formatting (Times Roman) as the previous paragraph. Try saving it and opening and see if the formatting 'stuck'. 

If it's a style problem, you can find help at [http://documentation.openoffice.org/manuals/oooauthors2/](http://documentation.openoffice.org/manuals/oooauthors2/)  (manuals) or get to the forums via the support link.

---

