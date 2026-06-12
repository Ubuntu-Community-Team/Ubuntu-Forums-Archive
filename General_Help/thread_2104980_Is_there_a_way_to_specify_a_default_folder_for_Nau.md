---
title: "Is there a way to specify a default folder for Nautilus"
date: 2013-01-14
forum: General Help
---

### Post by cforput on 2013-01-14
I want Nautilus to open to a different default folder than my home folder. I found an old post that showed how to do that from the terminal but since I'm a GUI Geek I want to find a way to do it when I click on the Nautilus icon. 

If you want to know why, read on but if you just want to answer my question you don't need to read the rest of this

I partitioned my hard drive into 3 sections. One for windows vista, one for 11.10 (12.nn doesn't work with my Realtek wifi card) and one for all my data that can be accessible by both Vista and 11.10 (Oneiric Ocelot). I try not to use my home folder to save any files so I never go there for anything. That's why I want Nautilus to open to my "shared/data" drive.

---

### Post by Frogs Hair on 2013-01-14
Are you saying you want the shared data drive permanently mounted in nautilus ? This seems like a catch 22 , use nautilus to create a folder in order it bypass Nautilus/Home Folder. 

> I want Nautilus to open to a different default folder than my home folder

---

### Post by tgalati4 on 2013-01-15
You could create a launcher (right-click on the desktop) to open nautilus with a specific folder.

Put in the command line dialog box:  nautilus /home/cforput/defaultfolderthatIalwayswanttoopen

man nautilus

or

nautilus --help

for more options.

---

### Post by mc4man on 2013-01-15
If your  "shared/data" volume is automounted on boot then you could simply edit the Exec= line in 
/user/share/applications/nautilus-home.desktop
(or copy the above to ~/.local/share/applications & edit there

You'd use 
```
Exec=nautilus [COLOR="Blue"]/exact/path/to/mountdir/name[/COLOR]
```

(if it isn't automounted or automounted with decent permissions for your user then you wouldn't do the above

---

