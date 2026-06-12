---
title: "Ubuntu 12.04 LTS No Longer Responds to CTRL+C or CTRL+Z"
date: 2014-03-28
forum: General Help
---

### Post by ayrton04 on 2014-03-28
Hello,

After running sudo apt-get update and sudo-apt-get upgrade recently, I find that I can no longer use CTRL+C or CTRL+Z in any kind of terminal window. I've tried in both gnome-terminal and in xterm, and the result is the same (i.e., absolutely nothing occurs).

Strangely, if I try pinging localhost and hitting CTRL+C, ping echos my CTRL+C key press, but doesn't kill the process! If I hit CTRL+F1 and use the command line interface only, CTRL+C and CTRL+Z work just fine. 

I'm using Cinnamon for my desktop environment. 

Any ideas?

Thanks!

---

### Post by MikRose on 2014-03-29
Re: Ctrl-C doesn't work in gnome-terminal

    try this
    ctrl+alt+F1 and type as
    Code:

    sudo apt-get install --reinstall gnome-terminal

    then press ctrl+alt+f7 to get back to GUI . and try again with Ctrl+C .

---

