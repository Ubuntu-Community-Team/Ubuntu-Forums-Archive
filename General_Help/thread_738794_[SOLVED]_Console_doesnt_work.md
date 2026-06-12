---
title: "[SOLVED] Console doesnt work"
date: 2008-03-29
forum: General Help
---

### Post by crazyfuturamanoob on 2008-03-29
If I try to go to this directory in console, it wont go:
/home/arho/.wine/drive_c/Ohjelmatiedostot/Electronic Arts/Command & Conquer 3
And if I try to go to this directory, it will go:
/home/arho/.wine/drive_c/Ohjelmatiedostot/Electronic Arts
EDIT: For some reason above reads electron ic, trough i didnt put there any spaces,
and i dont see them even when editing this?? Why? Is this another bug?

I got this from console:
> 
[email]arho@ohra-desktop:~/.wine[/email]/drive_c/Ohjelmatiedostot/Electronic Arts$ cd Command\ &\ Conquer\ 3
[1] 7288
bash: cd: Command : No such file or directory
bash:  Conquer 3: command not found
[1]+  Exit 1                  cd Command\ 


Is this a bug, or did I mispell something? Anyway
it works with gui, but I want console. Help!

---

### Post by monraaf on 2008-03-29
You have to put a backslash before the &, otherwise bash thinks you want to run the command before the & in the background.

---

### Post by Antarctica on 2008-03-29
Directories that contain spaces must be enclosed within quotes
```
cd "home/arho/.wine/drive_c/Ohjelmatiedostot/Electron  ic Arts/Command & Conquer 3"
```
Try that.  It should work.

---

### Post by mvan83 on 2008-03-29
> **crazyfuturamanoob said:**
> If I try to go to this directory in console, it wont go:
/home/arho/.wine/drive_c/Ohjelmatiedostot/Electronic Arts/Command & Conquer 3
And if I try to go to this directory, it will go:
/home/arho/.wine/drive_c/Ohjelmatiedostot/Electronic Arts
EDIT: For some reason above reads electron ic, trough i didnt put there any spaces,
and i dont see them even when editing this?? Why? Is this another bug?

I got this from console:


Is this a bug, or did I mispell something? Anyway
it works with gui, but I want console. Help!

If you use tab completion (start typing a file name and hit tab -- it will fill in the filename for you or beep, after which you can hit tab again and it will show you all possible filename matches for what you've typed), bash will escape any "special" characters for you. The other option, as already mentioned is to use double or single quotes to delimit the filename.

---

