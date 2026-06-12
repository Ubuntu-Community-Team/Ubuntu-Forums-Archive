---
title: "Stupid permissions question"
date: 2007-06-27
forum: General Help
---

### Post by Contrarian on 2007-06-27
I'm logged in to the desktop as a basic user.  I want to change permissions on a folder, but I'm not the owner.  Now i know in term I can use SU to change my permissions then I can use chmod, but i'd like to do this within the GUI.  Basically I need to do something as root, and I'd like to do it within the GUI whenever possible .

---

### Post by nsleiman on 2007-06-27
use "sudo" instead of 'su',
ex. sudo chmod 755 Folder1/ Folder2/
the 755 are for:
owner group everyone
rwx-rwx-rwx=777

if you want to make it read and write for all means you want 110-110-110
where 110 in binary is 6
...

you need maybe to change the owner also, type: "man chown" and "man chgrp" to see what is it about before 

this works on linux but i dont think its same syntax on windows machines,

---

### Post by Contrarian on 2007-06-27
Right, I know how to do it from the command line.  But I want to do it within the GUI.  I notice I cannot login to the GUI as root, and I'm wondering if there is an equivalent to SU to raise my permissions to have root level access at GUI and throughout.  Yes, I know this is a "security risk", but I'm not concered about security in as much as wanting ease of use.

---

### Post by ajgreeny on 2007-06-27
If you open nautilus with **gksudo nautilus** you will have root access for doing things like changing permissions and owner etc.  Just **right click>properties**  on the file and make the changes you need in the tabbed dialogue box that appears.  As long as you are aware of the potential dangers of doing this it is worth putting a link on the desktop for this, right click on the desktop and add a launcher (I think that's what it's called in gnome, I use kde).  I've done exactly that but using kde so there it's [B]kdesu konqueror.

[/B]However, it's worth getting used to the command line as it can be very very useful at times;  if x breaks and and you have no GUI, it's all you've got and it is good to know how to deal with things.

---

### Post by Ziox on 2007-06-27
you can always start nautilus with root access:

gksudo nautilus

---

### Post by Contrarian on 2007-06-29
Thanks.  

Actually I'm  familiar with the command line.  However  I wanted to be able to also do it from the GUI.  As I get older, there are times my fingers are getting arthritic/carpal tunnel, so i prefer to be able to move the mouse and do a few clicks than having to type in a long path and other commands.  

Sure this one time it wasn't much I needed to do, I spent more effort typing in and requesting how to do it, but now I know.  I have the option to do either way now.

---

