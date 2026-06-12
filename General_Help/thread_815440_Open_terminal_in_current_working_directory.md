---
title: "Open terminal in current working directory"
date: 2008-06-01
forum: General Help
---

### Post by terrordrone on 2008-06-01
Hi

Im running ubuntu gutsy

ive installed nautilus-open-terminal which opens terminal in current directory. But i need to use the mouse for this.

how do i make it do the same thing by pressing a key, like say 'f4' as in kubuntu.

I am missing this a lot.

Please do give instructions in detail as im a bit new to linux :)

Thanks

---

### Post by mike2357 on 2008-06-01
System -> Preferences -> Keyboard Shortcuts

In the Desktop section, the last item is "Run a terminal".  You can set the shortcut to whatever you like.

---

### Post by terrordrone on 2008-06-01
> **mike2357 said:**
> System -> Preferences -> Keyboard Shortcuts

In the Desktop section, the last item is "Run a terminal".  You can set the shortcut to whatever you like.
thanks for the reply

i did what u said

it only opened the terminal in my home directory...

i want it to open in the directory of the window in focus

---

### Post by mike2357 on 2008-06-01
Sorry, you said that on your first post, but I missed it.  Unfortunately, I don't know how to get a terminal window to open anywhere but in your home directory.  Maybe someone else will.

---

### Post by terrordrone on 2008-06-01
> **mike2357 said:**
> Sorry, you said that on your first post, but I missed it.  Unfortunately, I don't know how to get a terminal window to open anywhere but in your home directory.  Maybe someone else will.
Maybe i should start bumping...
otherwise this threadll wont be seen :(

---

### Post by viciouslime on 2008-06-01
I don't think this functionality is built into gnome, it is in kde. You might like to look into something called nautilus scripts. I haven't used them for a long time, but if you google for it you should be able to find a way to get it to work :) I know that's not a great answer, but I really haven't used them for ages and can't remember exactly how they work.

---

### Post by terrordrone on 2008-06-02
> **viciouslime said:**
> I don't think this functionality is built into gnome, it is in kde. You might like to look into something called nautilus scripts. I haven't used them for a long time, but if you google for it you should be able to find a way to get it to work :) I know that's not a great answer, but I really haven't used them for ages and can't remember exactly how they work.
I have NScripts.. but how do i map f4 to run that?

---

### Post by vanadium on 2008-06-02
When in nautilus a folder is selected, "ett<enter>" will open a terminal. Alternatively: <Shift+F10>tt<enter>

For the current folder to open: <Alt+f>t

In theory, the "editable menu shortcut keys" feature should be able to help: System - Preferences - Appearance, Interface tab. Check "Editable menu shortcut keys". However, this does not seem to work for the "File - Open in terminal" command which is a plugin.

---

### Post by terrordrone on 2008-06-03
> **vanadium said:**
> When in nautilus a folder is selected, "ett<enter>" will open a terminal. Alternatively: <Shift+F10>tt<enter>

For the current folder to open: <Alt+f>t

In theory, the "editable menu shortcut keys" feature should be able to help: System - Preferences - Appearance, Interface tab. Check "Editable menu shortcut keys". However, this does not seem to work for the "File - Open in terminal" command which is a plugin.
1) "ett<enter>" will open a terminal. Alternatively: <Shift+F10>tt<enter>
 can u explain this .. i didnt get it.. :|

2) how do i make it to open for f4 instead of <alt+f>t

---

### Post by bedek on 2010-12-20
This one work for me:

[http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/](http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/)

If link is broken here is content:
step 1
$ gedit "$HOME/.gnome2/nautilus-scripts/Open Terminal Here"
step 2
paste this content:
[COLOR=#808080]*#!/bin/bash*[/COLOR]
[COLOR=#808080]*# From Chris Picton*[/COLOR]
[COLOR=#808080]*# Replaces a Script by Martin Enlund*[/COLOR]
[COLOR=#808080]*# Modified to work with spaces [COLOR=#000000]**in**[/COLOR] path by Christophe Combelles*[/COLOR]
 
[COLOR=#808080]*# This script either opens [COLOR=#000000]**in**[/COLOR] the current directory,*[/COLOR]
[COLOR=#808080]*# or [COLOR=#000000]**in**[/COLOR] the selected directory*[/COLOR]
 
[COLOR=#007800]base=[/COLOR][COLOR=#FF0000]"`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"[/COLOR]
[COLOR=#000000]**if**[/COLOR] [COLOR=#7A0874]**[**[/COLOR] -z [COLOR=#FF0000]"$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"[/COLOR] [COLOR=#7A0874]**]**[/COLOR]; [COLOR=#000000]**then**[/COLOR]
     [COLOR=#007800]dir=[/COLOR][COLOR=#FF0000]"$base"[/COLOR]
[COLOR=#000000]**else**[/COLOR]
     [COLOR=#000000]**while**[/COLOR] [COLOR=#7A0874]**[**[/COLOR] ! -z [COLOR=#FF0000]"$1"[/COLOR] -a ! -d [COLOR=#FF0000]"$base/$1"[/COLOR] [COLOR=#7A0874]**]**[/COLOR]; [COLOR=#000000]**do**[/COLOR] [COLOR=#7A0874]**shift**[/COLOR]; [COLOR=#000000]**done**[/COLOR]
     [COLOR=#007800]dir=[/COLOR][COLOR=#FF0000]"$base/$1"[/COLOR]
[COLOR=#000000]**fi**[/COLOR]
 
step 3
run command:
$ chmod +x "$HOME/.gnome2/nautilus-scripts/Open Terminal Here"

step 4
use it:
And you are done. Open nautilus file manager, select directory > Right Click > Scripts > Open Terminal Here:
gnome-terminal --working-[COLOR=#007800]directory=[/COLOR][COLOR=#FF0000]"$dir"[/COLOR]

---

### Post by tep200377 on 2011-04-20
Thansk bedek ;) It worked great for me ;)

---

### Post by TranceWarp on 2011-04-23
Thanks!  This worked for me as well, but for some reason, I had to replace $ with sudo in the terminal commands. :confused:

---

