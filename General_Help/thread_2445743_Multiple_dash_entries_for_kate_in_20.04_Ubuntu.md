---
title: "Multiple dash entries for kate in 20.04 Ubuntu"
date: 2020-06-19
forum: General Help
---

### Post by ejbiow on 2020-06-19
I'm not a regular gnome-shell user, but I'm liking it for my bedroom/TV computer, but I'm having a weird issue. Normally, when you add an item to the dash and you activate it the application does not spawn another icon on the dash, there is just a glowing dot next to it. But for some reason this is not the behavior I'm experiencing with the KDE text editor kate. When it is active it spawns a new icon, and because I'm using the oxygen icons it is a different color than I am used to, a blue. The problem is when I want to bring it to the front my motor-memory causes me to hit the white "favorites" kate icon, spawning a new page, not bringing the document I was editing to the front. Very annoying. This isn't the behavior I get from my dolphin file manager favorite in the dock. (I normally use plasma, and much prefer konsole, kate, dolphin, gwenview to their gnome equivalents but gnome is working well for this computer, it seems like 20.04 has really sped up the gnome environment, which was always very laggy on my low-powered hardware). I guess I could simple autostart kate since I use it most of the time and wouldn't be distracted by the 'favorites' kate icon, but I'd just like kate to act like every other application in the dash.

I've nosed around the net and the forum and looked over dconf-editor, but can't figure this out. The bottom two icons in this screenshot of the dash are the issue.
[https://i.ibb.co/9hdyDsj/screenshot.jpg](https://i.ibb.co/9hdyDsj/screenshot.jpg)

---

### Post by wildmanne39 on 2020-06-19
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by lvm on 2020-06-19
There are two kinds of programs: some e.g. libreoffice run a single or linked processes for all open windows while some e.g. kate run independent processes for each window. What you are seeing might be a result of that. GUI task managers usually have task grouping option which allows to merge all instances of running program into a single item, if dash has something similar it might help.

---

### Post by ejbiow on 2020-06-19
That is an interesting thought. But I don't think that is quite the issue, dash has the normal behavior for every other application but kate. FWIW, I always choose the 'ungroup' behavior in the KDE task manager.

The white icon in the dash does not link  to a running process, it merely opens a new instance of kate, but here  is an interesting wrinkle, each time I hit it I get a new separate blue  kate icon for each individual newly spawned instance. According to the  alacarte menu editor the command for the kate I used was 'kate -b %U'; I  created a new entry that was just 'kate' but it acted the same way it  had before. I tried a menu entry with 'kate -u' but now I have some sort of weird  unkillable process that is keeping that new desktop shortcut from working.

[I]0 T  1000   78772    1716  0  80   0 - 449709 do_sig ?       00:01:03 kate

[/I]I'll try it again after I reboot, but that might not be for a day or two.

I messed around with the kate sessions settings, but nothing I did seemed to matter.
[https://i.ibb.co/DCxGKKq/gnome-shell-screenshot-1-ITZL0.jpg](https://i.ibb.co/DCxGKKq/gnome-shell-screenshot-1-ITZL0.jpg)

Here  is a weird clue. Normally, if you launch an application you can  right-click on its icon in the dash and choose "Add to Favorites"; if I  call up an instance of kate from the command line or menu I get the blue  icon, but if I right click on it there is no option to add it to  Favorites.  I still can't figure this out.
[https://i.ibb.co/Q9pJrk9/Screenshot-from-2020-06-19-12-11-30.jpg](https://i.ibb.co/Q9pJrk9/Screenshot-from-2020-06-19-12-11-30.jpg)

---

### Post by Dennis N on 2020-06-19
In Ubuntu 20.04, I have Kate installed as Flatpak. I was able to add it to favorites and it does not spawn another icon when launched. So if you can't solve these issues otherwise, you could try the Flatpak version.

---

### Post by norobro on 2020-06-19
Adding the following to /usr/share/applications/org.kde.kate.desktop worked for me:```
StartupWMClass=kate
```

From here: [https://askubuntu.com/questions/1205119/how-to-show-dot-symbol-under-the-icon-of-the-opened-application-when-searching-i](https://askubuntu.com/questions/1205119/how-to-show-dot-symbol-under-the-icon-of-the-opened-application-when-searching-i)

---

### Post by ejbiow on 2020-06-21
This is what I got after launching kate, opening a terminal, entering "xprop WM_CLASS" and clicking on my kate window.
> $ xprop WM_CLASS
WM_CLASS(STRING) = "kate", "kate"


I wonder if I have to log out for this to take effect.  I tried these 3 varieties (not at the same time), but am still getting the same effect:

StartupWMClass=kate
StartupWMClass= "kate"
StartupWMClass  = "kate", "kate"

Edit: I added the lines (again, trying one at a time) to the end of the */usr/share/applications/org.kde.kate.desktop* file.

---

