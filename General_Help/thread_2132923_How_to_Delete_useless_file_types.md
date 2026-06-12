---
title: "How to Delete useless file types"
date: 2013-04-06
forum: General Help
---

### Post by Rebelli0us on 2013-04-06
When you access a machine on your network, Nautilus shows all  .*  text files in the home directory as **Type "unknown"**. So to open them you have to create a new file type for each one!   So now back working on the actual machine, it looks like these file types persist, so you have to teach Nautilus all over again how to open simple text files!

So I googled and found an applet "assogiate" a "File Types Editor".  In there you can find all the useless file types but you can't delete them because **only root can do that**!  And of course they never give you Root's phone number so you can call him and ask for a favor. Then, when you open "gksudo assogiate" the useless file types are not found! You can see them as a humble user but not as Root.

So how do you Delete the useless file types? And better still how do you prevent this problem in the first place?

---

### Post by Kirboosy on 2013-04-06
Couldn't you right click on the file and hit "Open with gedit" (or whatever you use as a notepad) Then make sure "Set Selected application as default action of this file type" box is checked.

Whenever you gksudo the program are you sure that the hidden files are still showing?

 Other than that I would have to do some research on it.

~Caboose

---

### Post by Rebelli0us on 2013-04-06
> **Caboose885 said:**
> Couldn't you right click on the file and hit "Open with gedit" (or whatever you use as a notepad) Then make sure "Set Selected application as default action of this file type" box is checked.

Whenever you gksudo the program are you sure that the hidden files are still showing?

 Other than that I would have to do some research on it.

~Caboose

Yes you can right-click and select app to open-with but you have to do it for **every** file. You can't get any work done that way.

"gksudo assogiate" **cannot** see the useless file types, I don't know if the settings reside in hidden files, conf-editor, d-conf or whatever.

---

### Post by Kirboosy on 2013-04-06
Do they have a reoccurring/common name?

You could write a script that goes to the drive and recursively deletes all the files that match the script criteria. 

~Caboose

---

### Post by Kirboosy on 2013-04-06
So here is what I mean by the previous post. The script is a script I created to cleanup junk files off of my SAMBA share. Windows and other programs like to create junk data files. I like everything on my drive clean.

```

#!/bin/sh
#Cleanup Data Folder
#Deletes "Thumbs.db thumbs.db AlbumArtSmall.jpg *.ini DS_Store files"
echo "Cleaning up Data Folder!"
sudo chmod -R 777 /Data/
find /Data/ -iname 'thumbs.db' -exec rm {} \;
find /Data/ -iname "album*.jpg" -exec rm {} \;
find /Data/ -iname "*.ini" -exec rm {} \;
find /Data/ -iname ".DS_Store" -exec rm {} \;
find /Data/ -iname "._.DS_store" -exec rm {} \;
```


Warning: Be extremely careful when playing with scripts that delete files. You could on accident delete important files!

---

### Post by Rebelli0us on 2013-04-06
> **Caboose885 said:**
> Do they have a reoccurring/common name?

You could write a script that goes to the drive and recursively deletes all the files that match the script criteria. 

~Caboose

They are **all** the text files in your home dir starting with . which makes each one a different file type.  So all of a sudden Linux doesn't know how to open "unknown" file types and prompts you for each to select a preferred app to open-with.  I don't want to delete the files in my home dir just the useless file-types that you are forced to create.

---

### Post by Kirboosy on 2013-04-08
Files starting with **.** are hidden files. You could change the file manager settings to not show hidden files. Are you sure that they are useless files and not system-created/needed files? Can I have an example name of the files?

 The script would only delete the files that **you** specify. You can control how much or how little the scripts delete.

---

### Post by Vaphell on 2013-04-08
.whatever (both files and directories) in your $HOME store configuration of your profile. Files right under $HOME relate to very basic things like terminal etc, directories on the other hand are used by fullblown programs. I wouldn't touch them if i were you. Don't press ctrl+h in your filebrowser (show/hide hidden files), problem solved ;)

---

