---
title: "Multiple tabs in terminal by default?"
date: 2014-05-29
forum: General Help
---

### Post by maciej-bak-85 on 2014-05-29
Hi,

every day in terminal gnome I use same 3 tabs which I name every day..

[ATTACH=CONFIG]253557[/ATTACH]

Is it possible to make it as default on terminal open ?

---

### Post by tgalati4 on 2014-05-29
In a terminal:

```
gnome-terminal --help
```

I don't know if you can get multiple tabs without some complicated configuration.  The profile will set up the title and colors for the first tab, but I don't know how to get other tabs set up in a configuration file.  I don't see the configuration parameters for it.

Maybe there are some gconf parameters that control tabs.  Otherwise you would have to execute keystrokes with the terminal (Control-shift-T), twice, to open two additional tabs and then select the correct profiles to give them the correct tab title and colors.  There is the ability to execute a command within terminal, so with some fancy script you might make it work.

With all of the different terminals available in linux, I'm sure there is one that makes this easier:

```
apt-cache search terminal
```

---

### Post by LastDino on 2014-05-29
Well, there is Terminator you can have multiple tabs in both horizontal or vertical split style, you can simply make a different Layout with your preferred way and switch to it every time you open Terminator. Not sure if you can name them or not, I've never tried that.

---

### Post by steeldriver on 2014-05-29
You can specify multiple tabs on the command line e.g.

```

gnome-terminal --tab-with-profile="Default" --title="Tab #1" --tab-with-profile="Default" --title="Tab #2"

```

The titles may get overwritten depending on your shell's PS1 prompt and the specified profile. You could create that as an alias.

---

### Post by Habitual on 2014-05-29
> **LastDino said:**
> Well, there is Terminator you can have multiple tabs in both horizontal or vertical split style, you can simply make a different Layout with your preferred way and switch to it every time you open Terminator. Not sure if you can name them or not, I've never tried that.

Sure can. Just arrange your terminator just how you want it and 
right mouse click and select Preferences > Profiles tab > Add and name it (I use Layout2) and launch it using 
```
terminator -l "Layout2" 
```

Enjoy the Goodness.

---

### Post by LastDino on 2014-05-29
> **Habitual said:**
> Sure can. Just arrange your terminator just how you want it and 
right mouse click and select Preferences > Profiles tab > Add and name it (I use Layout2) and launch it using 
```
terminator -l "Layout2" 
```

Enjoy the Goodness.

Thanks a bunch for useful information :) 
I hope OP finds it useful too.

---

### Post by tgalati4 on 2014-05-29
Steeldriver's suggestion works with mate-terminal on 12.10 so I imagine it works with gnome-terminal.  Now you can create a launcher with that command you should be happy as a clam in mud with mutilple terminal tabs.

---

### Post by Habitual on 2014-05-29
> **LastDino said:**
> Thanks a bunch for useful information :) 

Always glad to share.

---

### Post by maciej-bak-85 on 2014-05-30
thanks!
btw --working-directory is nice to set up which directory as default for this profile/tab

---

