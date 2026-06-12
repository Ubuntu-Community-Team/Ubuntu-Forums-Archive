---
title: "Quanta Plus Code Formatting"
date: 2008-01-04
forum: General Help
---

### Post by HeavyAl on 2008-01-04
Hey All,

Does anyone know of a way to turn off the 'hash' marks and spacing/tab marks that Quanta+ uses to denote these spots when formatting the code? For example, when you have 'soft wrap' turned on the code that is wrapped is indented to be in line with the original line that it came from, but there is a crosshatch effect that is placed prior to the wrap and it is distracting to my eyes as I scan the code. Also, tab markers look like a normal period and so it makes me think that I've added periods to my code where there shouldn't be any.

Any help would be appreciated!

---

### Post by p_quarles on 2008-01-04
You'll need to go to the "View" menu and deselect "Dynamic Word Wrap." The shortcut is F10. 

That said, I was unable to get Kate (which is used by Quanta) to save this setting from one session to another. I had to manually alter the rc to get it to stick.

If the same thing happens to you, you'll have to edit the quantarc file:
```
kate .kde/share/config/quantarc
```
(replace kate w/ your editor of choice, of course)
In the default file, the dynamic wrap option is on line 84. Change it to false.

---

### Post by HeavyAl on 2008-01-04
Yeah, that disables word wrap but I don't actually want to disable it - I just want the hash marks to go away. As you mentioned, some of the settings don't seem to stick, another one is custom schema's. You set your schema up and it doesn't load up that way when starting the program. I can set it manually but its just an extra step.

You know what would be really nice is some in depth documentation of the features of Quanta including tweaks to the rc file. 

Anyhow, thanks for the input.

---

### Post by p_quarles on 2008-01-04
Yeah, KDE 3.5 is a patchwork mess of bugs. That's pretty much why they've rewritten everything from the ground up for 4.

Disabling dynamic word wrap is the only way I know of to get rid of the hash marks. You can then enable *static *word wrap by going to Settings >> Configure Edtior >> Editing. But, more than likely you'll have to set this in the quantarc file as well. This also allows you to set the page width in characters, with the default being 80. 

Also, a handy trick for finding things in config files prior to opening them:
```
me@me:~$ cat -n .kde/share/config/quantarc | grep Schema
    75  Schema=quanta - Normal
```
The "-n" option in cat adds line numbers. ;)

---

