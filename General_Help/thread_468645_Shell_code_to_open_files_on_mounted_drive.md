---
title: "Shell code to open files on mounted drive"
date: 2007-06-09
forum: General Help
---

### Post by utopial on 2007-06-09
Hi,

I was wondering if anyone could tell me how to open, via terminal, folders and files from the harddrives i have mounted? i can open them manually, but need to know the shell code.

i want to open a rar file (ive installed winrar thru wine) from a folder called 'study' on hda1
ive scoured google and tried heapsa commands like:
gnome-open /dev/media/hda1/study/file.rar
or
gnome-open /hda1/study/file.rar
but nothing works

I'm new to linux and don't know much shell code and cant find many good resources for it either.
I appreciate any help
thanks

---

### Post by Dekunuts on 2007-06-09
maybe you will find more information if you try searching 'using bash shell' or something.

you have to enter the program that you want to use to open the file. example :

stefan@Athlon:~$ ls
Archive  Debian Packages  Drawings  Nintendo  Ripping    Thema's   Video
Blender  Deku4            Images    N-Only    School 6e  Torrents  woorden.odt
Coding   Desktop          Music     Pictures  Shared     Ubuntu
stefan@Athlon:~$ cd Shared
stefan@Athlon:~/Shared$ ls
S11E02.avi
stefan@Athlon:~/Shared$** vlc S11E02.avi**
VLC media player 0.8.6 Janus

and if you just want to open a rar file, you can do that without wine. if you type 'sudo apt-get install unrar' in a terminal, a package will be installed for unrarring. Then you just have to double click the .rar file and it will open.

that should help you;)

---

### Post by PointSource on 2007-06-09
There is no such thing as "gnome-open", as you've already discovered.
I would suggest using a command like this:
```
wine C:\\Program\ Files\\WInRAR\\WinRAR.exe Z:\\media\\hda1\\study\\file.rar
```
You will probably need to edit those paths first.

However, you can also install unrar and use that to unzip your files.

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
^^ These would give you a better idea of what's happening in commands

Apologies if I appear to be treating you like a total n00b.

---

### Post by utopial on 2007-06-09
hey guys, thanks for the info
i am a total noob so no worries

i tried the wine code you posted and it opened winrar but not the file (which was located at the directory you specified)

i then installed unrar
this piece of code succesfully opened up my hard drive folder
```
gnome-open /media/hda1/
```

this piece of code failed to work:
```
gnome-open /media/hda1/study/
```
'Error showing url: The location or file could not be found.'

Dekunuts, correct me if i'm wrong but i think you can use gnome-open to open the program for you with whatever the default program is in ubuntu for that file type. the code you posted works too but allows u to be more specific about the program you want to use

anyway, i guess the code i should use will be like:

gnome-open /media/hda1/study/file.rar
or
unrar /media/hda1/study/file.rar


but neither works. the main problem is working out what the command is for the external media directories.

---

### Post by utopial on 2007-06-09
mofo
at the end  of all of this, i have learnt 1 thing:

shell code is CASE SENSITIVE!!!
dammit
'gnome-open /media/hda1/**S**tudy/file.rar' works fine

thanks anyway

---

### Post by strabes on 2007-06-09
By the way, why are you usnig winrar through wine? Just install the package "unrar-free"

---

