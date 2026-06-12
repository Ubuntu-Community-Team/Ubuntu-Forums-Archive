---
title: "can't move menu items"
date: 2016-01-20
forum: General Help
---

### Post by rebeltaz on 2016-01-20
Running Ubuntu 14.04LTS with gnome-session-fallback. I can go to Applications>System Tools>Preferences>Main Menu and I can edit properties, etc... but I cannot move a menu item (i.e. program) from one group (i.e. sub-menu) to another. For instance, there are several programs listed under Other that I would prefer listed under Electronics. I tried reinstalling alacarte, but that didn't help. Any ideas? Thanks.

Just to add a little more information, I have renamed the ~/.config/menus folder to menus.bak (to force menus to be recreated) and I have installed MenuLibre as well. Still cannot move items like I used to could in alacarte. I can move items around under MenuLibre (it's a pain in the with the [up] and [down] functions, but it can be done) but I CAN'T SAVE IT! The [save] button is disabled. I have tried to run both alacarte and MenuLibre as root (with sudo) but nothing changes - other than the menus.

I know my issues are usually off the wall - otherwise I could figure them myself - but every once in a while I get the feeling I'm being ignored on here :( I'd settle for a "you're screwed dude" right about now! Thanks....

For the past two and a half hours I have been searching the net for an answer to this. Either I am not wording it right, or the answer does not exist.

Let's try this then... how do I edit the menus to where I can move program X from Applications>sub-menu Y to Applications>sub-menu Z?

GUI or not... I really don't care anymore. 

I have looked in ~/.config/menus; ~/.local/share/applications; /usr/local/share/applications; and /usr/share/applications ... I cannot see half the programs that show up in the Applications menu nor can I see anything that relegates program X to sub-menu Y. 

Please...tell me what I am missing!!!!!!!

---

### Post by deadflowr on 2016-01-26
Change the category selection directly in the applications .desktop file.

Example, open gedit navigate to the usr share applications directory
open a familiar application and then change where it says the Categories= part of that from what it is to something else.
Then save and close.
(You would need root to edit those as is, but you can also save them in your user's home folder, in the hidden .local/share/applications folder;
no root required to do that)

you probably need to logout to make the changes appear.

---

### Post by v3.xx on 2016-01-26
Since you are running the Fallback/Flashback desktop, I would like to add that the Mate desktop may be more to your liking.  Much more flexible than the Flashback desktop, like 10.04 was.  Alacarte works like it should.  I still have 12.04 Fallback installed as backup, but Mate is its replacement.

Just a thought :)

---

### Post by rebeltaz on 2016-01-26
The files under /usr/share/applications aren't showing up as .desktop files... they don't have any extension at all. That is what threw me. I never thought to try to gedit one of those. I was able to modify the categories that way. THANK YOU! Still wish I could do this GUI - or at least know why I can't - but... I'll settle for I can!

> **v3.xx said:**
> Since you are running the Fallback/Flashback desktop, I would like to add that the Mate desktop may be more to your liking.  Much more flexible than the Flashback desktop, like 10.04 was.  Alacarte works like it should.  I still have 12.04 Fallback installed as backup, but Mate is its replacement.

Just a thought :)

You know... I think you suggested that before for a problem I had with my gf's computer, adn I did install that on hers. It looks good, but I think things worked a little bit differently. If I keep having trouble, I may have to try that. Thanks!

---

### Post by v3.xx on 2016-01-26
Yes, that sounds like something I would do :D  Good luck

---

