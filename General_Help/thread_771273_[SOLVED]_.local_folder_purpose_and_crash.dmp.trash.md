---
title: "[SOLVED] .local folder purpose and crash.dmp.trashinfo files"
date: 2008-04-27
forum: General Help
---

### Post by Diabolis on 2008-04-27
I analyzed my hard drive with Disk Usage Analyzer and found that I have a hidden folder, .local, that is consuming almost 2gb of space.

Does anyone know why is that folder there or how it is used?

I assumed that it was created by gnome because it has Trash folder (which is not a hidden folder) here is the structure of the folder:
```
ls -R .local/ | grep ./

.local/:
.local/share:
.local/share/applications:
.local/share/applications/wine:
.local/share/applications/wine/Programs:
.local/share/applications/wine/Programs/Diablo II:
.local/share/applications/wine/Programs/fabFORCE:
.local/share/applications/wine/Programs/Hero Editor:
.local/share/applications/wine/Programs/Joost:
.local/share/applications/wine/Programs/Packet Tracer 4.11:
.local/share/applications/wine/Programs/Warcraft III:
.local/share/applications/wine/Programs/World of Warcraft:
.local/share/desktop-directories:
.local/share/icons:
.local/share/Last.fm:
.local/share/Last.fm/cache:
.local/share/mime:
.local/share/mime/application:
.local/share/mime/packages:
.local/share/tracker:
.local/share/tracker/data:
.local/share/Trash:
.local/share/Trash/files:
.local/share/Trash/files/amsn_received:
.local/share/Trash/files/JMusic:
.local/share/Trash/files/JMusic/src:
.local/share/Trash/files/JMusic/src/jmusic:
.local/share/Trash/files/JMusic/src/jmusic/resources:
.local/share/Trash/files/JMusic/src/jmusic/resources/busyicons:
.local/share/Trash/files/JMusic/src/META-INF:
.local/share/Trash/files/JMusic/src/META-INF/services:
.local/share/Trash/files/JMusic/test:
.local/share/Trash/info:

```
off topic: is it possible to list the structure of a folder as a tree? 

As you can see it also have folders related with other applications, that doesn't make sense to me. For instance, why is wine showing up here if it has its own folder (.wine). I really don't care about those application folders because they don't use too much space.

The important part is the Trash folder, I found there files that I though were deleted. This were files that I used like a moth ago, how come they still here? This folder has a "info" folder. It has many files, they seem to be log files with terminations like **.trashinfo, crash.txt.trashinfo and crash.dmp.trashinfo** What could cause this errors?

This must be some kind of bug, I wasn't aware of all this. My Trash folder has been empty and I though everything was running smoothly, but now I know it wasn't the case.

---

### Post by chrisccoulson on 2008-04-27
~/.local/share/applications is where GNOME stores user specific .desktop files, which appear as launchers in your menu. The wine folder contains launchers for your Windows applications.

~/.local/share/Trash contains two folders - files and info, as per the Freedesktop spec. When you move files to trash, they end up in ~/.local/share/Trash/files, and a corresponding XML file ends up in ~/.local/share/Trash/info, which describes the files in trash, containing information such as where the file was deleted from. It also provides the framework for being able to restore files from trash, which will end up in future GNOME releases.

As for files that you thought you had deleted from your trash - your best bet is to clear the contents of files and info just incase something got screwed up, and then see if it happens again.

---

### Post by Diabolis on 2008-04-27
> It also provides the framework for being able to restore files from trash, which will end up in future GNOME releases.

Ok thankyou for the info, now I get it. Any ideas on what could cause this problem? so I can try to trouble shoot it?

---

### Post by chrisccoulson on 2008-04-27
The only thing I can think of is that the files in ~/.local/share/Trash/files and ~/.local/share/Trash/info may have been manipulated directly instead of using the GVFS trash:/// backend. I don't know what effect manipulating the files directly would have though.

---

