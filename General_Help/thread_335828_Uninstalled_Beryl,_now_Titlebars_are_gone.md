---
title: "Uninstalled Beryl, now Titlebars are gone"
date: 2007-01-10
forum: General Help
---

### Post by dmfrey on 2007-01-10
All,

I thought I would give Beryl a try and really liked it.  I was experiencing too many crashes, so I decided to remove it.  When I originally installed Beryl, I followed the NVidia installation for Edgy on the Beryl Wiki.  This appeared to work successfully.

Now that I have removed Beryl, the window manger cannot render the screen correctly.  By the way, this is only for my account, I have checked my wife's account and her's appears to be unaffected.  Basically, what I am seeing when I log in is some bogus session gets restored (opens my home folder view, a terminal and the session manager).  I cannot switch between windows (by clicking or alt-tab).  The windows do not have titlebars or any of the buttons usually on them.  All the windows are stacked in the upper right corner, overlaying the menu area so they have to be closed before I can use a menu or panel icon.

I would really appreciate any suggestions.  If there is anything further I can provide, please let me know.

---

### Post by llamakc on 2007-01-10
Start a Terminal and type:

metacity --replace &

---

### Post by dmfrey on 2007-01-11
Thank you very much.  That solved the problem.  I really appreciate your help.

---

### Post by Choad on 2007-01-11
as an aside, you can leave beryl, and use metacity by default, leaving you the option to play with beryl whenever you feel like it, and also to check out stability improvements when automatic updates kick in for it :) 

on the beryl manager, just go to "select window manager"

---

### Post by dmfrey on 2007-01-11
I will keep it around, but I need to find a new way to install it.  I followed the NVidia setup on the Beryl wiki, but I am not sure that is the correct option.  That option added a new nvidia repo that didn't seem to play nice with the other repos, eventually sending me an update that removed the nvidia-glx package.  I do have an nvidia card, I am just not sure if I needed to install the other nvidia driver in the wiki instructions.  If you have any suggestions, I will surely welcome them.

---

### Post by darkROAM_1 on 2007-01-21
I know this is a week old but, I had a similar need for this command. I was playing around w/ Beryl and after a few hours, it started slowing down and it removed itself? Weird. Meh, i'll play w/ it more once it becomes a bit more stable and I get my computer a bit more setup.

---

