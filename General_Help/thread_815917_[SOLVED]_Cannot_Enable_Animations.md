---
title: "[SOLVED] Cannot Enable Animations"
date: 2008-06-02
forum: General Help
---

### Post by PoopyTheJ on 2008-06-02
In Advanced Desktop Effects I can click on the animations box to enable it but when I close the window and reopen it's unchecked and animations are diabled. How can I enable them?

---

### Post by PoopyTheJ on 2008-06-02
Forgot to mention running 7.10 32bit with Radeon 3850HD and Catalyst 8.5 Drivers. Also though I have 4 desktops chosen and Desktop Cube enabled I only actually have 2 desktops. The rest of the Compiz effects also seem to not be working though in Appearance Custom settings are shown as checked.

---

### Post by Forlong on 2008-06-02
Well, first of all, make sure Compiz is running or not:
```
ps -o comm= -C compiz.real
```

---

### Post by PoopyTheJ on 2008-06-02
I ran that code but didn;t get any output, when I check animations, close advanced destop effects and reopen the check is gone, should that code have given me some output? When I login I get the compiz splash, dunno if that means anything. What is my next step and thanks for the reply!

---

### Post by PoopyTheJ on 2008-06-02
ok checked synaptics and I didn't have Compiz installed, though there were other compiz packages installed, now I have installed
compiz
compiz-bcop
compizconfig-settings-manager
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-pplugins-main
compiz-gnome
compiz-plugins

I can now enable animations though the animations don't seem to work, I'm assuming I installed some wrong packages here and they are causing some conflicts. now the command you gave me returns compiz.real as well.

---

### Post by PoopyTheJ on 2008-06-02
Ok, I found and ran compiz-check and it told me there was an issue with the installation path and gave me some code to run, did so and can now enable and get animations to work, my only problem now is when I set 4 desktops and close and then go back it's set for 3 I can't get 4 desktops to work for some reason. If anyone can help me with that then I'm golden and very thankful!

---

### Post by Forlong on 2008-06-03
> **PoopyTheJ said:**
> Ok, I found and ran compiz-check and it told me there was an issue with the installation path and gave me some code to run, did so and can now enable and get animations to work
Awesome. :)
That was the hardest part of the script.

As for the desktop problem:
Increase the value at *General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size* _not_ the number of desktops, that has to be left at 1 (see [here](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074) under "Getting the cube", there's also a screenshot).

---

