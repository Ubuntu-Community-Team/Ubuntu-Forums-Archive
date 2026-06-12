---
title: "Libreoffice saving doc location  (Ubuntu 18.04)"
date: 2019-12-07
forum: General Help
---

### Post by Robbyx on 2019-12-07
I used to see a lot of favourite folders when saving a file in Libreoffice..  I can still see them in nautilus and pcmanfm. All the drag and dropped locations no longer show in LO.  Does anyone know how to restore them? 

If they can not be restored how do I create new favourite folders to show up in the save as dialogue?

---

### Post by CatKiller on 2019-12-07
If you've installed it as a snap it will be restricted in where it can read from or write to.

---

### Post by Robbyx on 2019-12-07
Does that mean that all my favourite saving locations will not appear when saving a file?

If that is the case, how do I reinstall so that it does not get taken up by snap?

---

### Post by deadflowr on 2019-12-07
Use snap commands to remove libreoffice then use apt commands to install libreoffice.
```
snap remove libreoffice
sudo apt install libreoffice
```

---

### Post by Dennis N on 2019-12-07
> **Robbyx said:**
> Does that mean that all my favourite saving locations will not appear when saving a file?

Where are these favorite saving locations that you can't access? In snaps, you might be restricted to your home folder. 
I haven't used a LibreOffice snap, but you can work around such a restriction by saving your work to ~/Documents, then copying the file(s) to another location if necessary with the file manager.

---

### Post by Robbyx on 2019-12-07
> **deadflowr said:**
> Use snap commands to remove libreoffice then use apt commands to install libreoffice.
```
snap remove libreoffice
sudo apt install libreoffice
```

 I followed your advice but I did not get very far. What do you suggest I do next?

```
snap remove libreoffice
snap "libreoffice" is not installed

```

---

### Post by Robbyx on 2019-12-07
I think I have been misleading myself. I am not asking about favourites. The directories that are not showing in  save  are called bookmarks. These directories I can save to,  but it is tedious because they are not in the home directory. I prefer to click on a  bookmark and save the file.

---

### Post by Robbyx on 2019-12-09
Does any one know how to ensure that bookmarks are showing in the file  save as option? They appear in filemanagers but not when saving via libreoffice. They used to show but a recent upgrade has cause them to no longer appear.

---

### Post by ajgreeny on 2019-12-09
As long as Libreoffice can see those folders you want to use if you manually use the save dialogue to put the files there you may be able to add those folders in LO's settings.

Go to ***Tools -> Options -> Libreoffice ->Paths*** and edit the line in that for My Documents.

I've never tried this so I don't know if it works but it may give a clue as to where to try making the changes you want to the current default pathways.

---

### Post by Dennis N on 2019-12-09
Have you tried creating a bookmark for your folder from the file-chooser dialog while saving? See attached image.

---

### Post by Robbyx on 2019-12-11
> **ajgreeny said:**
> As long as Libreoffice can see those folders you want to use if you manually use the save dialogue to put the files there you may be able to add those folders in LO's settings.

Go to ***Tools -> Options -> Libreoffice ->Paths*** and edit the line in that for My Documents.

I've never tried this so I don't know if it works but it may give a clue as to where to try making the changes you want to the current default pathways.

Your suggestion makes life a lot easier for me. Thank you. It does not allow me to see the bookmarks created  with nautilus and pcmanfm. In the past they appeared automatically in the save as option.

---

### Post by Robbyx on 2019-12-11
> **Dennis N said:**
> Have you tried creating a bookmark for your folder from the file-chooser dialog while saving? See attached image.

Those options do not appear in my version. I chose Save As, found the desired directory, Right clicked and the only option available was to rename.

---

### Post by #&amp;thj^% on 2019-12-11
EDIT: Sorry I just blew right by Dennis N's post without seeing it.
1.Open Tools > Options > LibreOffice > Paths;
    2.Click on "My Documents" in the panel on the right, then click Edit;
    3.Choose your personal default location for saving LibO files;
    Click OK, then click OK again to save the settings.

On my Ubuntu 18:04 setting, my "Save as...` dialogue, does include my own system bookmarks, etc.
Is LO installed as a snap?

---

### Post by Robbyx on 2019-12-11
Yes, I think so, I am having antother conversation in this forum about the problems I had removing snap. Removing snap also  took out my settings, and sound!

---

