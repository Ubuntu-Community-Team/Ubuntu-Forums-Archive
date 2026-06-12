---
title: "[SOLVED] adding an idividual icon"
date: 2008-07-03
forum: General Help
---

### Post by benjaminjames on 2008-07-03
hi all, so i found an icon on the web that i want to use as my default folder icon but i dont know how to set it up so that i can change all of my icons=. the only way i have found is by changing them all individually which would take ages. soed anyone know how i can do this??

---

### Post by benjaminjames on 2008-07-03
bump

---

### Post by sayakb on 2008-07-03
Which Ubuntu version? And what Icon theme are you using? Is it an icon theme that you installed later or is it one among the defaults?

---

### Post by tuxxy on 2008-07-03
replace the old icon with your new one =D

old icon depending on your current theme could be be */usr/share/pixamps* or most likely a folder in */usr/share/icons* if you have a theme installed

tux

---

### Post by benjaminjames on 2008-07-03
ok so it is a custom theme called mac for lin but when i go into my usr/share/icons folder it isnt there??? im pretty clueless about the linux filesysytem still although im getting better :) btw im using mint elyissia

---

### Post by BandD on 2008-07-04
Look in /home/*username*/.icons (it's a hidden directory, so in Nautilus hit Ctrl+H to show hidden files and folders).  Your icon theme should be in there.

Now once your in .icons you should see a Mac for Lin folder open that up.  Then you'll most likely see a bunch of folders with different sizes for the names.  You'll have to go through each of those folders' "places" folder and replace each folder icon with the icon you want to replace.  It's not so hard, but a little time consuming.

i.e. for me I navigate to /home/user/.icons/custom_set  Then I open up the 24x24 folder.  Then I open up the "places" folder.  Then I look for all the files that have the icon I want to replace and replace them with the new icon keeping the exact same filename.  I actually usually just pick one file and change it to the new icon and create soft links (right-click, create link) for the other file names.  So I have a file called 'folder.png'  I change that to the new icon but keep the 'folder.png' file name.  Then I look through the rest of the the 'places' folder and see that I have a file called 'gnome-fs-directory.png' with the icon I want to replace, so I make a soft link to 'folder.png' and rename the link 'gnome-fs-directory.png'...and so on and so on...

I hope that makes sense.

---

### Post by angry_johnnie on 2008-07-04
If you've already installed it, the it is in /home/YOU/.icons.

Otherwise, press alt + f2 and type gnome-appearance-properties.

Most icon themes are just compressed files (something.tar.gz or something.tar.bz2), and can be installed simply by dragging and dropping them onto the gnome-appearance window.

---

### Post by benjaminjames on 2008-07-14
thanks all for the help this thread can be closed

---

### Post by sayakb on 2008-07-14
Please mark the thread as solved. (Thread Tools -> Mark thread as solved)

---

