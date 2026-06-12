---
title: "Numerous Ubuntu problems/questions:"
date: 2007-06-16
forum: General Help
---

### Post by AlexanderPetros on 2007-06-16
1. My secondary hard drve randomly switches between being /dev/hdb1 and /dev/sdb1. It's happened at least four times now, and the only time that was after a major system change was when it happened right after I upgraded to Feisty.

1.5. Incidently, how can I set up my second hard drive to be one of the root folders in the Tree View in the File Browser? 

2. I have some backup CDs I burned on a Mac Mini. They read fine from Windows but in Ubuntu the filenames are all truncated to 30 characters and in lower case. And some of the files won't read at all because apparently I don't have the permissions to read them. What gives?

3. Clicking with my mouse is sluggish. When I click the mouse button there's a short delay before it system registers it. It's long enough that I often click on a window to move it and before the computer registers the click the mouse cursor is somewhere else. I've tried different mice and tried plugging them into the PS/2 port and a USB port with the same results. Or is this just one of those Linux things I have to get used to?

4. When I try to save a file (say from Firefox) in my home directory I have to scroll past all these hidden directories with dots in front of their names. Aren't these directories supposed to be hidden? I think I messed up a setting somewhere. How do I change it back to hide them (The "Show Hidden Files" setting in the File Browser doesn't change this).

5. My windows want to snap to things, like each other and the edge of the screen. I could have sworn I saw a setting somewhere to turn this off but now I can't find it. How do I turn this off?

6. As long as I'm asking questions: If I want to install a program manually (not from the repositories), where should I install the program? The documentation says the program directory can be put anywhere, but that's not helpful. What directorie should it go in?

Thank you.

---

### Post by charleseddy on 2007-06-16
I can help you with a couple of these.

1.  I don't know why it keeps switching back and forth, but in 7.04 they did change hard drive naming from hd to sd.

1.5.  When you are in /media in nautilus, drag it over to the pane that says "places".  It will now appear in the gnome places menu, as well as in the main tree.

2.  No idea.

3. No idea.

4.  This is the saving dialogue, not the main hiding setting.  Go to save another file (for example, just click a link in firefox and hit "Save As,"  then right click somewhere in the right pane (even on a file or folder) and uncheck "Show Hidden Files."

5.  I just assume this to be a standard feature of GDE, and have never desired to turn it off.

6.  Usually, put a period ( . ) in front of the program folder name that you compiled, then toss it in your home folder.  It will be hidden there.

---

### Post by avik on 2007-06-16
I can't answer all your questions, but I can try my best.

> 1.5. Incidently, how can I set up my second hard drive to be one of the root folders in the Tree View in the File Browser?

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

That link will guide you through the basic process, which you can adapt to your particular need.

EDIT: whoops, I think I misinterpreted you.  I guess charleseddy answered your question.

> 4. When I try to save a file (say from Firefox) in my home directory I have to scroll past all these hidden directories with dots in front of their names. Aren't these directories supposed to be hidden? I think I messed up a setting somewhere. How do I change it back to hide them (The "Show Hidden Files" setting in the File Browser doesn't change this).

Right click in the file chooser window and uncheck Show Hidden Files.  It's not in the File Browser per se, but rather a separate setting in the file chooser window.

> 5. My windows want to snap to things, like each other and the edge of the screen. I could have sworn I saw a setting somewhere to turn this off but now I can't find it. How do I turn this off?


Are you by any chance using Beryl or Desktop Effects?  That could potentially explain your mouse behavior as well.

> 6. As long as I'm asking questions: If I want to install a program manually (not from the repositories), where should I install the program? The documentation says the program directory can be put anywhere, but that's not helpful. What directorie should it go in?

That really depends on the application.  If you can find a .deb file, then you can just double-click it.  On the other hand, if your installing from source, your can usually use make install at the end.  Most other applications you can often run straight from any directory (so you can just keep them wherever you downloaded them).

Hope that helps even a little.

---

### Post by AlexanderPetros on 2007-06-16
Thanks, but isn't there a standard place for putting programs to keep everything organized? Like "Program Files" in Windows? Where do all those other programs install themselves?

---

### Post by bukwirm on 2007-06-16
Programs install different files in appropriate locations, for example, most system binaries go in /bin, most user program binaries go in /usr/bin, and data files often install in /usr/share. You can probably install your own private programs in a directory in your home folder (like ~/bin, for example). If you want all the users on your system to able to use the program, /usr/local/bin is probably a good place for it. Just make sure wherever you install it is on your [path]("http://www.google.com/search?q=unix+path").

Edit: You might want to read some of the articles in [this list]("http://www.google.com/search?q=unix+filesystems") for more information about where different files get stored.

---

### Post by michaelzap on 2007-06-23
RE #4: You have no idea how happy I am to have encountered the trick to this!

---

