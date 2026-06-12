---
title: "Cannot move themes to appropriate folder"
date: 2012-11-20
forum: General Help
---

### Post by Deucalion29710 on 2012-11-20
When I try to move a theme folder from my downloads folder to my usr/share/themes folder it will not drop it there. Using drag and drop method it appears that the folder bounces right back out. What am I missing?

---

### Post by vasa1 on 2012-11-20
The destination isn't "yours". It belongs to the system. To make changes to system files and folders, including copying stuff to a system folder --- /usr is a system folder --- one needs to use sudo (in a terminal) or gksudo (or gksu) when using a GUI (file manager).

---

### Post by Deucalion29710 on 2012-11-20
so what would be the exact sudo string that I need in terminal to unlock permissions on usr/share/themes and usr/share/icons?

---

### Post by dannyboy79 on 2012-11-20
it's not a matter off unlocking those folder locations, you should leave them owned by root. You can do it 1 of 2 ways, either move it from your Downloads folder with sudo from a command line terminal session or invoke your file manager (nautilus) with gksudo.

```
sudo mv /home/user/Downloads/theme /usr/share/themes/
```

OR

```
gksudo nautilus
```

****BE VERY CAREFUL WHEN USING NAUTILUS WITH GKSUDO AS IT'S EASY TO ACCIDENTALLY DELETE A FOLDER OR FILE WHICH CAN HOSE YOUR INSTALL****

After I am done with gksudo nautilus I always close it right away.

---

### Post by philinux on 2012-11-20
> **Deucalion29710 said:**
> so what would be the exact sudo string that I need in terminal to unlock permissions on usr/share/themes and usr/share/icons?

If this is only for your user just put them in ~/.themes in your home folder.

---

### Post by Impavidus on 2012-11-20
After moving make sure ownership of the directory is correct.```
sudo mv /home/username/Downloads/theme /usr/share/themes
sudo chown -R root:root /usr/share/themes
```or they will still be owned by the user. mv moves the directory, but changes nothing in the files inside. That will not work when there are multiple users on the system (and is ugly anyway).

---

### Post by Deucalion29710 on 2012-11-20
OK I tried this renaming the user name and theme of course in the string.  It keeps telling me that the theme itself in the downloads folder is an invalid directory.  What am I missing?

---

### Post by Rebelli0us on 2012-11-20
> **Deucalion29710 said:**
> OK I tried this renaming the user name and theme of course in the string.  It keeps telling me that the theme itself in the downloads folder is an invalid directory.  What am I missing?

You may think it's **your** computer and **your** files but in fact there is a guy named root that owns everything, and they never give out his phone number. So one way out is to keep your work on a Windows NTFS partition. Or like somebody posted above use "gksudo nautilus", that way the OS thinks you're root and lets you copy whatever you want.

---

### Post by dannyboy79 on 2012-11-20
> **Deucalion29710 said:**
> OK I tried this renaming the user name and theme of course in the string.  It keeps telling me that the theme itself in the downloads folder is an invalid directory.  What am I missing?
can you be more specific please? are you sure you're trying to move the correct foldername? You can use tab completion to complete a folder or filename when using the terminal. Just enter the first few letters and hit the tab button to complete the string. WOrks great for when filenames or folders have spaces.

Example: If I want to move a theme called "Beautiful Delight" from my Downloads folder I would issue the command
sudo mv /home/username/Downloads/Beau (and then hit tab, and it would finish the name of the folder for me putting in the backslash for the space and everything.)

---

### Post by dannyboy79 on 2012-11-20
> **Rebelli0us said:**
>  So one way out is to keep your work on a Windows NTFS partition. I don't see how that's relavent to writing files or folders to root owned locations at all. Not to mention who uses Winbloz anymore anyway. THis is an Ubuntu forum. LOL

---

### Post by Rebelli0us on 2012-11-20
> **dannyboy79 said:**
> I don't see how that's relavent to writing files or folders to root owned locations at all. Not to mention who uses Winbloz anymore anyway. THis is an Ubuntu forum. LOL

True, I still keep my stuff on NTFS partitions because I don't like getting insulting error messages like, "Only root can do that" or "access denied", etc.

---

### Post by Deucalion29710 on 2012-11-20
> **Rebelli0us said:**
> You may think it's **your** computer and **your** files but in fact there is a guy named root that owns everything, and they never give out his phone number. So one way out is to keep your work on a Windows NTFS partition. Or like somebody posted above use "gksudo nautilus", that way the OS thinks you're root and lets you copy whatever you want.

Never used gksudo nautilus.  Is this something I would install from Synaptic?

---

### Post by Rebelli0us on 2012-11-20
> **Deucalion29710 said:**
> Never used gksudo nautilus.  Is this something I would install from Synaptic?

No you don't need to install anything. Nautilus is the command to start the file manger. When you precede it with gksudo it starts with administrative privilege. that's all.

---

### Post by LewisTM on 2012-11-20
From the thread title, the user is running Xubuntu. Therefore the command should be 
```
gksudo thunar /usr/share/themes &
```

---

