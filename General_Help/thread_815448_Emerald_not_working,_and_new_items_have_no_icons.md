---
title: "Emerald not working, and new items have no icons"
date: 2008-06-01
forum: General Help
---

### Post by joey-elijah on 2008-06-01
hey all - I'm running Ubuntu HARDY 64 bit - and have posted this already in there, but thought I'd get a better response here.

Emerald is installed, but it doesn't change my window themes no matter how much i click on it. I did enter the --replace & thingy into terminal, which changed them for the duration of the session, but upon logging in - they won't change at all again.

user/bin/emerald is specified in Compiz > Effects > Window Decoration - so getting this up and working would be awesome.

Also, i have installed Firefox 32 and flock 32 however in the 'internet' menu of the, er, main menu, they have no icons or a 'window' icon. This is a) annoying cos i want the proper icons and b) it means i can't drag them to my avant dock and create a launcher. 

all help will be rewarded with a huge thanks!

---

### Post by Morty007 on 2008-06-01
I had this problem when I installed it through wubi-but did a regular install and all is fine now.

---

### Post by sayakb on 2008-06-01
Press Alt+F2 and type in
```
emerald --replace &
```
That should use Emerald. You may add this to the startup by adding it to System->Preferences->Sessions

---

### Post by sayakb on 2008-06-01
Also, goto System->Preferences->Main menu to edit/add menu items to the Main Menu.

---

