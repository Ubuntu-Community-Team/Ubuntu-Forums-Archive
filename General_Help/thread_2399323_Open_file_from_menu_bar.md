---
title: "Open file from menu bar"
date: 2018-08-24
forum: General Help
---

### Post by monkeybrain20122 on 2018-08-24
Many applications (e.g Firefox, evince, gimp) have a File > Open File or File > Open option in the menu, when click it brings up a window from which you can choose the file to open. But depending on the application the box  that pops up may be the same or different. E.g if click File > Open File from Firefox it open a window that looks like nautilus (but not) and for other option it has some others. It seems that this is determined by some kind of settings in the OS rather than the applications because in some cases I notice the windows that  open by the same application somehow are different in two installations of Ubuntu. I wonder how this is determined because in some cases the windows have a search function which is very convenient in others no.

Sorry I can't phrase this very well but hopefully descriptive enough.

---

### Post by monkeybrain20122 on 2018-08-25
bump

---

### Post by #&amp;thj^% on 2018-08-25
Perhaps if you showed us the differences might help.
Also there is some good points made here: [https://unix.stackexchange.com/questions/149033/how-does-linux-choose-which-application-to-open-a-file](https://unix.stackexchange.com/questions/149033/how-does-linux-choose-which-application-to-open-a-file)
EDIT: 
```
XDG-OPEN(1)                     xdg-open Manual                    XDG-OPEN(1)

NAME
       xdg-open - opens a file or URL in the user's preferred application

SYNOPSIS
       xdg-open {file | URL}

       xdg-open {--help | --manual | --version}

DESCRIPTION
       xdg-open opens a file or URL in the user's preferred application. If a
       URL is provided the URL will be opened in the user's preferred web
       browser. If a file is provided the file will be opened in the preferred
       application for files of that type. xdg-open supports file, ftp, http
       and https URLs.

       xdg-open is for use inside a desktop session only. [U]It is not
       recommended to use xdg-open as root.[/U]

OPTIONS
       --help
           Show command synopsis.

```

---

### Post by monkeybrain20122 on 2018-08-25
> **1fallen said:**
> Perhaps if you showed us the differences might help.



Here are a few screenshot of windows that come up when choose File > Open or File > Open File or similar from different apps (Firefox, evince, qpdfview, foxit)

See the second one has a search button on the side panel, the third one has a search (with x-nautilus ..) but doesn't work, the last one can search by typing into "file name" but it is really stupid because it only works with exact match including case

---

### Post by #&amp;thj^% on 2018-08-25
If it helps I can get a search bar by using keyboard combo <ctrl+f>

---

### Post by Dennis N on 2018-08-25
> But depending on the application the box that pops up may be the same or different
Might be for the same reasons discussed in this thread:
[https://ubuntuforums.org/showthread.php?t=2358715](https://ubuntuforums.org/showthread.php?t=2358715)

---

### Post by monkeybrain20122 on 2018-08-25
> **1fallen said:**
> If it helps I can get a search bar by using keyboard combo <ctrl+f>

Hi, it works only for some kind of windows (the first and third screenshots) But the search is very dumb in that you need to have exact match in the first word. If I go to the book folder and type ctrl+f and then type "linux", then it will find "linux networking" but not "introduction to linux networking" or "Linux networking", so that is pretty useless if I have a lot of documents. but the search in the second screenshot would find them all. The last one is completely useless.

---

### Post by monkeybrain20122 on 2018-08-25
> **Dennis N said:**
> Might be for the same reasons discussed in this thread:
[https://ubuntuforums.org/showthread.php?t=2358715](https://ubuntuforums.org/showthread.php?t=2358715)

Hi, sounds like it, will take a look. Thanks.

---

### Post by monkeybrain20122 on 2018-08-26
Hi Dennis N,

Following your ink I went to [https://askubuntu.com/questions/706528/qt-apps-stopped-inheriting-gtk-themes](https://askubuntu.com/questions/706528/qt-apps-stopped-inheriting-gtk-themes), the answer there works! Now all qt applications have a search option that works well just like in my second screenshot (no more screenshot 4) 

Though with gtk applications the search is still stupid as explained in post #7, but I basically started this thread because of qpdfview and this is fixed with the link above. so I am marking this thread as solved.

Thanks for the help!

---

