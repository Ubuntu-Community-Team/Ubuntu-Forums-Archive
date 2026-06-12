---
title: "Computer does not shut down completely"
date: 2007-06-28
forum: General Help
---

### Post by Max_Sterling on 2007-06-28
I previously had Ubuntu 5.10 and installed 7.04 last weekend from the live cd.  Now, when I try to shutdown the computer, the shutdown status bar image stays on the screen showing 0%, and the fan on my power supply continues to run.  In order to shutdown the computer completely I have to press the power button.

I didn't have to do that with 5.10...it shut itself down completely.  Is there any setting on 7.04 that I can change to have it completely power off my machine or am I stuck?

I'm running Ubuntu 7.04 on an old (1999-2000ish) era HP Pavilion desktop.

---

### Post by berniedd on 2007-07-01
I have the same problem on two different desktops where I installed Ubuntu Edgy and Feisty.Both were socket 462s with Athlon Semprons. I'm stumped.

---

### Post by confused57 on 2007-07-01
This might work:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

---

### Post by berniedd on 2007-07-02
Yaay, that worked! Although the command SUDO GEDIT /ETC/MODULES worked only if I typed it in lowercase.  Thanks, man.  Before, I had to unplug the AC cord from the wall socket to completely turn it off. Had to do that because my monitor's On/Off power button was stuck in the ON state permanently.

---

### Post by Max_Sterling on 2007-07-03
Thank you very much, that solved my problem.  Now my computer shuts down completely.  I appreciate your help!

---

