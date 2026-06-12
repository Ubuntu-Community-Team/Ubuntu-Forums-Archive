---
title: "Xubuntu 16.04, want to start gkrellm hidden, not showing in panel"
date: 2016-08-07
forum: General Help
---

### Post by rhauff on 2016-08-07
I am using Session and Startup > Application Autostart and have an entry that runs /usr/bin/gkrellm.  This works fine, however I always have the gkrellm entry on the panel.  How can I run it so it does not show on the panel?

---

### Post by mook765 on 2016-08-08
Right-click on the panel-item. you can see now what it is.
If it is the indicator-plugin, click properties and you will get options to hide items.
If it is not the indicator-plugin, it is a panel-applet, which can be removed clicking remove.

---

### Post by rhauff on 2016-08-08
Well, maybe my terminology is all wrong.  This is for the regular window button that shows up in the middle part of the panel for regular applicaitions.  When I right click on it the options are: Maximize, Move, Resize, Always on Top, etc.

---

### Post by mook765 on 2016-08-08
Ok, one more try...
Right-click on the panel, the small menu opens and you choose "Panel >". 
This will open a new sub-menu, here you choose "Panel preferences"
Now the panel preferences window should be open, it has three tabs, choose the Items-tab
This will display a list of all items on the panel and has buttons to add, remove and reorder the panel-items
Choose the item which you want to remove and click the "-"-button.
I don't know how this item is named in your case, as i don't have gkrellm installed, but i think you will be able to find the correct item to remove.
in the case you removed the wrong item, don't worry, you can get this item back by a click on the "+"-button, then choose from the list. 
In that case it would be an advantage if you remember the name off the just removed item...
So, that should work now, try out and good luck...

---

### Post by rhauff on 2016-08-08
That got rid of ALL the window buttons, not just gkrellm.  The Panel item is called "Window Buttons".  I am trying to have only the window button for gkrellm hidden.  I have heard of Devils's Pie and may have to give that a try.  On my old Xubuntu setup from 8 years ago I had gkrellm running hidden from panel, but cannot remember how I did it (devils pie did not exist).

---

### Post by mook765 on 2016-08-09
"Window Buttons" is not the item you should remove. this item provides adding buttons on the panel for each window which is opened, these buttons will disappear when the window are closed.
The item you should remove is also not named "Separator", "Indicator" or "Notification Area".
Did you find the list with the panel items?

---

### Post by mook765 on 2016-08-09
There is something in the gkrellm-preferences.
I think you have to check "Do not include on a Taskbar"

---

### Post by howefield on 2016-08-09
> **rhauff said:**
> ... How can I run it so it does not show on the panel?

You have probably seen this thread but it might help ?

[https://forum.xfce.org/viewtopic.php?id=6755](https://forum.xfce.org/viewtopic.php?id=6755)

---

### Post by rhauff on 2016-08-09
> **mook765 said:**
> There is something in the gkrellm-preferences.
I think you have to check "Do not include on a Taskbar"

mook765, you are relentless!  You hit the nail on the head exactly, that is what I was looking for, thank you, thank you, thank you!

It appears you also went through the effort of installing gkrellm, enjoy!

---

### Post by mook765 on 2016-08-09
You are welcome.
Please mark this thread as solved ( use the thread-tools at the top off the thread )
Nice that you let me know that i could solve this.
Indeed, i didn't install gkrellm, but did some research.
Gold luck...

---

