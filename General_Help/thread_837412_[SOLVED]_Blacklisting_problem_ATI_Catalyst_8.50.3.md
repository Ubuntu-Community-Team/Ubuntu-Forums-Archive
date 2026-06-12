---
title: "[SOLVED] Blacklisting problem ATI Catalyst 8.50.3"
date: 2008-06-22
forum: General Help
---

### Post by Marinodimare on 2008-06-22
I have just installed the new ATI drivers, v. 8.50.3. Previous versions did not work satisfactoraly with Compiz, so I decided to upgrade. Installation went flawlessly, as did configuration of xorg.conf. I ran glxgears without problems, and fglrxinfo did not report anything troublesome either. However, when I try to start Compiz (using ```
compiz --replace
```), the following error is returned:

```

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Not initializing the Gtk-Qt theme engine
```

I already changed ```
~/.config/compiz/compizconfig/config
``` to skip the driver check:
```

[kde_session]
profile =
plugin_list_autosort = true


[gnome_session]
profile =
plugin_list_autosort = true

SKIP_CHECKS=yes

```

I run KDE 3.5.8 on a system with an ATI Radeon x1650 pro video card. Does anyone have any idea what's going on?

---

### Post by Forlong on 2008-06-22
What's the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Marinodimare on 2008-06-22
Here's the output... again, nothing seems to hint at problems..
```

./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   KDE
 Graphics chip:         ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

---

### Post by Forlong on 2008-06-23
I see... I haven't thought of this combination yet.

Run this command in the terminal:
```
mkdir -p $HOME/.config/compiz && echo SKIP_CHECKS=yes >> $HOME/.config/compiz/compiz-manager
```
Afterwards, you should be able to run Compiz just fine.

---

### Post by Marinodimare on 2008-06-23
It worked! the only thing now is that Compiz is a bit slow in moving/resizing windows. Any idea how to fix this? I can't imagine my hardware being too slow.

---

### Post by Forlong on 2008-06-23
That's actually a common problem.
Compiz has to calculate the window's geometry for every step. Don't know if this will be "fixed" anytime soon.

Because of that, I recommend setting the **Default Resize Mode** to **Rectangle** in the **Resize** plugin.

(in case you don't have ccsm installed, run 'sudo apt-get install compizconfig-settings-manager')

---

### Post by Marinodimare on 2008-06-23
Sorry, one more problem: window switching (ie. alt+tab or similar) sometimes results in loss of window borders. Any idea why?

---

### Post by Forlong on 2008-06-23
I have frankly never heard of such a problem. You might want to file a bugreport for that.

---

### Post by Marinodimare on 2008-06-23
will do. Thanks!

---

