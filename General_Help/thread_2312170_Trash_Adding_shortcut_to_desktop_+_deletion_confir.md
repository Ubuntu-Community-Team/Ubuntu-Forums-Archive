---
title: "Trash: Adding shortcut to desktop + deletion confirmation"
date: 2016-02-02
forum: General Help
---

### Post by helm10101 on 2016-02-02
How can I add a shortcut to the Ubuntu desktop, in addition for the icon at the bottom left of the screen on the launcher?
Also, how can I make Ubuntu prompt me when I press delete on a file? like in Windows, where it asks you if you're sure you want to delete a file?

Thanks!

---

### Post by QDR06VV9 on 2016-02-02
See if this helps [http://askubuntu.com/questions/44678/how-to-add-a-shortcut-on-desktop](http://askubuntu.com/questions/44678/how-to-add-a-shortcut-on-desktop)

---

### Post by egeezer on 2016-02-02
As far as getting a delete confirmation, if you click on the file and press Shift-Delete, you get a confirmation pop-up before the action takes place.

---

### Post by howefield on 2016-02-02
> **helm10101 said:**
> ... how can I make Ubuntu prompt me when I press delete on a file? like in Windows, where it asks you if you're sure you want to delete a file?

Open up Files (Nautilus) and go into the preferences menu, should be an option similar to the one in the image below.

---

### Post by deadflowr on 2016-02-02
You add a trash can to the desktop with
```
dconf write /org/gnome/nautilus/desktop/trash-icon-visible 'true'
```
or
```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```
or install dconf-editor and navigate to the section org > gnome > nautilus > desktop, 
and simply toggle the trash-icon-visible to on.

---

### Post by helm10101 on 2016-02-02
> **runrickus said:**
> See if this helps [http://askubuntu.com/questions/44678/how-to-add-a-shortcut-on-desktop](http://askubuntu.com/questions/44678/how-to-add-a-shortcut-on-desktop)

This doesn't help for Trash because for Trash I don't see these. Only on regular files it works

> **egeezer said:**
> As far as getting a delete confirmation, if you click on the file and press Shift-Delete, you get a confirmation pop-up before the action takes place.

But Shift-Delete is for permanent delete. I was wondering if it can be done on a normal deletion as well

> **howefield said:**
> Open up Files (Nautilus) and go into the preferences menu, should be an option similar to the one in the image below.

I do not see anywhere "Preferences" :shock:. I tried right click, or to look somewhere in the window itself but I can't find it
> **deadflowr said:**
> You add a trash can to the desktop with
```
dconf write /org/gnome/nautilus/desktop/trash-icon-visible 'true'
```
or
```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```
or install dconf-editor and navigate to the section org > gnome > nautilus > desktop, 
and simply toggle the trash-icon-visible to on.

Thank you! It worked :KS
Btw, How did you know for example the code "dconf write /org/gnome/nautilus/desktop/trash-icon-visible 'true" is it because you knew this one specifically, or you're an experienced Linux user so that these commands come in a known pattern and you can actually find a code for any question about Ubuntu I'll throw at you?
And how come both codes work? just curious :D

Thanks everyone

---

### Post by deadflowr on 2016-02-03
> **helm10101 said:**
> This doesn't help for Trash because for Trash I don't see these. Only on regular files it works



But Shift-Delete is for permanent delete. I was wondering if it can be done on a normal deletion as well



I do not see anywhere "Preferences" :shock:. I tried right click, or to look somewhere in the window itself but I can't find it


Thank you! It worked :KS
Btw, How did you know for example the code "dconf write /org/gnome/nautilus/desktop/trash-icon-visible 'true" is it because you knew this one specifically, or you're an experienced Linux user so that these commands come in a known pattern and you can actually find a code for any question about Ubuntu I'll throw at you?

It called being a constant gardener.
Keep digging around.

I happen to remember that particular command.

To understand what dconf and gsettings do, you can look at the manpages 
```
man gsettings
man dconf
man 7 dconf
```
The last one gives you a clearer understanding of dconf.

Also, Ubuntu has vast resources on-line.
Good place to start is here:
[https://help.ubuntu.com/community/PopularPages](https://help.ubuntu.com/community/PopularPages)

**Edit:** forgot why I posted.
If the solution works for you please mark this thread as solved, so that others may someday find it, and maybe help them solve their own problem(s).
How to mark as solved here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by helm10101 on 2016-02-04
done. thank you

---

