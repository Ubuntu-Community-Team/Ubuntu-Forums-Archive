---
title: "Emerald won't start by default"
date: 2008-05-02
forum: General Help
---

### Post by Ender305 on 2008-05-02
I need help getting Emerald to start automatically, I can get it to work by using the command "emerald --replace" but it won't start automatically whenever I log in

---

### Post by TeoBigusGeekus on 2008-05-02
Go to System->Preferences->Sessions and add the command to the startup programs.

---

### Post by Ender305 on 2008-05-02
cool, that works perfectly

---

### Post by MattressVon on 2008-05-04
I found an even better solution. install the compiz fusion icon from synaptic or add/remove and then restart your system. go to Applications/System tools/compiz fusion icon , and start the appliction. it will appear in your desk tool bar. right click the icon and select "Select Window options" it should give you the option of using GTK or Enmerald. Select emerald and you are golden!

---

### Post by TheMemphisExperience on 2008-05-04
Those don't work for me. Whenever I log in, I have to reload the window manager from compiz-fusion icon. It's minor, but it is an annoyance. I've gone to the session manager and added emerald, but maybe i have the wrong command for opening it.

---

### Post by Ender305 on 2008-05-04
the commend is just ```
emerald
```, if that doesn't work, try ```
emerald --replace
```

---

### Post by TheMemphisExperience on 2008-05-05
Nope. 

I went into the session manager and removed compiz fusion icon, emerald, and some other start up commands. I think I have to look somewhere higher. Somewhere I have not yet been. Somewhere in some .lst or config beast buried somewhere on my computer is the answer I seek. 

In spite of Compiz-Fusion Icon not being a start-up program, it still starts. I think this is s husk left over from when I told the session manager to remember currently running applications.

I can only hope a new Hardy install disc will not be necessary. Because of the way things are, I can't even reinstall the system and keep my settings.

---

