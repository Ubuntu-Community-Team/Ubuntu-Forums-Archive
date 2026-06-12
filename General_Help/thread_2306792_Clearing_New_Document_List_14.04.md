---
title: "Clearing New Document List 14.04"
date: 2015-12-18
forum: General Help
---

### Post by stoney4 on 2015-12-18
Hi,

Whenever I right-click on the screen and open a new document, I get a mile-long list that I can't figure out how to clear.

Any help appreciated.

---

### Post by Geoffrey_Arndt on 2015-12-19
Perhaps it would help (so we understand) . . . what exactly are you trying to do?   Create a new document in a text editor (like gedit), or create a new document in the standard program "LibreOffice - Writer"???   Or are you trying to edit a previously created document that now is shown (as a page icon) on the desktop?   And what do you mean by using the word "clear" . . . . . ???   Erase the content in the document, delete the document???

Generally, most Ubuntu users wouldn't right click on the desktop to make a new document (note I said "make", not open).   They would just open the actual word or text processing program first - - and use it to create the full document, save it to a specific folder in your home directory, and then just by clicking that document in the file manager - - it would be opened in the program that was used to create the document in the first place.   Am I missing something?

Take some time, gather your thoughts, and put together a clear paragraph or two about what you are actually trying to do.

---

### Post by vasa1 on 2015-12-19
And to add to what Geoffrey said, it's unlikely the list would be a mile long. Each program has a default number of "recently opened" files if that's what you really mean instead of "New Document".

---

### Post by grahammechanical on 2015-12-19
It is also useful to know what version of Ubuntu and what user interface you are using. There are different desktop environments and things change over time. Therefore advice needs to be modified accordingly.

In Ubuntu + Unity we can right click the background wallpaper and a small menu appears. It has options to create a new folder or a new document right on the desktop. The new document will be an empty text document file labelled Untitled Document.

Ubuntu does not use this right click menu to load existing documents because we can do that from the Dash files & folders lens>recent. Or Super + F.

---

### Post by stoney4 on 2015-12-19
Distro: TT 14.04.03
Env: Flashback Compiz

When I right-click on the desktop, then hover over the second selection in the context menu, which is "New Document," then a list appears to the right which currently has 18 entires. These are all Glabels documents. This is what I want to get rid of, thanks.

---

### Post by Frogs Hair on 2015-12-19
I don't get a recent items list in the desktop context menu so I'm a bit confused. Try the following to remove recent items.

```
echo > ~/.local/share/recently-used.xbel
```

---

### Post by deadflowr on 2015-12-19
The listings in that right click new documents setting should be in the Templates folder.

---

