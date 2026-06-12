---
title: "How to reset the gnome menu?"
date: 2007-04-28
forum: General Help
---

### Post by Bou on 2007-04-28
Hi, I seem to be having some problems with apps that I uninstalled but still appear in my menu, and others that don't even though they are installed. How can I reset my menu to make it detect what it must show and what it mustn't?

Thanks in advance.

---

### Post by mskadu on 2007-04-28
I am not sure if this is the silver bullet, but have you tried the "Reset" button on the menu editor (right click on the Ubuntu Icon)

---

### Post by Bou on 2007-04-29
Yes, I tried but it didn't work.

Where are those settings stored? Is there a folder/file that I can remove to get the menu reset?

---

### Post by mskadu on 2007-04-29
Well, I am not sure what you mean then. The "reset" button simply sets the menu items to their default. visibility. If you are looking for it to remove invalid items then I am not sure how thats done.

---

### Post by engla on 2007-04-29
There are some things in ~/.config/ and some in ~/.local/share/ that are realated to the main menu. I don't know the proper way though, but you could try that..

---

### Post by rykel on 2007-11-14
Hi,

I am also having a problem with the GNOME Menu...

Basically I accidentally dragged the "Sound & Video" menu back to itself and now I have the items in that menu appearing in the "Others" menu, and when I tried to recreate the "Sound & Video" menu, the icon is just a simple folder...

Is there a way to rearrange the menus back to how a fresh Ubuntu install would have it, and restore the icons too?

I tried to "Revert" the menu, bad... it changed my manually created "Sound & Video" menu into "alacarte-made-1" menu, and the icon still has NOT changed back...   :confused:

Thanks!

UPDATE: Sorry pals, I think I did something right... anyway, I did "reinstall" GNOME Menu and "libgnome-menu" from Synaptic, and tried once more to "Revert" the menu inside Edit Menu dialog box, and it returned the "Sound & Video" menu with the correct icon back to me... I only had to drag the relevant programs back into their original positions and delete their presence in the "Others" menu. Hope that helps... lots of repetitive descriptions!!    LOL

---

