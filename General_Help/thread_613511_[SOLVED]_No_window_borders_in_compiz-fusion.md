---
title: "[SOLVED] No window borders in compiz-fusion"
date: 2007-11-15
forum: General Help
---

### Post by mlissner on 2007-11-15
I know this subject has been posted on several times, but I have not been able to find a solution to this problem. In short, I do not have borders on my windows when I am running compiz-fusion.

I don't entirely understand all of the xgl/compisiting techno-jargon, which is fine with me, but I have tried all of the gtk-window-manager --replace, emerald --replace, compiz --replace type commands, and none of them work.

The one clue I have discovered is that emerald --replace returns a segmentation fault. I have tried removing the settings directories, and I have tried reinstalling compiz, to see if that would help. I have also tried the xorg changes that have been thrown around here and there. So far, nothing seems to help.

I am running this on a laptop with an intel card on Gutsy.

Are there any other ideas out there for fixes?

---

### Post by mlissner on 2007-11-15
Help? I am dying without borders....I can't live like this...

---

### Post by oneadvent on 2007-11-15
I'm sorry, did you type those in the terminal?

Also did you try and just uncheck windows borders in ccsm?

Josh

---

### Post by mlissner on 2007-11-15
Yep. Tried that in the terminal, and tried unchecking windows decoration in ccsm.

---

### Post by DjBones on 2007-11-15
well, if there is a segfault in emerald, have you tried re-installing emerald through synaptic?
if you *need* window borders, you can just use the metacity borders like the default ubuntu uses for a while..

---

### Post by oneadvent on 2007-11-15
Has it worked before on this computer? Is this a recent problem?

Did you do something before this started happening?

---

### Post by mlissner on 2007-11-15
I have reinstalled emerald, and compiz, including purging them, just to make sure it wasn't something in a setting.

It has worked before on this computer, but I have no idea if I did something to make them break (if I did do something, it's beyond me what that was). It's a recent problem.

There's no way to use the metacity borders within compiz is there? I haven't been able to do that either, I don't think...

thanks for the quick replies...

---

### Post by oneadvent on 2007-11-15
did you remove the config files in your home directory when you did the uninstall and reinstall?

---

### Post by mlissner on 2007-11-15
Ummm...I'm not sure if I did that at the same time, but I did do that at some point along the road. Do you think that would make a difference?

---

### Post by oneadvent on 2007-11-15
did for me. I uninstalled completely everything that had to do with compiz, then went in and deleted that folder under .config 
Then I reinstalled and downloaded new emerald themes.

Then all I had to do was recheck mark the window border and it all worked.

---

### Post by mlissner on 2007-11-15
OK. I have moved .config/compiz, .config/autostart/compiz.desktop, .config/autostart/emerald.desktop, .config/autostart/gnome-compiz-preferences.desktop, .beryl-managerrc, and .emerald to backup locations. 

I have removed gnome-compiz-manager, compiz, ubuntu-desktop (a metapackage), compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-gnome, libcompizconfig-backend-gconf, and libgnome-compiz-manager0. 

Will report back if it works.

EDIT: Still had no borders until I ran metacity --replace. Now I have borders, but no compiz. I am proceeding to reinstall.

---

### Post by oneadvent on 2007-11-15
let us know.

---

### Post by mlissner on 2007-11-15
I am shocked. I really didn't think there was any hope, but after doing all that above, I still didn't have borders, which tipped me off to the fact that this could be bigger than compiz. 

Indeed, it was. I tried running gtk-window-decorator, and I noticed that even *it* was returning a segmentation fault, so I tried reinstalling it, which failed because it isn't an actual package, but aptitude informed me that libdecorator0 is a package, and that I could reinstall it.

Once I did that, lo and behold, I had borders. This has been a long road, I must say.

Any theories as to why libdecorator0 would need to be reinstalled? Very, very odd.

---

### Post by oneadvent on 2007-11-15
nope, got me. I'm just glad to hear that you are back up and running.

Don't forget to mark as solved.

(maybe a bad sector on your HD?)

---

### Post by mlissner on 2007-11-16
That may be. I had another rather strange problem not too long ago that pointed towards a bad hard drive sector. 

Hmmm...time to backup.

---

### Post by oneadvent on 2007-11-16
yikes, that sounds like a good idea then.

or you could get fancy and buy a very expensive raid controller card...

maybe you should just back up.

---

