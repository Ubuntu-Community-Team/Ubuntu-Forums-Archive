---
title: "Frost wire wont run properly"
date: 2007-05-21
forum: General Help
---

### Post by Death_Sargent on 2007-05-21
I have frost wire installed and java configured for the latest package.

The only thing is when i open it all i see is a blank window

---

### Post by Death_Sargent on 2007-05-21
now i have tested it with two seperate java engines and it still won't do anything but make a big blank box

---

### Post by taurus on 2007-05-21
By any chance you have beryl running?

---

### Post by Death_Sargent on 2007-05-21
Yes i do

---

### Post by Death_Sargent on 2007-05-21
ok i ran it in a nonxgl environment and it works so what am i supposed to do

the only way to integrate is in a clunky non acell environment.

---

### Post by Death_Sargent on 2007-05-21
Please help

---

### Post by taurus on 2007-05-21
So now you know where the problem is, it's up to you if you want to run frostwire or beryl.  I've heard that beryl and java don't like each other so that could be the problem with frostwire since it's a java base app.

---

### Post by rsambuca on 2007-05-21
Do you have beryl installed?  If so, they don't work well together.  Switch your window manager to metacity and then turn frostwire on.

---

### Post by Death_Sargent on 2007-05-21
Found a fix

use metacity to launch frostwire then switch back. 

Works fine though the extra step is kind of anoying.

---

### Post by macabro22 on 2007-05-30
Annoying indeed. Please let me know if there's a more sane solution to this.
Bugs... everywhere.

---

### Post by rsambuca on 2007-05-30
There is a small script you can run to have both frostwire and beryl running at the same time.  I haven't bothered, but if you search these forums for "frostwire beryl scrip java" I am sure you will find it.

---

### Post by xerosis on 2007-05-30
execute 'export AWT_TOOLKIT="MToolkit"' in a terminal for a one-time fix, or add it to your startup script.

---

### Post by macabro22 on 2007-05-30
> execute 'export AWT_TOOLKIT="MToolkit"' in a terminal for a one-time fix, or add it to your startup script.

Thanks! That hit the nail properly.

---

