---
title: "[SOLVED] Nautilus Broken?"
date: 2008-06-23
forum: General Help
---

### Post by Plasma_NZ on 2008-06-23
have posted this in the x86_64bit sections too, but i feel this isnt just 64bit related..


Ok here's the issue, not sure what happened to cause this..


Ok, if i have say a folder with a tar.gz file i used to be able right click and choose extract-here - its gone, and double clicking on it doesnt work either... but i can still tar.gz from terminal..

Secondly, jpg files, i cant double-click them and have them open in a viewer, it tries to open them in text-editor of sorts.. but i can view them if i open a image-viewer then browse to the jpg etc..

Any ideas how i can resolve this to back how it was previously.?

---

### Post by plucky on 2008-06-23
> **Plasma_NZ said:**
> have posted this in the x86_64bit sections too, but i feel this isnt just 64bit related..


Ok here's the issue, not sure what happened to cause this..


Ok, if i have say a folder with a tar.gz file i used to be able right click and choose extract-here - its gone, and double clicking on it doesnt work either... but i can still tar.gz from terminal..

Secondly, jpg files, i cant double-click them and have them open in a viewer, it tries to open them in text-editor of sorts.. but i can view them if i open a image-viewer then browse to the jpg etc..

Any ideas how i can resolve this to back how it was previously.?

1) You could try and reinstall "Archive manager" in Add/Remove or ```
sudo apt-get install file-roller
``` from a terminal.

2) Select a jpeg file and right click on it and select open with "Image viewer". After this all jpeg files will open with Image viewer.


Good Luck

---

### Post by Plasma_NZ on 2008-06-23
> **plucky said:**
> 1) You could try and reinstall "Archive manager" in Add/Remove or ```
sudo apt-get install file-roller
``` from a terminal.

2) Select a jpeg file and right click on it and select open with "Image viewer". After this all jpeg files will open with Image viewer.


Good Luck

Jpg's work again now, thanks...

As for the right-click option of "extract-here" on a tar.gz file... didnt work... stumped... dont want to have to use terminal each time

---

### Post by plucky on 2008-06-23
> As for the right-click option of "extract-here" on a tar.gz file... didnt work... stumped... dont want to have to use terminal each time



What options do you get when you right click?

Do you get "Open with other Application"?

Did you try to reinstall "Archive Manager" using ADD/Remove?

Open Synaptic Package Manager and search for "file-roller",and see that it is installed.If it is installed,try removing it and then reinstall.

---

### Post by Plasma_NZ on 2008-06-23
> **plucky said:**
> What options do you get when you right click?

Do you get "Open with other Application"?

Did you try to reinstall "Archive Manager" using ADD/Remove?

Open Synaptic Package Manager and search for "file-roller",and see that it is installed.If it is installed,try removing it and then reinstall.

Have reinstalled both, still missing the "extract here" option, it seems to be causin problems with other files aswell..

Could this be python related perhaps ?

is the only thing i've installed recently..

---

### Post by Plasma_NZ on 2008-06-23
if i download a avi file now - and double click it, it reckons its a executable, but any previous avi file since this issue arising opens normally with vlc... 

if i click on the avi it reckons is a executable and check its properties - it says its open with vlc - so im kinda stumped... something seems messed up somewhere...

seems to be a migrating problem..

---

### Post by Keith Hedger on 2008-06-23
I had a similar problem when i installed wine a number of file types wouldn't open when double clicking them it turned out that the default application had been changed so i just right clicked and went to properties->open with and reset the default "open with" app

---

### Post by Plasma_NZ on 2008-06-23
Tried that, hasnt worked... somethings really wrong, but i dont want to reinstall..!

Man... im completely stumped..

---

### Post by Plasma_NZ on 2008-06-23
It seems as though extention's manager or something like that has messed up what extentions opens with..

If i tell avi to open with vlc, it opens the new .jpg files with vlc, which is really annoying...

---

### Post by Plasma_NZ on 2008-06-24
bump...

---

### Post by Plasma_NZ on 2008-06-25
Well im at my witt's end, seems to be gettin worse... if anyone has any ideas do step forward..

---

### Post by VMC on 2008-06-25
in your home directory there's ".nautilus" directory. You could try moving that to some tmp dir and try reinstalling again. Also, create a new user and see if that solves your problem. If it doesn then something in you home dir's maybe the culprit.

---

### Post by Plasma_NZ on 2008-06-25
> **VMC said:**
> in your home directory there's ".nautilus" directory. You could try moving that to some tmp dir and try reinstalling again. Also, create a new user and see if that solves your problem. If it doesn then something in you home dir's maybe the culprit.

Will give that a whirl..

---

### Post by Plasma_NZ on 2008-06-25
> **VMC said:**
> in your home directory there's ".nautilus" directory. You could try moving that to some tmp dir and try reinstalling again. Also, create a new user and see if that solves your problem. If it doesn then something in you home dir's maybe the culprit.

Thanks VMC.. problem fixed by deleting nautilus folder and reinstalling nautilus - plus its data-modules.. :)

---

