---
title: "How to mount my windows desktop folder in ubuntu?"
date: 2008-04-29
forum: General Help
---

### Post by pyrotherm on 2008-04-29
Hey guys,

Was wondering if any of you knew a way to mount my "%homedir%\desktop folder in my windows partition (which I have already mounted to dev/sda1) into my Home directory in Ubuntu 8.04, so that I may share the same desktop folder between ubuntu and windows

Thanks in advance, I have faith in you people!,

Pyrotherm

---

### Post by scragar on 2008-04-29
it's not possible to mount a folder to another, however it is possible to link your desktop to the desktop of the windows folder, however you should remember that shortcuts from windows won't work on linux, and visa versa.

Easiest way would be to use the file manager to go and middle click/drag your folder to the home folder, and choose link here when asked, once your done delete your current desktop folder and rename the link. then restart the desktop```
kill-all nautilus
```



WARNING - if you do not have your windows partition mounted you will technicaly not have a desktop, and it will cause several errors and problems, be warned.

---

### Post by Zorael on 2008-04-29
> **scragar said:**
> WARNING - if you do not have your windows partition mounted you will technicaly not have a desktop, and it will cause several errors and problems, be warned.
It's possible to make a mount --bind so that the desktop directory always "exists". Any previous content will not be accessible but will neither be destroyed. I did this before I learned of symlinks, heh.
```
$ sudo mount --bind "/media/windows/Documents and Settings/Zorael/Desktop" ~/desktop
```
Then you could place it into /etc/fstab to get it automounted on boot, but it doesn't understand long filenames enclosed in quotes, so you'd have to replace whitespaces with \040. One tip, if the path contains "weird" characters, is to mount it manually in lieu with the first command, then do examine the contents of **/etc/mtab** (with cat/grep/gedit/nano/anything) to get an idea of how fstab interprets it. Then just paste the relevant line into /etc/fstab. Backup first.
```
$ grep -i desktop /etc/mtab
/media/windows/Documents\040and\040Settings\Desktop /home/zorael/desktop none rw,bind 0 0
```
Or, all in one command;
```
$ grep -i desktop /etc/mtab **>>** /etc/fstab
```
If you enter > instead of >> you'll wipe your fstab. Bad bad. Lucky you backed it up, right? Right?

---

### Post by pyrotherm on 2008-04-30
Thank you guys so much, the link thing didn't work, but the binding to the folder through fstab did the trick nicely!

---

