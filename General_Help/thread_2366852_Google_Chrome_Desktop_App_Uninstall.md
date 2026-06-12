---
title: "Google Chrome Desktop App Uninstall"
date: 2017-07-22
forum: General Help
---

### Post by marcussignor on 2017-07-22
Hi guys.
I'm new to Linux. I was testing a fuctionality of google chrome, and I added the google keep website to the desktop as shown in the images. But as it was a test, now I wish to remove it. I tried right-clicking it and clicking on show details then remove, but it didn't work. Any tips?
[ATTACH=CONFIG]276097[/ATTACH][ATTACH=CONFIG]276098[/ATTACH][ATTACH=CONFIG]276099[/ATTACH]

EDIT: I forgot to say that I use the latest version of Ubuntu Gnome.

---

### Post by vasa1 on 2017-07-22
Please post the output of```
ls $HOME/.local/share/applications
```

---

### Post by marcussignor on 2017-07-22
I typed it on the Terminal and got this:
[ATTACH=CONFIG]276100[/ATTACH]

---

### Post by vasa1 on 2017-07-22
Now please try```
grep Name= $HOME/.local/share/applications/*.desktop
```

---

### Post by deadflowr on 2017-07-22
Perhaps run grep against Keep instead of Name=, since Name= will output all, and Keep should only show the single desktop file it would be inside.
forgot to add what it'd look like, so here:
```
grep Keep $HOME/.local/share/applications/*.desktop
```

---

### Post by oldos2er on 2017-07-22
> **marcussignor said:**
> I typed it on the Terminal and got this:
[ATTACH=CONFIG]276100[/ATTACH]

Please just copy and paste the terminal text into a post here; screenshots are unnecessary. If there is a lot of text output please use [code tags]("https://ubuntuforums.org/showthread.php?p=12776168#post12776168"). Thanks.

---

### Post by monkeybrain20122 on 2017-07-23
Those web apps are just instances of chrome, if you don't want to open all other tabs you should check the box "open as window" when you create them, then you have standalone instances of chrome open only to the specific websites for the apps in question. To remove them just go to .local/share/applications and delete the .desktop files (the "launcher icons")  Open the file manager, press ctrl+h or choose show hidden file from menu, find the hidden folder .local (note the "." in front), go to the subfolder applications and delete those files. If you have them in your desktop, delete them too.

---

