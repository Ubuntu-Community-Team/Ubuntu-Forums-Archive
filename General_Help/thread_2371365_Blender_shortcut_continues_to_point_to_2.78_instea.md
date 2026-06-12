---
title: "Blender shortcut continues to point to 2.78 instead of 2.79 :("
date: 2017-09-13
forum: General Help
---

### Post by javierdl on 2017-09-13
This is what I have done:

1. Removed the shortcut I had in the Left panel launcher.
2. Ran Blender 2.79, while open I right-clicked on its temporary shortcut in the Left panel launcher, and chose "Lock in Launcher". 

But still, it keeps opening 2.78!

For now I am using a Link I made that I keep in the Desktop.

Thanks guys,

JDL

---

### Post by ajgreeny on 2017-09-14
Why do you have both versions installed?
How did you install them?

---

### Post by javierdl on 2017-09-14
Since I never install from Ubuntu Software (as it's never the latest version), I always end up with a tar.bz2 file (not an installer). So the resulted expanded folder I move it to my improvised Applications folder I have in Home. 
I was pretty sure I had done this before, and it did work.

---

### Post by javierdl on 2017-09-15
This is the answer:

Open the .desktop file corresponding to the application you want to change the path for with a simple word processing app like Gedit. See command line below for location of mentioned .desktop file.
You may want to make a duplicate of this file and add "_old" to the end of its name, just in case.
Replace both "Path=" and "Exec=" lines with the new address path pointing to the application in question.
Save it.
Done.

Example command line:
```
gedit ~/.local/share/applications/blender.desktop &
```

The longer and more complete answer:
[https://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand](https://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand)

---

### Post by ajgreeny on 2017-09-15
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

