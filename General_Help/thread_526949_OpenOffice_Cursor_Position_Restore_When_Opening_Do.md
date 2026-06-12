---
title: "OpenOffice Cursor Position Restore When Opening Documents"
date: 2007-08-16
forum: General Help
---

### Post by cb474 on 2007-08-16
I'm having a problem where when I close a document and reopen it in OpenOffice Writer, it always returns to the beginning of the document. In Windows, OpenOffice returns to the last position of the cursor, so on files that I'm frequently editing documents just open up to where I left off.

I'm using OOo 2.2.0, as provided with Feisty.

I posted over on the OOo forums and was told that OpenOffice is supposed to open to the last cursor position, called cursor position restore (or something like that). Also, hitting Shift+F5 should return you to the last cursor position. Over there someone thought I should try downloading OOo straight from the OpenOffice site.

So I uninstalled the Ubuntu version of OOo 2.2.0 that came with Feisty and installed OOo 2.2.1 directly from the package on the OpenOffice site. This did not fix the problem (though again someone on the OOo forum said cursor restore was working for them with 2.2.1 in Fedora).

I've gone back to the Feisty 2.2.0 version of OOo. Is there any way to get cursor restore working?

---

### Post by Total_Biscuit on 2007-08-17
Well, the OOo help says
> **Cursor Position**
In general, all documents open with the cursor at the start of the document. 
One exception appears when the author of a Writer text document saves and reopens a document: the cursor will be at the same position where it has been when the document was saved. This only works when the author has entered his name in Tools - Options - OpenOffice.org - User Data.
Press Shift+F5 to set the cursor to the last saved position.
and that's how it works for me.

---

### Post by cb474 on 2007-08-18
Yes, that's how it's supposed to work. But apparently there have been bugs in different versions and it hasn't always worked for people. It turns out that my problem is it doesn't work with .doc files only with .odt files (although I could swear it used to work for me in earlier versions of OOo).

---

