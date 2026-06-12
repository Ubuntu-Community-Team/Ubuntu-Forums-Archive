---
title: "Menu bar disappeared, how do I get it back ?"
date: 2008-05-19
forum: General Help
---

### Post by cuco2772 on 2008-05-19
Hi, I'm running feisty and recently was doing something with my mouse,
I think I inadvertently dragged it somewhere and somehow my menubar at the top disappeared so now there's no way to go into my Applications menu or my
System menu. So, for ex., if I want to open a terminal window and work from the command line, I'm screwed. So now my menu bar starts with the firefox icon and everything to the right, which is only the envelope icon and the ? icon. It's weird that it only got rid of my drop down menu's and not those.
I tried making the bar smaller, but that didn't work.
Any ideas ?

---

### Post by tamoneya on 2008-05-19
hit alt-F2 and type ```
gnome-panel
```

---

### Post by cuco2772 on 2008-05-19
Thanks tamoneya for the quick reply. I tried running the gnome-panel as you said and got this message:
'I've detected a panel already running and will now exit'
Anything else I can try ?

---

### Post by cuco2772 on 2008-05-19
SOLVED: I guess all I had to do was rt click on the panel and hit 
Main Menu, then Add. I am a doofus , :lolflag:

---

### Post by tamoneya on 2008-05-19
i believe panel placement is controlled by ~/.gnome2/main.  Post that file if you could.  Since you cant get to the panel to open up home you should probably use: Alt-F2```
gedit ~/.gnome2/main
```

EDIT: I am not really sure how this config file works so if anyone else does help would be great.  I was just going to attempt to fix it by comparing to mine:```

[Placement]
Dock=FilterBar\\2,4,1,0\\LocationBar\\0,3,1,0\\ToolBar\\0,2,1,0\\MenuBar\\0,1,1,0
```
My gnome panel has one bar up top and one bar down bottom. Very similar to the defualts.

---

### Post by puifais on 2008-09-12
I have the same problem except that when I hit alt and F2, my terminal doesn't open...so I can't input the code you recommended...  Is alt-F2 suppose to open terminal?

---

### Post by johnathan12 on 2011-05-17
Right click on the bottom bar and click new panel!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 



John Hendrickson:o:p;)

---

### Post by rotten69 on 2011-07-03
Hi people,

I have the same problem on my Ubuntu system. The top bar is missing and whenever I turn my machine on and log in, I can't see the top main menu. Therefore, I open the terminal and type in  ```
 gnome-panel
``` ,so now it is activated. But, If this terminal is closed, the menu gets missing again. 

Does anyone know how to fix this?

---

