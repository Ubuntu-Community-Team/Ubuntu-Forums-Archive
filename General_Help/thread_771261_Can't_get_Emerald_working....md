---
title: "Can't get Emerald working..."
date: 2008-04-27
forum: General Help
---

### Post by kylejn on 2008-04-27
First off, I'm completely new to Ubuntu/Linux, so please keep that in mind when offering solutions. Thanks!

My problem is that I can't seem to get any themes installed. I have compiz-fusion correctly installed, I think (I have the "Advanced Desktop Effects Settings" option in System->Preferences), and I also have Emerald installed (at least, I have the "Emerald Theme Manager" in System->Preferences).

However, whenever I try to drag a theme into the Emerald Theme Manager window, or try to select a theme via the "Import" option, it never works. No error or anything, it either does nothing (when I try to drag it in) or simply shows no themes to select (when using the "Import" button). I've downloaded a few themes with different formats, but it can't seem to find any of them.

Any suggestions?

Thanks!

EDIT: Not sure if you need this information or not, but my graphics card is an nVidia 8800GTS 640MB. I'm running the "restricted" drivers.

---

### Post by hessiess on 2008-04-27
run

```
emerald --replace
```

---

### Post by kylejn on 2008-04-27
OK, done that, now the window decorations are different, but I still get the same problems when I actually try to add any themes to the Emerald Theme Manager...

---

### Post by Donald-Duck on 2008-04-27
Are the emerald themes you're downloading in the format .emerald?

---

### Post by kylejn on 2008-04-27
> **Donald-Duck said:**
> Are the emerald themes you're downloading in the format .emerald?

Some are .emerald, some are .tar.gz, some are .zip, but none of them work.

---

### Post by Enthrall on 2008-04-27
I had the same problem. If you still havent got it working yet. Go into the compiz fusion manager. The place where you can turn certain effects off and on. Double click the window decorator. Look for commands. Type emerald --replace in the command box. Done should work.

---

### Post by freecode99 on 2008-04-28
I ran into the same issue using Hardy Heron as well. These worked previously under Gutsy, but they aren't working with the restricted or proprietary drivers under Hardy. These are all .emerald format themes as well, so that is not the issue. 

I have chosen to remove emerald for now until this gets resolved.

freecode

---

### Post by MemoryDump on 2008-04-28
> **Enthrall said:**
> I had the same problem. If you still havent got it working yet. Go into the compiz fusion manager. The place where you can turn certain effects off and on. Double click the window decorator. Look for commands. Type emerald --replace in the command box. Done should work.

would "emerald --replace" replace what's in that "command" box already? I have "/usr/bin/compiz-decorator" right now.

---

### Post by drdnl on 2008-04-28
Yeah, replace it all and it'll work. Just tried it out.

---

### Post by pjones0404 on 2008-04-28
i am having a similar issue. i am able to install emerald and have it running with --replace. 

i am having issues importing themes as well as switching between different themes. i was able to sue this no problem in gutsy. all of them are .emerald files. i am actually able to import then fine just nit switch between them.

---

### Post by freecode99 on 2008-04-28
RESOLUTION:

Change the gconf settings from /usr/bin/compiz-decorator to /usr/bin/emerald and it works.

If you have the configuration editor available under system tools, simply go to:

apps -> compiz -> plugins -> decoration

in Hardy, this is set to:

/usr/bin/compiz-decorator

in Gutsy, it was blank.

Reset this to:

/usr/bin/emerald

reboot and viola!

Emerald works again.

freecode

---

