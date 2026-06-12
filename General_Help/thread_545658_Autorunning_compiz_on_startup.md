---
title: "Autorunning compiz on startup"
date: 2007-09-07
forum: General Help
---

### Post by superbenny on 2007-09-07
Every time I start up Kubuntu, it loads up kwin as a window manager, and i need to run compiz --replace in the command line to load compiz-fusion. is there any way to load it during boot, as opposed to running the command every time:confused:

---

### Post by DarkOx on 2007-09-07
Yes, there is. First, make a file in /usr/bin called startcompiz.sh

> kdesu kwrite /usr/bin/startcompiz.sh

Now, place the following in the file and save.

> 
#!/bin/bash
compiz --replace &
sleep 5
emerald --replace &

Make the file executable, either through konqueror running as root or using "sudo chmod 755 /usr/bin/startcompiz.sh"

Test the file to make sure it works correctly. If you type "startcompiz.sh" at the command prompt, it should load compiz. If it does, it's safe to go on.

Open the file ~/.bashrc

> kwrite ~/.bashrc

Now, append the line "export KDEWM=startcompiz.sh" to the file, save and exit. Now when you log into KDE, compiz will be your window manager, not kwin.

---

### Post by superbenny on 2007-09-07
> **DarkOx said:**
> Yes, there is. First, make a file in /usr/bin called startcompiz.sh



Now, place the following in the file and save.



Make the file executable, either through konqueror running as root or using "sudo chmod 755 /usr/bin/startcompiz.sh"

Test the file to make sure it works correctly. If you type "startcompiz.sh" at the command prompt, it should load compiz. If it does, it's safe to go on.

Open the file ~/.bashrc



Now, append the line "export KDEWM=startcompiz.sh" to the file, save and exit. Now when you log into KDE, compiz will be your window manager, not kwin.
ok everything works up until bashrc. when i run startcompiz.sh in the command promt, it loads compiz up fine. i wrote export KDEWM=startcompiz.sh to the very end of ~/.bashrc, but when i restarted, kwim was the manager still. i checked to make sure that the line was still in bashrc and it was.

---

### Post by DarkOx on 2007-09-07
What manufacturer of graphics card are you running? I think that you may need to use one of the following to start compiz:

Nvidia
> compiz --replace --indirect-rendering --sm-disable ccp &

ATI
> LIBGL_ALWAYS_INDIRECT=1 compiz --replace --indirect-rendering --sm-disable ccp &

Intel
> INTEL_BATCH=1 LIBGL_ALWAYS_INDIRECT=1 compiz --replace --indirect-rendering --force-aiglx --sm-disable ccp &

Try replacing the "compiz --replace &" with the one that applies, and see if that works.

---

