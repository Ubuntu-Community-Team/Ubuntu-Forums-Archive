---
title: "Stupid WINE problem"
date: 2007-09-19
forum: General Help
---

### Post by yme on 2007-09-19
Hey,

I've got a WINE problem if anyone can help (and don't suggest Alcoholics Anonymous!). It is very stupid but here goes ...

I want to use various programs that are available only for Windows (the OED CDROM, a program that runs my partners organizer and MakeTorrent). I installed WINE and started by trying to installl MakeTorrent.

I downloaded it, clicked on it and there is now a folder wine/drive_c/Program Files/Maketorrent 2/ which contains maketorrent.exe. I now want to try and move to folder Maketorrent 2 in order to be able to type 'wine maketorrent.exe' and get it going. Everything goes OK when I cd .wine and cd drive_c but it refuses to recognize cd Program Files. I tried with / before it, cutting and pasting from a screen after I had ls the contents, etc. But nothing works!

Stupid thing is when I am in .wine and type the name of any other folder, such as cd windows, this works! What is wrong?

yme

---

### Post by 505 on 2007-09-19
Escape the space with a \, so you have to type
```
cd Program\ Files
```

---

### Post by yme on 2007-09-19
Cheers! That seems to work. I have never heard of the use of this character before \ 

I am still very confused as to when I need to put / before a dierctory when using cd. There seems to be no standard convetion and I just get it by trial and error.

Btw, I did try to navigate to the folder in graphical mode and click on maketorrent.exe but it said there was no program to open it. Surely wine should kick into action?

Thanks again,

yme

---

### Post by Zaneyard on 2007-09-19
> **yme said:**
> Cheers! That seems to work. I have never heard of the use of this character before \ 

I am still very confused as to when I need to put / before a dierctory when using cd. There seems to be no standard convetion and I just get it by trial and error.

Btw, I did try to navigate to the folder in graphical mode and click on maketorrent.exe but it said there was no program to open it. Surely wine should kick into action?

Thanks again,

yme

the windows standard for directories is \
ex C:\program files\application
linux instead uses /
ex /home yeah you get the idea

---

### Post by Zaneyard on 2007-09-19
as far as wind goes
cd to the directory with the .exe in it
then type
wine maketorrent.exe
i think that should work, someone correct me if i'm wrong

---

### Post by anaconda on 2007-09-19
cd Program\ Files
works, but another  (easier?) posibility is to use:
```
cd "Program Files"
```
which works in windows too.

---

