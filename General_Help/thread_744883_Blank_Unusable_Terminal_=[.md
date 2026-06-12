---
title: "Blank Unusable Terminal =["
date: 2008-04-04
forum: General Help
---

### Post by TidusBlade on 2008-04-04
Just yesterday night, I opened up a terminal window and it just stayed blank... I couldn't do anything, whatever I type just doesn't do anything. I know it's hard to explain so here's what my terminal looks like now.
[IMG]http://img507.imageshack.us/img507/8274/snapshot1nj3.png[/IMG]

Im using Linux Mint KDE, and I tried to rename ~/.kde/ and restart X, but same problem :(
When I log in as root, the terminal works properly.

Hope someone can help me :D
Thanks!

---

### Post by ajmorris on 2008-04-04
hi there,
do you have access to another CLI, like xterm or the gnome terminal? You could see if konsole is at fault. Also, do TTY sessions as your user work?

AJ

---

### Post by matey3 on 2008-04-04
hi can you type gnome-terminal and see if you get a new screen with the prompt?

---

### Post by mali2297 on 2008-04-04
My guess is that someone has messed with your .bashrc file. Open a file manager, view hidden files, locate .bashrc and rename the file. Then try opening a terminal window again.

If this works, please post the content of the old .bashrc.

---

### Post by TidusBlade on 2008-04-05
All terminals were unusable and looked the same :S

Anyways I did solve it, after opening ksysguard, turns out my CPU usage was at 100% and all the bash processes were using up tons of CPU power, so I just restarted the computer and everything worked like a charm! I did try to killall bash but it didnt let me.

Thanks every for the replies too =]

---

### Post by mali2297 on 2008-04-05
So that opening message was something that you had set yourself? Fortune cookie?

---

