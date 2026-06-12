---
title: "I can't put any icon on Lubuntu 18.04 desktop"
date: 2019-07-22
forum: General Help
---

### Post by stilnovo1 on 2019-07-22
Hi to Everybody,

I can't put any icon on my desktop.

When I try to add an icon, it doesn't remain on the desktop.

The OS is Lubuntu 18.04.2 32 bit. 

It's an old notebook (a Fujitsu Amilo L7320).

In all my computers I exclusively use Lubuntu 18.04.2, but this is the only one where it happens this strange behaviour.

Thanks in advance for the help!

Andrea

---

### Post by stilnovo1 on 2019-07-25
Nobody can help me?

---

### Post by ajgreeny on 2019-07-25
What sort of icon; do you mean a launcher for an application, ie a (for example) **firefox.desktop** file?

Have you allowed the desktop to show anything at all in the settings?  
I can't remember the details of how to get to the settings in LXDE and I'm using Xubuntu at the moment so can't check the available options for you.

---

### Post by stilnovo1 on 2019-07-25
Thanks for your answers. Lubuntu normally allows the desktop shortcuts, infact on my other computers I have them full of shortcuts. In pcmanfm (the file manager) the desktop tab doesn't have the normal 'desktop' writing, but some strange symbols, meaning that there is something strange. Maybe it could be interesting to know how and where is defined the path for 'desktop'?

---

### Post by CatKiller on 2019-07-25
> **stilnovo1 said:**
> Maybe it could be interesting to know how and where is defined the path for 'desktop'?

~/.config/user-dirs.dirs

---

### Post by ajgreeny on 2019-07-25
And also show output of command ***ls -l Desktop*** to check ownership and permissions of Desktop; it may also, if the pathway is incorrect, just throw an error saying "File or folder not found"

---

### Post by stilnovo1 on 2019-07-26
> **CatKiller said:**
> ~/.config/user-dirs.dirs


```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/Scaricati"
XDG_TEMPLATES_DIR="$HOME/Modelli"
XDG_PUBLICSHARE_DIR="$HOME/Pubblici"
XDG_DOCUMENTS_DIR="$HOME/Documenti"
XDG_MUSIC_DIR="$HOME/Musica"
XDG_PICTURES_DIR="$HOME/Immagini"
XDG_VIDEOS_DIR="$HOME/Video"
```


This is the file...

> **ajgreeny said:**
> And also show output of command ***ls -l Desktop*** to check ownership and permissions of Desktop; it may also, if the pathway is incorrect, just throw an error saying "File or folder not found"

the  error message in the terminale is: impossible to access to Desktop (I've also tried 'desktop' and 'scrivania' - desktop in italian): invalid file or directory

Other strange thing: /home/ergaold/N

In pcmanfm this is be the path for 'desktop'...

---

### Post by deadflowr on 2019-07-26
Looks like you're missing the Desktop directory.
try creating it, and then add the name to the the XDG_DESKTOP_DIR= line in the 
~/.config/user-dirs.dirs file
```
"XDG_DESKTOP_DIR="$HOME/**Desktop**"
```
Probably use the Italian name since that's seems to be what your using, language-wise.

---

### Post by CatKiller on 2019-07-26
> **stilnovo1 said:**
> 
This is the file...

And as you can see it lists your Home folder as where references to your Desktop directory should point...

> **stilnovo1 said:**
> the  error message in the terminale is: impossible to access to Desktop (I've also tried 'desktop' and 'scrivania' - desktop in italian): invalid file or directory

...probably because at some point you've deleted your Desktop directory.

Part of the reason for using that XDG specification is to decouple the on-disc location of those important directories from the localised names of those directories. So, as an Italian user, you get to see your Desktop directory referred to as Scrivania (or whatever) but the developer never needs to learn how to speak Italian.

In principle you should be able to create a directory in your Home folder called Scrivania (or whatever you like, really) and adjust the XDG_DESKTOP_DIR entry to point to that directory (you might need to log out and log back in) and things should start working more properly.

---

### Post by stilnovo1 on 2019-07-26
I have modified the value in 'Scrivania' (desktop in italian) and... it works!! Thank you very much! How it could happen, it's a mystery anyway...

---

### Post by stilnovo1 on 2019-07-26
Is there a mode to upvote your solutions?

---

### Post by jeremy31 on 2019-07-26
No method to upvote here, only on askubuntu/stackexchange

---

### Post by stilnovo1 on 2019-07-27
Ok, thanks again!

---

