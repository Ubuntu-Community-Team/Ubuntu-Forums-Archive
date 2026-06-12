---
title: "help recovering Files/Nautilus"
date: 2023-10-12
forum: General Help
---

### Post by jdefed on 2023-10-12
I have a pc which is used mostly for internet, Ubuntu 22.04LTS. I have 3 exts. added mostly for desktop looks. I was playing around with a media program for playing my media library, and checked a box that allowed the program to modify files and folders. It ended up modiying the file/folder structure in Nautilus. Even though everything seems to function properly, when I open Nautilus its has definitely changed the folder layout. I tried uninstalling Nautilus and reinstalling but it comes back looking the same. Is there any way to recover the original look of Nautilus and folder/file structure.

Thanks
Jim

---

### Post by TheFu on 2023-10-12
>  I have 3 exts. 

What's this mean?

Also, which media player are you using?

---

### Post by jdefed on 2023-10-12
3 extensions  1) arcmenu 2) Dash to Panel 3) Desktop icons. It was Kodi and I have since removed it.

---

### Post by TheFu on 2023-10-12
> **jdefed said:**
> 3 extensions  1) arcmenu 2) Dash to Panel 3) Desktop icons. It was Kodi and I have since removed it.

Ok, I've use Kodi and it doesn't move anything. It can delete things, but not much else, and only if you set the permissions to allow that AND setup kodi to allow that access inside the settings.

I have no idea about Nautilus. It isn't the file manager I use, when I use one.  Someone else will need to help.

Long, long, long, ago, I had a coworker who was constantly losing files.  Turned out he'd gotten a new mouse and wasn't holding the button down during drag-n-drop operations.  As he was trying to copy files, he got confused and would drop files (moved, not copied) somewhere between the place he started and where he intended to drop them.  He was using some other OS, so I found a tool that was like 'locate' is on Unix and with it, he was able to find where those files had been dropped accidentally.  Not saying you are doing this, but it is possible. We all have hiccups sometimes.

---

### Post by MAFoElffen on 2023-10-12
From what you described, it sounds as if you changed the look and feel of Nautilus, and now want it back to default right?

If that is what is going on, you can reset the profile back to it's defaults by doing
```

gsettings reset-recursively org.gnome.nautilus

```

---

### Post by dragonfly41 on 2023-10-13
From another line of thought .. what does your file/folder layout look like in Thunar File Manager? The same?

---

### Post by jdefed on 2023-10-13
[COLOR=#000000][I]MaFoeiffien is correct, all i want is to get it back to default.  I will try your suggestion.
 thanks[/I][/COLOR]

---

### Post by jdefed on 2023-10-14
gsettings reset did not work. I also disabled desktop icons extension, as I think it modifies Nautilus. Any other suggestions?

---

### Post by jdefed on 2023-10-20
Dont know the exact reason it worked, but I renamed ~/.config/uses-dirs.dirs and when I restarted the pc it reloaded the correct folder/file setup~/.config/uses-dirs.dirs

---

