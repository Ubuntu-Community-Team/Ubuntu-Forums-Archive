---
title: "Redirect folders"
date: 2015-03-02
forum: General Help
---

### Post by SteinarSS on 2015-03-02
I have been going back and forth between different distros on different partitions on my computer, and all my files (documents, pictures etc.) are on one partition. I would like the folders that comes up when I click on the File Manager in the lanucher (the one to the left) in Unity to be shortcuts to the corresponding folders on the shared partiton rather than normal folders. Is this possible to do?

---

### Post by egeezer on 2015-03-02
To access a partition's contents it needs to be mounted, so if you open two instances of Nautilus you will be able to go from one distros files to the other with ease.  However, I don't know if the Unity desktop permits that; you might have to install another desktop (I usually install Ubuntu, then add Xfce and work in that desktop)

---

### Post by deadflowr on 2015-03-02
Do you know the path to the folder?
If so I would copy the file manager's desktop file from /usr/share/applications into my home folders .local/share/applications folder and edit it.
```
cp /usr/share/applications/nautilus.desktop .local/share/applications
```
then open gedit and edit the exec line:
(You need to open a text editor first to edit, double clicking will only try to launch the application the file is for.)

Typical exec line is
```
Exec=nautilus --new-window %U
```
I would change it to something like
```
Exec=nautilus --new-window Pictures
```
(Or if you are concerned make it the full path ; /home/user/Pictures)
from now on, when i launch the file manager, it'll open directly in my pictures folder.
(You can test run the commands from a terminal to see how they will work)
then save the file.
Now unlock the files from the launcher, and open the dash and search for Files --the program name.
It is possible that two Files might show, I really do not know what to do about that.
Now click on one and launch it.
Does it open in the newly set default window or still in the old one?

I hope some of this makes sense or is helpful or even close to the idea you are thinking of.


Oh, I forgot, have you set the data partition to mount on start up, or do you just mount it when you open the file manager?
I guess that might be important...

---

### Post by SteinarSS on 2015-03-17
Thank you for the reply. I am sorry to say that this goes way over my head, so I think I'll just leave everyting as it is... Sorry for the bother!

---

### Post by Keith_Helms on 2015-03-17
I have a script that does pretty much what you're asking about.  I delete the standard names and use my own names for the home directories (mostly because I like all lower-case names), but there's no reason you couldn't use the standard names.  I have a laptop with 3 boot partitions and currently have Xubuntu 14.04, Ubuntu 14.04, and Mint 17.1 installed.  I have another partition which I mount under the name homedata and that is where all the shared stuff goes.

Here's the script.  You're welcome to make use of it, make fun of it, whatever.  To use the standard names, just change the DIR_NAME value above each call to set_homedirs_softlink.  Do a global change of homedata to whatever name you have your shared partition mounted under. If you have any files under any of the standard directories, the remove command "rmdir" will fail.   It will only work on an empty directory.



```

#/bin/bash

remove_dir () {
if [ -e "$HOME/$DIR" ]
then
    echo "Removing $HOME/$DIR"
    rmdir $HOME/$DIR
else
    echo "$HOME/$DIR does not exist"
fi
}

set_homedirs_softlink () {
echo "creating link for $DIR"
if [ ! -e "/homedata" ]
then
    echo "/homedata does not exist!"
    return
fi
if [ ! -e "/homedata" ]
then
    mkdir "/homedata"
fi
if [ ! -e "$HOME/$DIR" ]
then
    if [ ! -e "/homedata/$DIR" ]
    then
        mkdir "/homedata/$DIR"
    fi
    ln -s "/homedata/$DIR" "$HOME/$DIR"
fi
}

set_softlink () {
echo "creating link for $DIR"
if [ ! -e "/homedata" ]
then
    echo "/homedata does not exist!"
    return
fi
if [ ! -e "$HOME/$DIR" ]
then
    if [ ! -e "/homedata/$DIR" ]
    then
        mkdir "/homedata/$DIR"
    fi
    ln -s "/homedata/$DIR" "$HOME/$DIR"
fi
}


DIR="Documents"
remove_dir
DIR="Downloads"
remove_dir
DIR="Music"
remove_dir
DIR="Pictures"
remove_dir
DIR="Public"
remove_dir
DIR="Templates"
remove_dir
DIR="Videos"
remove_dir

DIR="bin"
set_homedirs_softlink
DIR="data"
set_homedirs_softlink
DIR="documents"
set_homedirs_softlink
DIR="dosdrive"
set_homedirs_softlink
DIR="download"
set_homedirs_softlink
DIR="jars"
set_homedirs_softlink
DIR="workspace"
set_homedirs_softlink
DIR="Podcasts"
set_softlink
DIR="video"
set_softlink

exit

```

---

### Post by Holger_Gehrke on 2015-03-18
> **SteinarSS said:**
> I would like the folders that comes up when I click on the File Manager in the launcher (the one to the left) in Unity to be shortcuts to the corresponding folders on the shared partition rather than normal folders. Is this possible to do?

Do you mean the folders in the sidebar on the left in the filemanager ? Those are just bookmarks, you can change them or add to them by choosing 'Bookmarks' > 'Edit Bookmarks' from the menu.

If you want to actually replace the folders with symbolic links, it gets a bit more complicated. You can create links by dragging the folders from your shared partition to the home directory and holding the key "alt" before and during releasing the mouse button (if you hold "alt" at the beginning of dragging, you will drag the window - not quite what you want ...). On release you'll get a menu with the option to create a link to the directory. You'll need to remove the directories you want to replace before you create the links and you'll have to make sure the partition gets mounted automatically, otherwise you'll have dead links in your file manager until you mount the partition.

---

