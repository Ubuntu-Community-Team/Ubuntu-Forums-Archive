---
title: "Different icons used for PDF documents"
date: 2015-02-13
forum: General Help
---

### Post by cscj01 on 2015-02-13
I have Ubuntu 14.04, but I believe this issue predates this by several versions.  Whenever I create a PDF document, most often the icon associated with the document is the first page of the document.  However, in some cases the Adobe icon for a PDF document is used.  Every PDF document I have shows Document Viewer as the default application on the Open With tab of Properties. Since I do not use Adobe Reader, I would prefer that the Adobe icon not be used.  Any suggestions as to why this is occuring and how I can change this behavior?  Thanks.

---

### Post by vasa1 on 2015-02-15
> **cscj01 said:**
> I have Ubuntu 14.04, but I believe this issue predates this by several versions.  Whenever I create a PDF document, most often the icon associated with the document is the first page of the document.  However, in some cases the Adobe icon for a PDF document is used.  Every PDF document I have shows Document Viewer as the default application on the Open With tab of Properties. Since I do not use Adobe Reader, I would prefer that the Adobe icon not be used.  Any suggestions as to why this is occuring and how I can change this behavior?  Thanks.
Do you mean the thumbnail? If yes, the icon you see may depend on the rules you set for thumbnails. Smaller files may have the image of the first page; larger files may have a "generic" icon.

Do you have Wine installed?

Which icon theme are you using?

In my opinion, the icons in */usr/share/icons/Your_icon_theme_name/mimes/* (or the corresponding folder in your home) determine what you see. I replaced icons I don't like with those I like.

---

### Post by mc4man on 2015-02-15
I could  imagine that what is 'picked' by the file manager could also be affected by file detection. Without really knowing, seems possible that some method is used to detect file/mime type. If it's successful then it gets a predetermined icon or in some type  cases a text preview.  
If it fails then the file extension is used with a predetermined icon there.

No real idea, just thinking,  but if I create a new document (empty) & name it 1.pdf it gets the adobe icon, all my other (real, successfully detected )  .pdf's get a text preview

Which it appears current gnome has stopped doing, instead of a preview just a blank icon or some icon based on ext, too bad.

---

### Post by cscj01 on 2015-02-20
Thanks for the replies.  I can say this.  If I cut the file with the Adobe icon and paste it somewhere else, it changes from the Adobe icon to the text preview icon.  So there is no change in file size.  I have looked at the mime types in /usr/share/icons/Humanity/mimes and found an svg file with an Adobe icon and a type of application-pdf.  In fact, I have found several of these in some of the other icon subdirectories.  The problem is, I'm not sure how to replace them.  I suppose I could copy one that had the text preview icon into the Humanity subdirectory and rename the one with the Adobe icon.  However, that would require me to do the same thing every time I upgraded the operating sytem or whenever an update to the theme occurred.  Which leads to another question.

If I have icons in ~/.local/share/icons, can I put mime types in a subdirectorey and have that overide what is in /usr/share/icons/<some theme, say Humanity>/<mimetypes or mimes>?

---

