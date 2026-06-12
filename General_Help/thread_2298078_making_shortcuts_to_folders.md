---
title: "making shortcuts to folders"
date: 2015-10-08
forum: General Help
---

### Post by matt18 on 2015-10-08
Just wondering how to make a shortcut from a folder onto the desktop. I have googled this but it seems that all the info they tell me, i cant seem to do. for example, if i right click on the foilder i want to create a short cut for, there is no make link option. i have command line options i can try but since the people i am showing this to are basic users, thats not an option at the moment haha. 

i am on ubuntu 14.04 (vmplayer) using cinnamon as my GUI. why does cinnamon not have make link option or any of my gui's?

Ps, i did find the ctrl+shift drag trick but wopuld still like the right click option to work. thanks Oh and is there a list of common hot keys for ubuntu that list items such as ctrl+shift drag? thanks

---

### Post by TheFu on 2015-10-08
$ ln -s source target

If the source is in a different directory, then the target can be left off and will be assumed in the CWD.

---

