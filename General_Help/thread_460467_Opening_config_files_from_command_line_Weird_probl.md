---
title: "Opening config files from command line? Weird problem!"
date: 2007-05-31
forum: General Help
---

### Post by NikoKun on 2007-05-31
I've got a bit of a weird problem...

Whenever I try to load ANY file using gedit or the like(other editors too), from the command line... It always comes up blank, like the file doesn't exist... This happens whether I'm root or normal user.

for now, I solve it by opening gedit as root from the command line, but then manually clicking Open, and finding the file I want.

For some reason, I just can't tell it to open the files from command line... =/  wtf???

Anyone know how to fix that... it's happened on 2 machines, straight from installing ubuntu.

For example:
If I type "sudo gedit /ect/fstab"
It opens a blank nothing... So i have to click Open (then it says File or folder not found)  and I have to manually point it to the file.

Same thing if I just use gedit with no sudo... and if I try to open for example grub menu.list... This problems seem to happen for everything... @_@

And Like I said, this happens on 2 different machines, both have fresh installs of Ubuntu 7.04.

Anyone know what I can do?

Thanks in advance! ^_^;

---

### Post by coffeecat on 2007-05-31
> **NikoKun said:**
> If I type "sudo gedit /ect/fstab"
It opens a blank nothing

Whenever I get a blank text editor from the command line I know I've made a typo in the file name or path. I think that's maybe what you are doing. Have a look at the part of your post I've quoted, The file is /etc/fstab. If you type /ect/fstab, gedit wil make a file /ect/fstab, because there isn't one already, and this will be empty - or blank - of course.

---

### Post by NikoKun on 2007-05-31
> **coffeecat said:**
> Whenever I get a blank text editor from the command line I know I've made a typo in the file name or path. I think that's maybe what you are doing. Have a look at the part of your post I've quoted, The file is /etc/fstab. If you type /ect/fstab, gedit wil make a file /ect/fstab, because there isn't one already, and this will be empty - or blank - of course.

OH MY GOD... I feel dumb... XD

Thanks.. yah... for some reason my my hand has a tendancy to type ect instead of etc... -_-

Thank so much... that takes a major confusion off my mind!

---

### Post by coffeecat on 2007-05-31
No worries. We all do it! :wink:

---

