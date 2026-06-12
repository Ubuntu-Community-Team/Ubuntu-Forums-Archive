---
title: "How do I reset the gnome shell panel?"
date: 2013-12-05
forum: General Help
---

### Post by BlackoutWorm on 2013-12-05
Hello. I installed an extension to change gnome shell panel settings.
This extension removed the panel.
How do I get it back **without an extension**?
No matter what I google related to gnome-shell, there's always just links to extensions rather than actual guides.
Most of the extensions don't even work or they end up freezing gnome-shell.
The extension idea might seem handy and user-friendly on the surface, but at the end of the day it means more geek work and knowledge required.
Anyway. Do you know how to reset the gnome shell panel or where I can edit its settings?

---

### Post by monkeybrain20122 on 2013-12-05
Can you just open gnome-tweak-tool, go to Shell Extensions and remove the addon? You may need to logout and log in again. Of course you have to install the gnome-tweak-tool first, it is in the repo.

---

### Post by deadflowr on 2013-12-05
Go to [gnome extensions]("https://extensions.gnome.org/") and turn it off.

Look in Installed extensions.

+1 for tweak-tool, though.

---

### Post by BlackoutWorm on 2013-12-05
I've tried all that stuff.
I tried to disable the extension and delete the settings.xml file.

---

### Post by deadflowr on 2013-12-05
> **BlackoutWorm said:**
> I've tried all that stuff.
I tried to disable the extension and delete the settings.xml file.

What .xml file?

The extensions should be in ~/.local/share/gnome-shell.
But I haven't seen any xml files, just .json,.js, and .css files.(And probably others)

---

### Post by BlackoutWorm on 2013-12-05
Sorry, not xml. I mean settings.json.
Anyway I've tried to remove extensions one by one and even the whole folder.
So where are the actual panel settings?

---

### Post by deadflowr on 2013-12-05
Beats me about where all the panel settings might be, but the folder
/usr/share/gnome-shell
is where all the gnome-shell settings are.
I know it contains all the default settings of the shell, including, I would venture to guess, the panel.

You could always purge gnome-shell and remove the .local/share folder, then run
```
sudo apt-get clean && sudo apt-get update
```
then reinstall the shell, and see if it installs correctly.
But that's only something to think about.

---

### Post by BlackoutWorm on 2013-12-05
Thank you so much. That solved my problem

---

