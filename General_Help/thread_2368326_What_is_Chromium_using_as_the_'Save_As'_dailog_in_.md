---
title: "What is Chromium using as the 'Save As' dailog in 16.04?"
date: 2017-08-09
forum: General Help
---

### Post by arsenic23 on 2017-08-09
I just switched from using Chromium in 12.04 to Chromium in 16.04 as my main browser.  I hate this 'save as' dialog.

[ATTACH=CONFIG]276324[/ATTACH]

Wasn't chromium using GTK in 12.04?  I honestly don't remember, it wasn't something that drew my attention.
Whatever is creating this dialog, and I hope it isn't Chrome itself, is terrible.

It doesn't alphabetize folder then files, and when I touch a file it causes the name of the file I'm saving to change.  I can't deal with this.

So, what is it, and how can I change it?

---

### Post by ajgreeny on 2017-08-09
Try using Settings -> Appearance from the menu icon top right (three vertically arranged dots) and click on **Use GTK+** if it is showing, instead of **Use Classic** to see if that makes any difference; it does not change much in my chromium, and does nothing to the save dialogue.

I do not have the problem you seem to have of the alphabetical arrangement of folders then files, nor the change of file name to be saved when I hover over a file in the chosen folder, however I have just noticed that by right clicking in the file listing pane you get several options that you can choose, including list folders before files.

---

### Post by vasa1 on 2017-08-09
I think Chromium now uses the GTK_3_ save as dialog window. What you saw in 12.04 was the GTK_2_ save as dialog window.

---

### Post by arsenic23 on 2017-08-09
> nor the change of file name to be saved when I hover over a file in the chosen folder
It's when I click on something.  So, I click on a file or folder to put the focus on the list windows, then I want to be able to take my hand off the mouse and use the keyboard to navigate.  Hit 'G' and to move to the first item with a 'G' in it and then use the arrow keys to move around to the correct entry.  Unfortunately, while I can still do this, the filename of the thing I am saving is changed to that first thing I clicked on.  This is my real problem; and yes, looking at some other software it seems that this is GTK3 and it is normal behavior.   Who thought this was a good idea?

I can live with folders not being sorted separately from files; but I keep saving things with the wrong filename, and that's extremely frustrating.

EDIT:  Forget clicking; if I don't use the mouse at all, just scrolling through the list items with the arrow keys changes the filename.
I can't find anyone talking about this.  How is it not infuriating everyone who uses GTK3 everywhere?

---

### Post by Dennis N on 2017-08-09
> It doesn't alphabetize folder then files, and when I touch a file it causes the name of the file I'm saving to change. I can't deal with this.

To fix file chooser (save/open file window), use dconf-editor, navigate to: **org > gtk > settings > file chooser** and set "sort directories first" to true. See attached screen shot from Lubuntu 17.04. Dialog appearance and how to set values varies somewhat between desktop envoronments - some have little switches, for example.

Many File Managers (Nautilus, Caja, Thunar) set this for the file manager window in their preferences.

---

### Post by arsenic23 on 2017-08-11
> **Dennis N said:**
> To fix file chooser (save/open file window), use dconf-editor, navigate to: **org > gtk > settings > file chooser** and set "sort directories first" to true. See attached screen shot from Lubuntu 17.04. Dialog appearance and how to set values varies somewhat between desktop envoronments - some have little switches, for example.

Thank you.  I got so wrapped up in completely reverting that I didn't even think to look into that.   That's very helpful.  Still, I wish I didn't have to be so careful when saving files from the Internet.  A single miss-click and I loose the correct filename and have to start again.

---

