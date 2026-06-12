---
title: "[SOLVED] How to view mutiple pages of tiff format files"
date: 2008-04-23
forum: General Help
---

### Post by hosammy on 2008-04-23
I am using version 8.04 and I also use the Fax to email to receive my fax.
The email attachement the fax as tiff format file.
Previously I use the "evince" to view this kind of files and can read multiple page, but now I can only read the first page.
Please advise what other applications can suit my purpose?

:(

---

### Post by _sAm_ on 2008-04-23
If I understand you correct; 

You can still use Evince for tiff, and view/read multiple page. 

Open Evience and right click on the toppanel and choose Toolbar(or Edit > Toolbar). Add "sidepanel" and "Continuous"(and "dual" if you have a large screen). Then you can go from one page to another.

---

### Post by ryanhaigh on 2008-04-23
From the command line you could use tiff2pdf to convert the tiff to mutlipage pdf or tiffsplit to split the multipage tiff into separate tiff images. This utilities are available in the package [libtiff-tools](apt://libtiff-tools) < click on this link to install.

There is also [ghfaxviewer](ghfaxviewer) which can also read these files although I have never personally used it.

---

### Post by hosammy on 2008-04-23
> **_sAm_ said:**
> If I understand you correct; 

You can still use Evince for tiff, and view/read multiple page. 

Open Evience and right click on the toppanel and choose Toolbar(or Edit > Toolbar). Add "sidepanel" and "Continuous"(and "dual" if you have a large screen). Then you can go from one page to another.

I have tried, but the file clearly have 11 pages in Windows image viewer but only shows the first page in "evince" even I have added the sidepanel, continuous page.

Please advise ...

---

### Post by hosammy on 2008-04-24
> **ryanhaigh said:**
> From the command line you could use tiff2pdf to convert the tiff to mutlipage pdf or tiffsplit to split the multipage tiff into separate tiff images. This utilities are available in the package [libtiff-tools](apt://libtiff-tools) < click on this link to install.

There is also [ghfaxviewer](ghfaxviewer) which can also read these files although I have never personally used it.

The ghfaxviwer can suit my purpose, I think my problem is solved.
Thank you to all for using efforts to help me.

:lolflag:
:guitar::popcorn:

---

### Post by ryanhaigh on 2008-04-24
You might want to use thread-tools in the top right of this page to mark this thread as solved so others know that there is a solution presented here.

---

### Post by hosammy on 2008-04-27
> **ryanhaigh said:**
> You might want to use thread-tools in the top right of this page to mark this thread as solved so others know that there is a solution presented here.

But the [Solved] tool seems to be removed, I cannot find it under thread tools.

:confused:

---

### Post by ryanhaigh on 2008-04-27
Yeah sorry about that seems its one of the features yet to be implemented in the new forums.

---

