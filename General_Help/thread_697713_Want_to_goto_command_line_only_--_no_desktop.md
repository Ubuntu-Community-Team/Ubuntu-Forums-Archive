---
title: "Want to goto command line only -- no desktop"
date: 2008-02-15
forum: General Help
---

### Post by dman777 on 2008-02-15
Hello, I just installed Ubuntu and I love it. I'm not a desktop kind of guy though. So what I want to do it use the terminal window, execute things from command line, and  use compiz fusion to manage my windows.

So my questions are:

Which file do I edit so it does not load a desktop when I boot up but instead goes to console?

Where/what file do I edit  for the console fonts?

---

### Post by luisromangz on 2008-02-15
Mmmm, you want no desktop but want to use compiz fusion? It's quite extrange, and impossible...

---

### Post by Vadi on 2008-02-15
Ctrl+Alt+F1 will get you to the terminal.

I'm not sure as to what do you expect to do with Compiz though.

Edit: Or actually, well, just use only the terminal windows?

---

### Post by Spitphire on 2008-02-15
If you want to boot straight to console you need to disable gdm (i'm assuming you are using gnome) from loading on startup.. easiest way for you to do this would be to install a program called rcconf

```
sudo apt-get install rcconf
```

then run the program and deselect gdm and hit ok, restart your computer and you should be in a console.

---

### Post by dman777 on 2008-02-15
You should be able to run compiz fusion without a desktop environment(unless I'm wrong then someone please correct me). Simply go into the X server environment(xinit) and execute compiz fusion. That goes with any programs. 

I need to know what file to edit so when I boot Ubuntu it will go into console and not load up a desktop. Can anyone tell me?

Also, can anyone tell me where the fonts are at?

And, can anyone tell me where the console fonts are?

---

### Post by lovhorror on 2008-02-15
Haha, I did this accidentally recently, freaked me out. CLI is intimidating.

---

### Post by dman777 on 2008-02-15
I went to /etc/rc2.d/ and found a file called S30gdm and renamed it. I thought it was gnome but afterward i couldn't boot up. So I had to change it back. I'd rather do it the back end way than have that program do it for me. This way I can learn Linux better. Which file could it be?

---

### Post by PinkFloyd102489 on 2008-02-15
You could add this to /etc/rc.local:

```

./etc/init.d/gdm stop

```

This will stop gdm after it begins to load.

---

### Post by dman777 on 2008-02-15
Naw, that didn't do it. It made it stall out again during boot up.

---

### Post by PinkFloyd102489 on 2008-02-15
Try installing sysv-conf and removing gdm from all run levels.

---

