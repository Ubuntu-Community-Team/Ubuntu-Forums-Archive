---
title: "Installing a Recycle bin?"
date: 2006-10-26
forum: General Help
---

### Post by paul6 on 2006-10-26
I did a server install of Ubuntu and I am using OpenBox and Pypanel as my GUI. My question is, when I delete something inside Nautilus, does it go to a trash can somewhere? Or do I need to install something to add that functionality?

---

### Post by IYY on 2006-10-26
Yes, there is a trash at **~/.Trash** (a hidden subdirectory in your home directory). There is a menu in Nautilus that lists a bunch of locations on your system, and Trash should be one of them.

---

### Post by Seq on 2006-10-26
In Nautilus, the default is 'Move to Trash", which is ~/.Trash. Deleting files on other devices (Removable Hard Disks, etc) creates a new directory there, something like .Trash-$USER .

Nautilus is capable of drawing a Trash on the Desktop (Assuming you have nautilus drawing the desktop) by setting the following gconf key:

```
gconftool-2 --set /apps/nautilus/desktop/trash_icon_visible -t bool true
```

This is not the default as there is a trash applet in the gnome panel... Unless you're not running gnome... :)

---

### Post by woedend on 2006-10-26
click view -> show hidden files.  its in your home directory as .Trash.  There is an option under file to empty it.

---

### Post by Seq on 2006-10-26
also, pressing CTRL+L to get a address bar, go to the following address:

```
trash:
```

That will show you all trash items, whether they are on removable media or your local drive.

---

### Post by Eli101 on 2008-07-05
> **woedend said:**
> click view -> show hidden files.  its in your home directory as .Trash.  There is an option under file to empty it.
Hey,
Hope your okay.
I was looking how to re-install the recycle bin, and I saw your reply. but i still dont reall understand how to. 
Please could you help me??

---

### Post by paul101 on 2008-07-05
i can see the cobwebs on this thread


the trash can should be a small icon at the bottom right of your screen


if not, right click the bottom taskbar and click **Add to Panel**


then find the trash can :)

---

### Post by lukjad on 2008-07-05
Also, if you have difficulty emptying the trash bin this command will get the job done. Go to the terminal and type:```
sudo rm -r ~/.local/share/Trash/files/

```
Hope this helps.

---

