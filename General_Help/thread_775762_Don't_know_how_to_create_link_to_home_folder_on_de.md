---
title: "Don't know how to create link to home folder on desktop"
date: 2008-04-30
forum: General Help
---

### Post by floatingbox on 2008-04-30
A new Ubuntu (former Windows) user here. I've been trying for some time now to create a link to my home folder on my desktop.

First, I went to /home and right-clicked on my home folder. However, the "Make Link" option is grayed out for some reason so this does not work.

Second, I try to make a link to a folder inside my home folder and move it to the desktop, with the intention to just edit the link path. I right click the link and choose "Properties". I can edit the name of the link, emblems, permissions, and other properties, but not the link target. So this does not work. I try to open the link in a text editor to see if it is a simple text file that can be edited, but it cannot be opened.

Third, I try to drag and drop  the "Home folder" link from the "Places" menu onto the desktop, but get a message that "You cannot copy a folder into itself".

Fourth, I right click on the desktop and choose "Make Launcher" (which seems the closest option, although I really just want a link, not a "launcher"). I choose "Type: Location". I click on "Browse" and navigate to /home. But I am unable to select a folder here, apparently only files can be opened. So I close the file selection dialog and manually type in the path "/home/<username>"; this works.

Now there is still a problem: the icon for the launcher is a small ugly screw. I'd at least want the launcher to look like a folder. I open its Properties dialog and look around for a "Change icon" option, but there is none to be found.

After a while I figure out that I can click on the button with the icon on it (which I at first didn't notice since the icon consists of a few barely visible pixels) for a "Select Custom Icon" dialog. However, this dialog doesn't show a list of icons but the entire filesystem. I have no idea where in the filesystem to locate a folder icon.

I've run out of ideas. What next? I get the feeling I'm missing something obvious here.

---

### Post by MemoryDump on 2008-04-30
* Open the Configuration Editor, by running the program **gconf-editor** (ALT-F2 to open a RUN box)
    * Choose apps->nautilus->desktop.
    * Tick the box beside computer_icon_visible, home_icon_visible, and trash_icon_visible. The changes take effect immediately.

---

### Post by Nepherte on 2008-04-30
open gconf-editor (press alt+F2 and type gconf-editor). Navigate to apps > nautilus and check home_icon_visible.

---

### Post by Triggerhapp on 2008-04-30
Run up a terminal and type "ln -s ~ ~/Desktop/Home" That should be enough :)

---

### Post by Triggerhapp on 2008-04-30
ooh, a BETTER idea might be to make a "new launcher" and type in something like "nautilus /home/yourusername" as the command and "Home" as the name

Edit : Or you could do the right thing, thanks Nepherte.
Maybe I should stop giving advice about gnome when i dont use it XD

---

### Post by stoogiebuncho on 2008-09-21
Sounds like this has been solved, but I thought I'd put my two cents in here.

I was trying to put a link to the home folder on my AWN dock thingy, and was having trouble getting it to work.

What I finally realized was that when you open nautilus, it automatically opens to your home folder, so all I had to do was create a launcher to launch nautilus, and then change the icon to your home folder icon.

So create a new launcher.  Name = Home  Command = nautilus.  Change the icon, you're good to go.

---

### Post by bmasterflash on 2010-07-04
I know that this thread is old, but I thought that I would just add something for those users having this problem and finding this discussion through Google.  If 'make link' is greyed out it is probably because you do not own the folder.  You can change the permissions/owner to get make link available, or better yet just hold ctrl and shift while you drag the folder where you want the link - your desktop for instance.  That should do the trick.

---

