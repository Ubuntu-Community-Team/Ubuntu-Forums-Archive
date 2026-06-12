---
title: "Some apps only run through terminal"
date: 2008-05-18
forum: General Help
---

### Post by castironpants on 2008-05-18
I've been having a problem with some programs of mine, most of them wine-based, like Wine-Doors, PlayonLinux and Google Earth. I can generally get them to load normally, but they don't seem to connect to their respective data sources/function properly unless I launch them from the terminal. In the meantime, I've changed their menu options to launch them in terminal with a nohup and exit command, but I'd like to get to the heart of the matter. What's wrong, exactly?

---

### Post by Mhurst1 on 2008-05-18
I have noticed this too. Report it as a bug!

---

### Post by castironpants on 2008-05-18
I'm not exactly sure how to do that. I should, I've been using Ubuntu long enough...

---

### Post by Mhurst1 on 2008-05-18
Launchpad.net

---

### Post by castironpants on 2008-05-18
Done and done.

---

### Post by Monicker on 2008-05-18
Hrmm. GoogleEarth has always worked fine for me using its desktop icon.

---

### Post by bravo331 on 2008-05-21
how do you launch Google Earth from the terminal?

---

### Post by sdennie on 2008-05-21
Is it possible that your apps have spaces in their path?  For example, if you install stuff in Wine, it's likely to end up in: ~/.wine/drive_c/Program Files.  However, if you don't quote the path or backslash the spaces, it won't work.  For example, to run WoW on linux, the command is likely to be:

```

wine /home/your_username/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe -opengl

```

---

### Post by castironpants on 2008-05-21
Well, I know you can do that or put the path in "". But even Google Earth, which (though has its own built-in wine) is still runnable as a linux app.

---

### Post by sdennie on 2008-05-21
I think google earth is a native port to linux (if you've installed it correctly) so, it shouldn't be using Wine at all (I think some other google app comes with Wine.  Picasa?).

---

### Post by castironpants on 2008-05-21
Well, either way, I installed the 4.3 beta binary and it's the linux version. It DOES work, just not from the main menu.

---

### Post by sdennie on 2008-05-21
Odd.  Pull the icon off the menu and drop it onto a blank spot in the panel.  Right click it and select Properties.  Change the application type to Application in Terminal.  See if it outputs anything interesting.

---

### Post by castironpants on 2008-05-21
Yeah, it works if I do Run Application in Terminal (its the same as running it in a terminal). There's no output. What I've done in the meantime is make a script that runs it with nohup and an exit command, and I run that in terminal from the menu. I just want to know whats going on.

---

