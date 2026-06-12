---
title: "[SOLVED] How to clean up/repair Nautilus file associations (Open With entries)?"
date: 2007-12-17
forum: General Help
---

### Post by bobstro on 2007-12-17
I'm running a fresh 7.10 Gutsy install and have a file association/MIME issue when using GIMP to open an image file of any flavor using the context menu "Open with->Open with GIMP Image Editor". When I select that option, nothing happens. The other entries all work fine, although there are many duplicates.

I've manually created a new GIMP entry using the "Open with other application..." option. That works fine, but I've now got a confusing and spurious entries that should be easy to fix, but I don't know where/how those files are stored. I understand how to work around the issue, but I want specifically to _clean up the Nautilus context menu_. 

Can anybody point me to some documentation on how Nautilus context menu entries are stored?

Thanks!

- Bob

---

### Post by danwood76 on 2007-12-17
Right click the image file and select properties then click the open with tab.

The rest should be self explanitory, remove to remove ones and add to re add the gimp.

---

### Post by bobstro on 2007-12-17
> **danwood76 said:**
> Right click the image file and select properties then click the open with tab.

The rest should be self explanitory, remove to remove ones and add to re add the gimp.

Hmm. I can't select the Remove option for the broken "GIMP Image Editor" option. And doing this for every possible graphic image type is going to be tedious and error prone.

Is there a "teach a man to fish" level answer that will illustrate the underlying mechanism, rather than keeping me stuck in the GUI front-end?


Thanks,

- Bob

---

### Post by cudjoe on 2008-01-17
I am also interested in that issue...
I thought they were stored in gconf but can't find them using gconf-editor.

In addition, the "Open With" menu is different when file type is unknown. And I would like to clean this one especially.

I tried several ```
find dir | xargs grep "string"
``` without success...

If you guyz have an idea, would love to hear it ! Thanks

---

### Post by outofnicks on 2008-01-17
Another "me too" here. In the context menu for "Open with", I have duplicate choices for Firefox and Bluefish and the Minus sign for remove is grayed out. Why is that?

---

### Post by cudjoe on 2008-01-18
Hey I found information in another thread :
[http://ubuntuforums.org/showthread.php?t=362368#8](http://ubuntuforums.org/showthread.php?t=362368#8)

For my part, I just had to delete .desktop files in 
```
~/.local/share/applications/
```

It's so obvious when you know the solution !

(bobstro, you may want to close this thread and switch to the other one...)

---

### Post by outofnicks on 2008-01-18
That other thread pointed me in the right direction, thanks.
I only had to navigate to .local/share/applications and delete the duplicate aliases but I had to restart X before that took effect.

---

### Post by bobstro on 2008-07-07
> **cudjoe said:**
> Hey I found information in another thread :
[http://ubuntuforums.org/showthread.php?t=362368#8](http://ubuntuforums.org/showthread.php?t=362368#8)

For my part, I just had to delete .desktop files in 
```
~/.local/share/applications/
```It's so obvious when you know the solution !

(bobstro, you may want to close this thread and switch to the other one...)

Done and thanks!

- Bob

---

