---
title: "How to put bash script file into gnome dock"
date: 2015-08-29
forum: General Help
---

### Post by Robbyx on 2015-08-29
I have created a simple bash script on my desktop. 

#!/bin/sh 
wine 'c:/Program Files/Any Password/AnyPass.exe'

The file is called anypass
It has no extension.
When I click the execute file, a  window  opens with buttons for execute, execute in terminal, open, cancel. The file's  permissions are set for anyone to execute the file. I only  want it to execute when I click on it. Should I make any changes to the script to get it to just execute without the window  opening?

How do I drag the file  into the gnome dock?

---

### Post by TheFu on 2015-08-29
chmod +x
Changes the file permissions only. Can't tell clearly if that has been done.

The gnome-.... option below isn't on my system, but I don't run gnome so that is not surprising.

---

### Post by CaptainMark on 2015-08-30
I would create a gnome launcher that will launch the script, you can give it good icon and drop it ~/.local/share/applications, then it will appear in your normal menu system and you can usually drag these to a dock quite easily.

You can create it directly with this command ```
gnome-desktop-item-edit --create-new ~/.local/share/applications/
```

This way you can also drop the script somewhere out of the way rather than having it sit on your desktop, but remember if you move the script after creating a launcher then the launcher will break.

---

### Post by Robbyx on 2015-08-30
Thank you both.

Assuming that --create-new is a program  option, what is the actual program I am invoking in 

"gnome-desktop-item-edit"

I looked in synaptic and I do not have anything close enough to match to be certain I have the right command.

---

### Post by CaptainMark on 2015-08-31
That is the name, I'm not sure about the package name, I was assuming it was in the core Ubuntu install but I may be wrong as I haven't used Vanilla Ubuntu for a long time. The package it's from is gnome-panel I believe but you should have that already if you have Gnome desktop installed.

---

