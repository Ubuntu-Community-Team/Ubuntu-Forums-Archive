---
title: "Help with Wine"
date: 2008-04-02
forum: General Help
---

### Post by FS92 on 2008-04-02
Hello :)

I've installed Wine, but when i'm trying to launch a .exe file installed on windows partition nothing happens... What do i have to do to get it work?

---

### Post by kesman on 2008-04-02
How are you trying to launch the executable? Try from terminal with command

```

wine /path/to/exe/executable.exe

```
and see if there's error messages.

---

### Post by FS92 on 2008-04-02
When i try to  click the .exe file twice i get this message:"
 The filename "launcher.exe" indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

When i try "open with Wine Windows Emulator" nothing happens...

Open i terminal i didn't quite understand, did i do it right?;
 erlend@erlend-laptop:~$ Wine /media/HDD/Program Files/Paragon Software/Partition Manager 9.0 Professional/Program/exe/launcher.exe
bash: Wine: command not found

---

### Post by kesman on 2008-04-03
the command is lower-case, not Wine but wine

---

### Post by soxs on 2008-04-06
And you have to put a \ in front of space

---

### Post by Paris Heng on 2008-04-06
> **FS92 said:**
> Hello :)

I've installed Wine, but when i'm trying to launch a .exe file installed on windows partition nothing happens... What do i have to do to get it work?

Hi, have you able to run the .exe right now?

---

### Post by FS92 on 2008-04-06
Hello

My HDD chrashed a couple of days ago so i haven't had time to install windows yet. I'll try it out soon:)

---

### Post by LaRoza on 2008-04-06
> **FS92 said:**
> When i try to  click the .exe file twice i get this message:"
 The filename "launcher.exe" indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

When i try "open with Wine Windows Emulator" nothing happens...

Open i terminal i didn't quite understand, did i do it right?;
 erlend@erlend-laptop:~$ Wine /media/HDD/Program Files/Paragon Software/Partition Manager 9.0 Professional/Program/exe/launcher.exe
bash: Wine: command not found

You can write click it, and chose to open it with Wine.

---

### Post by FS92 on 2008-04-06
> **LaRoza said:**
> You can write click it, and chose to open it with Wine.


When i try to do that nothing happens

---

