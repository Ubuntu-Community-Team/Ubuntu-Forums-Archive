---
title: "Unrar problem"
date: 2007-08-27
forum: General Help
---

### Post by Sikarian on 2007-08-27
I've got a whole folder full of .rar and .zip files, a couple hundred of them I need to unrar all at once.  I can highlight them all in Nautilus, right click and Extract here.  That works, except that instead of taking the folder inside of it and just placing it in the same directory, it puts it in a redundant directory.  

Example,  "files1.rar" with a folder inside called "lolfiles".  When I extract it, it creates a lolfiles_FILES directory, and then inside of that is the folder.

Is there anyway I can mass unrar these, and have them just take the "lolfiles" directory out and place it in the main directory?  

Or if that is not possible, can I somehow get a script to take every _FILES directory, pull the folder out and up one level, and then delete the _FILES directory?

---

### Post by apetresc on 2007-08-27
I'm not sure about changing Nautilus' behaviour the way you want (I don't use Gnome), but I can definitely give you a single command to take everything out of each of the _FILES directories and move them to the parent: ```
mv *_FILES/* .
```
Make sure you write that out exactly as I wrote it, including the "." at the end. :) Tested and works!

Obviously, you should run this command in the directory containing the various SOMETHING_FILES directories.

Enjoy, and good luck!

---

### Post by srunni on 2007-08-27
Try opening a terminal, cd'ing to the directory with all the archives and typing ```
unrar e *.rar
``` and ```
unrar e *.zip
``` I don't use GNOME either, so I don't know how to change Nautilus's behavior either. :(

---

### Post by Sikarian on 2007-08-27
> **AdrianP said:**
> I'm not sure about changing Nautilus' behaviour the way you want (I don't use Gnome), but I can definitely give you a single command to take everything out of each of the _FILES directories and move them to the parent: ```
mv *_FILES/* .
```
Make sure you write that out exactly as I wrote it, including the "." at the end. :) Tested and works!

Obviously, you should run this command in the directory containing the various SOMETHING_FILES directories.

Enjoy, and good luck!


Man, that worked fantastically.  Thanks!

---

