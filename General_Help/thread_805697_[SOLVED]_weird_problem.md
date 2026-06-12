---
title: "[SOLVED] weird problem"
date: 2008-05-24
forum: General Help
---

### Post by RMD94 on 2008-05-24
Hi everybody,

I am Rajas and i have a weird problem to tell u guys... 
My problem is: whenever i open a new window the top bar (i don't know what is the correct word for it) that has the close, minimize, maximize options......  it goes above the screen and i cannot move the window, the only way to do it is that i have to right-click on my awn and click move and then move it.........  and after that when i reopen the window i get the same problem.....

Looking forward to hear from u

-Thank You

---

### Post by Forlong on 2008-05-24
Install ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
Afterwards run it like this:
```
cssm
```
Then go to the **Place Windows** plugin and try changing the **Placement Mode** (e.g. to Centred).

---

### Post by RMD94 on 2008-05-24
i don't get it.. what do u mean by run it as cssm?????? i can't find where is that place windows plugin.........

---

### Post by SkonesMickLoud on 2008-05-24
You don't run it _as_ ccsm, you simply type *ccsm* into a terminal (Or System >> Preferences >> Advanced Desktop Effects Settings).  Then, scroll down to "Window Management", click on "Place Windows" and under 'Placement Mode', select "centered".

---

### Post by neymac on 2008-05-24
Open a terminal and type:
sudo apt-get install compizconfig-settings-manager

then, after ccsm (compiz config settings manager) is installed, type in the terminal:
ccsm

the program ccsm will open.
Then do what Forlong said above.

---

### Post by Forlong on 2008-05-25
> **RMD94 said:**
> i don't get it.. what do u mean by run it as cssm?
Just a tip for the future: every time somebody posts a command in [noparse][code][/noparse] tags, then it's most probably something you can run in the terminal.
In addition to that: any program can also be run via [Alt]+[F2]
(Of course, that will only work for programs, not commands like 'cp /foo/bar /bar/foo')

---

### Post by RMD94 on 2008-05-25
Thank You very much......

---

