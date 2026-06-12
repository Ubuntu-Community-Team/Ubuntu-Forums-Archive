---
title: "Deleted files still on USB"
date: 2006-12-14
forum: General Help
---

### Post by drito on 2006-12-14
When I delete files from USB, they go to hidden folder Trash, still on USB. It happens with all USB disks. How to stop this?

---

### Post by rpkehoe on 2006-12-14
They may be already gone, I have found that when I use a memory card it does refresh unless I specifically tell it to.  Try right clicking on the usb drive and hit 'safely remove' and then reattach the usb drive and see if the files are still present.

---

### Post by Lord Illidan on 2006-12-14
Try this link:

[http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/](http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/)

> They may be already gone, I have found that when I use a memory card it does refresh unless I specifically tell it to. Try right clicking on the usb drive and hit 'safely remove' and then reattach the usb drive and see if the files are still present.

His problem doesn't have anything to do with that. When you are using a usb disk and delete something from it, it goes to a hidden directory .Trash on the disk...which means that it is never actually deleted.

---

### Post by mysticrider92 on 2006-12-14
After you delete something, stay in nautilus (or whatever file manager you are using) and click on the tab that says 'view' and select 'show hidden files' then delete the folder named trash and it will be permanent. I don't know how to stop it from putting things in a trash folder, I think that is just part of Ubuntu.

---

### Post by drito on 2006-12-14
Lord Illidan have right, rpkehoe. I used his link, and read a post, which describes how to solve this problem with Nautilus. However, I use Konqueror as a file manager. For Konqueror, one should go to Settings/Configure Konqueror/Behavior and mark Show "Delete"... Thank you both for help. I have just switched from Windows and this community support is amazing!!!

---

### Post by Lord Illidan on 2006-12-14
> **drito said:**
> Lord Illidan have right, rpkehoe. I used his link, and read a post, which describes how to solve this problem with Nautilus. However, I use Konqueror as a file manager. For Konqueror, one should go to Settings/Configure Konqueror/Behavior and mark Show "Delete"... Thank you both for help. I have just switched from Windows and this community support is amazing!!!

We do our best...then it is your turn to contribute. ;)

---

### Post by yabbadabbadont on 2006-12-14
There is an opton for Nautilus to add a delete option that bypasses the trash.  I don't remember if you can get to it from the settings in Nautilus itself, or if you have to edit the Nautilus settings using gconf-editor.

---

### Post by bodhi.zazen on 2006-12-14
Hmmm ....

Yet another advantage of the CLI :p

---

### Post by mcduck on 2006-12-14
it seems that all OSes leave some hidden files on disks.. Windows likes to put it's thumbs.db files to every possible directory, OSX leaves hidden backup files and Linux leaves hidden trash files..

Couple of weeks ago I was doing a web project with people using win and mac, and I had my Ubuntu. After moving files between machines for a while the thumb drive we used was so full of all kinds of funny files that it became hard for me to find the actual files. :D

At least Ubuntu puts all those files inside one hidden directory so that they are easy to remove. :rolleyes:

---

### Post by magnastiks on 2007-01-25
Just adding this for someone searching for help:

[http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/]("http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/")


The above link mentions the option to include permenant delete as well as trash-can functionality to nautilus.

Creating a hidden .trash is a bad and confusing feature for USB-drives.  Even trying to delete something from the Trash Bin through gnome doesn't work correctly with flash drives.

---

### Post by dannyboy79 on 2007-01-25
yeah, I have noticed that I deleted something from my network attached xbox and it put it inside my .trash folder and now when I try to remove it it gives me an error saying I can't delete the file. do you know what's up with  this???

---

### Post by agustin.g on 2007-01-26
try doing ```
sudo rm /path/to/file.extension
```

When deleting just use Shift+Delete and it will bypass the trashcan and really delete the file.

---

### Post by dannyboy79 on 2007-01-26
i'll try this but I am sure it's going to say that this file doesn't exist as it doesn't. the file is located in the .trash. Maybe I should make sure the xbox is remounted and then try what you're saying. thanks for the suggestion.

---

### Post by shareMenaPeace on 2007-01-28
> **mysticrider92 said:**
> After you delete something, stay in nautilus (or whatever file manager you are using) and click on the tab that says 'view' and select 'show hidden files' then delete the folder named trash and it will be permanent. I don't know how to stop it from putting things in a trash folder, I think that is just part of Ubuntu.
Thx

---

### Post by MkfIbK7a on 2007-01-28
this problem has to do with notm mounting the usb drive correctly try rightclicking and unmount 

then go to properties some tab i dont remeber and check 
mount automatically

---

### Post by brianC on 2007-01-28
Try
   Places
   Home Folder
   Edit
   Preferences
   Behaviour
   At the bottom check the " Include Delete command that bypasses Trash"
This will add the command delete to all folder (and drive) edit menus

---

