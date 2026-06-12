---
title: "Serious problems after reboot when installing Awn!!!"
date: 2008-06-28
forum: General Help
---

### Post by djnapster on 2008-06-28
Hi,

This morning i installed Compiz-fusion
now I've had just installed the Awn dock 

i followed this 'tutorial':

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

somewhere on the middle of the page there is a tip 3.
that says how i can erase the default menu bars of ubuntu.

well i did that, but i think i did something wrong.
i've also set the Awn dock as auto start up task.

well than after a reboot, i logged back in and my desktop was totally empty, no menu bars, no awn, no icons only my default desktop background.

i hope im not in deep ****, because the awn bar was the last thing i needed. i transfered al my files from my NAS which took very long :)

could i repair it by booting with live cd!?

PLEASE HELP! thx,
Bye

---

### Post by djnapster on 2008-06-28
or could i acces the terminal with a keyboard shortcut?

thx

---

### Post by el-mar01 on 2008-06-28
Can't you just run ALT - F2 and then type in gnome-panel ?? And then re-add the Gnome Panel to the sessions list ??

EDIT: Just add the Gnome main Menu to the panel after you run gnome-panel then through the menu you get to the sessions dialog box.

---

### Post by djnapster on 2008-06-29
Thanks for your reply, 
but when i press alt + f2 nothing happens,
it looks like my computer keeps hanging after logging in.
altough i could move the mouse.

is there any other option to go back to my previous settings?

thx,

---

### Post by Sam Lars on 2008-07-05
I have the same issue that you have.  It's due to the removal of gnome-panel, and it takes the Alt+F2 dialog with it.  You can do Ctrl+Alt+F1 to get to a terminal.
I'm searching for how to remove gnome-panel and not kill gnome... which is how I found this thread...

---

### Post by carlinuxlearner on 2008-07-10
@ djnapster

1. Press Ctrl+Alt+F1
2. Login with your user name and password
3. Type "gnome-panel" (without the quote marks) and hit enter
4. Press Ctrl+Alt+F7 
Now you should be back in the GUI and the gnome-panel should be running. Next just add "gnome-panel" back into the sessions list and all should be working. 

If anything does NOT work or if you don't know how to add it to the session list then just ask here.

C@RL

---

