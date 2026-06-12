---
title: "Command help"
date: 2007-10-29
forum: General Help
---

### Post by WrathofthePenguin on 2007-10-29
Ok, I'm trying to edit a starter in gdesklets. Specifically, the home folder launcher on the Starterbar. However, I can't edit the icon because there's no command entered into the Starter. If this isn't making sense, right-click on the home folder on the Launcherbar gdesklet. Click "Edit starter". Note that the Type is Application, The name is Home, but there's no Command. All I'm trying to do is edit the icon being used, but it won't let me save it because the command is blank.

So, I guess I need to know what the terminal command would be to open a window for your home folder.

Thanks!

---

### Post by SPr on 2007-10-29
From the terminal
```
nautilus ~
``` Kubuntu would use Konqueror rather than Nautilus.

The shell will expand the ~ to the path to your home folder.

---

### Post by WrathofthePenguin on 2007-10-29
Thanks! That did it. I was pretty unsatisfied with the icon being used since it was 48x48 - I wanted to switch to a much higher resolution one, since the launcher magnifies it.

---

### Post by SPr on 2007-10-29
You're welcome :)

---

