---
title: "No create new file on right click"
date: 2018-10-17
forum: General Help
---

### Post by Vagelism_Meintasis on 2018-10-17
Hello to all, I tried to remove some metadate from files in one directory following some instructions from this forum post
[https://askubuntu.com/questions/308250/is-there-a-tool-for-removing-metadata#308257](https://askubuntu.com/questions/308250/is-there-a-tool-for-removing-metadata#308257)

so after I run the command

```
exiv2 rm /path/to/location/files
```

and after that I notice that I can not create new files, the option is not there when I right click on my desktop.
I can not also open with double click any folder. I have to open it from the file manager.

How can I undo what ever I did wrong ?

Thank you!

---

### Post by deadflowr on 2018-10-17
On Ubuntu 18.04 that's the default.
There is no right click create documents. But not all lost.
You can re-enable it by creating a blank file and put it in the Templates folder.
Then just give it name like New Document.
Once that file exists, right clicking will bring up the New Document option.
This command will create it simple enough
```
touch ~/Templates/New\ Document
```

Of course if on an older release such as Ubuntu 14.04 or Ubuntu 16.04, then yes you did something odd.
Are you on an older release?

---

### Post by Vagelism_Meintasis on 2018-10-17
> **deadflowr said:**
> On Ubuntu 18.04 that's the default.
There is no right click create documents. But not all lost.
You can re-enable it by creating a blank file and put it in the Templates folder.
Then just give it name like New Document.
Once that file exists, right clicking will bring up the New Document option.
This command will create it simple enough
```
touch ~/Templates/New\ Document
```

Of course if on an older release such as Ubuntu 14.04 or Ubuntu 16.04, then yes you did something odd.
Are you on an older release?

```
lsb_release -a
LSB Version:    core-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bioni
```

---

### Post by Vagelism_Meintasis on 2018-10-17
[B]deadflowr,
Your trick worked fine for making new empty documents, but when I make a new folder on Desktop, I can not double click them and get inside. Is this odd or not? Thank you![/B]

---

### Post by deadflowr on 2018-10-17
[s]Right click to properties and see what the Open With shows.
See if you can set it to open with gedit or Text editor by default.
It might've been reset to try and open with something else.[/s]

Edit: Scratch that. Misread about the folder creation. oops.
Hmm, that's odd.
Let's think about that for a moment.

Edit again: similar to this issue:
[https://askubuntu.com/questions/984153/cant-open-desktop-folders-by-double-clicking-on-ubuntu-17-10]("https://askubuntu.com/questions/984153/cant-open-desktop-folders-by-double-clicking-on-ubuntu-17-10")

---

### Post by Vagelism_Meintasis on 2018-10-17
Right click and open is not working at all, right click and open with other applications lets me select the files, and then opens it!

---

### Post by deadflowr on 2018-10-17
We're probably crossing paths here.
But to open documents, right click on it and go down to properties.
In Properties go to the Open With section.
Scroll down the available apps until you get to Text Editor, then highlight that and click on the set as default at the bottom.

---

### Post by Vagelism_Meintasis on 2018-10-17
Documents work great... no more issues. Folders, No. I did what ever I found on the post you send me. Nothing worked.

---

### Post by Vagelism_Meintasis on 2018-10-17
> **deadflowr said:**
> [s]Right click to properties and see what the Open With shows.
See if you can set it to open with gedit or Text editor by default.
It might've been reset to try and open with something else.[/s]

Edit: Scratch that. Misread about the folder creation. oops.
Hmm, that's odd.
Let's think about that for a moment.

Edit again: similar to this issue:
[https://askubuntu.com/questions/984153/cant-open-desktop-folders-by-double-clicking-on-ubuntu-17-10](https://askubuntu.com/questions/984153/cant-open-desktop-folders-by-double-clicking-on-ubuntu-17-10)

Here what I find odd 

> sudo gnome-tweaks 
WARNING : Shell not installed or running
WARNING : Shell not running
NoneType: None
WARNING : Error loading desktopfile: /home/vagelis/.config/autostart/dropbox.desktop
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 216, in __init__
    raise Exception("Shell not running or DBus service no


---

### Post by Vagelism_Meintasis on 2018-10-17
With out running on sudo mode I have the following exception

gnome-tweaks 

(gnome-tweaks:6320): Gtk-WARNING **: 21:24:57.974: Attempting to read the recently used resources file at '/home/vagelis/.local/share/recently-used.xbel', but the parser failed: Failed to open file &#8220;/home/vagelis/.local/share/recently-used.xbel&#8221;: Permission denied.
WARNING : Error loading desktopfile: /home/vagelis/.config/autostart/dropbox.desktop

---

### Post by deadflowr on 2018-10-17
What does
```
echo $XDG_CURRENT_DESKTOP
```
show?

Also never need to sudo gnome-tweaks, fwiw.

---

### Post by Vagelism_Meintasis on 2018-10-18
> **deadflowr said:**
> What does
```
echo $XDG_CURRENT_DESKTOP
```
show?

Also never need to sudo gnome-tweaks, fwiw.



Thank you for the information! Here is the output you needed!
> vagelis@vagelis-desktop:~$ echo $XDG_CURRENT_DESKTOP
ubuntu:GNOME
vagelis@vagelis-desktop:~$ 




---

### Post by deadflowr on 2018-10-18
If the goal is to try and toggle the desktop icons on and off you can do that without gnome-tweaks.
You can install dconf editor, or run this
```
gsettings set org.gnome.desktop.background show-desktop-icons false
and
gsettings set org.gnome.desktop.background show-desktop-icons true
```
false turns it off and true turns it on.
```
gsettings get org.gnome.desktop.background show-desktop-icons
```
will show current setting.

though truth be told I think the better answer would be to try that answer also found here:
[https://askubuntu.com/questions/235660/how-do-i-change-the-default-file-manager-back-to-nautilus/288136#288136]("https://askubuntu.com/questions/235660/how-do-i-change-the-default-file-manager-back-to-nautilus/288136#288136")

---

### Post by Vagelism_Meintasis on 2018-10-18
No, the objective is to be able to double click a folder on Desktop and open it!

---

### Post by Vagelism_Meintasis on 2018-10-18
The solution on the forum is not working!

---

### Post by deadflowr on 2018-10-18
> **Vagelism_Meintasis said:**
> No, the objective is to be able to double click a folder on Desktop and open it!

No , I meant the need for gnome-tweaks, not the overall objective.
I get that part.

Can you open Files (the program) from Activities up top (or from the dash, the launcher panel on the left side)?
((You can just click on Activities name up top and then type files and it will run a search for Files, it'll then list it and then you can click on that to open it))
And then try moving around various folders and see what happens. (do they open or not open when you try open different folders...)

---

### Post by Vagelism_Meintasis on 2018-10-18
Yes , the program opens and works great, I manage to open the folders only from this. But when I double click them. They do no to anything. Also right click open with....doesnot work.

---

