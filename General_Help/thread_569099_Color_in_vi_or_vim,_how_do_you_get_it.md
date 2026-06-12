---
title: "Color in vi or vim, how do you get it?"
date: 2007-10-06
forum: General Help
---

### Post by peterv6 on 2007-10-06
I just finished installing the KDE desktop and when I used the vi editor in a terminal window, there was no syntax coloring.  Can anyone give me simple directions on how to turn that on?  Also, 3 things I'd like to install in KDE are the Gnome terminal and Gedit, along with whatever the filemanager (I can't recall the name right now) from Gnome.  Is that possible, or would I have to install the entire gnome desktop?
Thanks....

---

### Post by Lord Illidan on 2007-10-06
First, I'd recommend installing vim-full from a terminal.

```
sudo apt-get install vim-full
```Then, to get syntax colouring, just type <colon>syntax on ..eg.

```
:syntax on
```You can install gedit and gnome-terminal, just use synaptic..EDIT - in your case, adept/apt-get. It will, however, neccessitate downloading lots of gnome files..

---

### Post by hardyn on 2007-10-06
or make a '.vimrc' file in your user directory.

and add 'syntax on' to the first line.

---

### Post by peterv6 on 2007-10-06
Thank you both!  Your answers were just what I was looking for!

---

### Post by peterv6 on 2007-10-06
Sorry, I forgot, I've got one more, do you know how to change the syntax colors?

---

### Post by Lord Illidan on 2007-10-06
Try googling :P

[http://vim.sourceforge.net/tips/tip.php?tip_id=53](http://vim.sourceforge.net/tips/tip.php?tip_id=53)

---

