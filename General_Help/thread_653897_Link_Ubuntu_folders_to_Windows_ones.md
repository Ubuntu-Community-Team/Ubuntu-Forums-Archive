---
title: "Link Ubuntu folders to Windows ones?"
date: 2007-12-30
forum: General Help
---

### Post by deleopario on 2007-12-30
I'm setting up a dual boot computer for my dad with most of the space on a FAT32 partition for XP. I want to try and link the home subfolders to the folders in Windows so that he can save files and have them be in the same place on both (without having to bother going to media/hda1/Documents and Settings...etc).
I tried "ln -s Documents /media/hda1/Documents\ and\ Settings/Runciman/My\ Documents" (with and without root), but it said "Operation is not permitted." Any ideas?

---

### Post by nick_h on 2007-12-30
Make sure the folder "Documents" does not already exist.

Also I think you have the 2 arguments in the wrong order.

---

### Post by deleopario on 2007-12-30
Ohhh, I see, it has to not exist? That could be a problem, as the folders are currently in all of those places shortcuts, which I want to keep, but if I delete the folders and then remake them as links will the shortcuts still be there?

---

### Post by nick_h on 2007-12-30
Shortcuts and symbolic links are the same thing.  I'm not quite sure what you want to do.

Try:
```
ln -s Documents /media/hda1/Documents\ and\ Settings/Runciman/My\ Documents Windows\ Files
```

You will now have a folder called "Windows Files" in your home directory which will point to your "My Documents" folder in Windows.

---

### Post by deleopario on 2007-12-30
Well, by shortcuts in this case I mean how under "Places" in the menu it has the links to Documents, Music, Pictures, etc. I want to keep those links but have them point to the Windows folders instead.

---

### Post by nick_h on 2007-12-30
Just delete the folder and replace it with a link with the same name.

---

### Post by deleopario on 2007-12-30
Oh okay, great, I was hoping that would work but I didn't want to risk trying without knowing if it would screw something up.

---

