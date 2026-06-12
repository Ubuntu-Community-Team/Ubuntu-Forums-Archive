---
title: "Fluxbox iDesk question"
date: 2006-08-01
forum: General Help
---

### Post by seshomaru samma on 2006-08-01
I want to use Fluxbox but must have desktop icons
I downloaded iDesk which suppose to help me create them but :
```
sesho@ubuntu:~$ idesk
 Idesk starting in :0.0
[idesk] Background's file not found.
[idesk] Background's source not found.
Error: you have to create the .idesktop dir on your HOME!!
```

:confused:

---

### Post by Tomosaur on 2006-08-01
Been a while since I used fluxbox, but to make your .idesktop directory:

Open up a terminal.
Type 'mkdir .idesktop'

I think idesk will automatically populate that folder, but I'm not entirely sure.

---

### Post by seshomaru samma on 2006-08-01
I think we are getting somewhere , but still....:
```
sesho@ubuntu:~$ mkdir .idesktop
sesho@ubuntu:~$ idesk
 Idesk starting in :0.0
[idesk] Background's file not found.
[idesk] Background's source not found.
Loaded default file: /usr/share/idesk/default.lnk
Can't load: /usr/local/share/idesk/folder_home.xpm bailing -- Idesk
Check to see if the image and path to image is valid
No Icons! Quitting.
```

---

### Post by Tomosaur on 2006-08-01
This page should help you. You can download idesktool which will allow you to create icons more easily:

[Clicky](http://users.netwit.net.au/~pursang/idesk-extras.html)

---

### Post by seshomaru samma on 2006-08-01
Thank you 
but....:
```
sesho@ubuntu:~$ idesktool
Xdialog found. So far so good..
idesk found - we're on a roll :)
Config. file  found - excellent!
sesho@ubuntu:~$
```
What now?
:confused:

---

### Post by Tomosaur on 2006-08-01
Not sure really, I seem to remember it popped up a nice little menu for you to add and remove icons. Try 'man idesktool', but don't get your hopes up. Your best bet would be to refer to that website for details on how to use it.

---

### Post by seshomaru samma on 2006-08-02
If anyone can find me a HOWTO on making icons in Fluxbox I would highly appriciate it.

Thanks....

---

### Post by BLTicklemonster on 2006-12-28
I find the lack of concise help on the topic of idesk appalling.


fbdesk, too for that matter.


Search the forums for either of them, and look at all the unresolved threads dating back for a year or so.


And there's a link posted back in august on getting idesktool. The links in that link are dead.


Is linux ready for the desktop? Why heck no, but it will be once people start answering questions concisely.

(flame me, I don't care, just so long as I can get fbdesk and idesk working)

---

### Post by Kulgan on 2007-01-11
I ljust found two links that worked for me:

This one explains the procedure on installing iDesk (I used it on fluxbox):
[http://fluxbox-wiki.org/index.php/Howto_idesk](http://fluxbox-wiki.org/index.php/Howto_idesk)

but you should copy the config file from here:
[http://idesk.sourceforge.net/wiki/index.php/Idesk-usage](http://idesk.sourceforge.net/wiki/index.php/Idesk-usage)

remember to edit the background paths.

---

### Post by bodhi.zazen on 2007-01-11
Never Fear, Bodhi's here !!

Fluxbox Rocks !!!!!

Easiest way to iconify fluxbox it with rox, AKA "Fluxrox"

Of course you can just install Fluxbuntu.

If you prefer to add rox on your own, here's how:

[How to ROX](http://community.fluxbuntu.org/index.php?&topic=78.0)

---

