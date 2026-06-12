---
title: "GTK Broke Unity. Help me recover?"
date: 2014-02-08
forum: General Help
---

### Post by cathect2 on 2014-02-08
So, I was trying to install the Birdie twitter client. [Following their directions]("http://birdieapp.github.io/help#tocAnchor-1-1-1"), I needed to update to Gnome 3 (Gtk version to 3.10). So I did. 

The problem is that this has really broken Unity. I can't see my cursor anymore and every time I log into Unity, I get error upon error. Since I can't see the cursor, the computer is essentially worthless. I'm able to use Gnome, but don't like it. 

How can I recover Unity? Any help out there?

---

### Post by deadflowr on 2014-02-08
Your best bet is ppa-purge
You'll need to install it, can you access a terminal?
ctrl+alt+T ?
does this get a terminal
If yes then run
```
sudo apt-get install ppa-purge
```
then try 
```
sudo ppa-purge ppa:gnome3-team/gnome3
```
this should revert the packages back.
[http://askubuntu.com/questions/309966/difference-between-ppa-purge-and-add-apt-repository-r](http://askubuntu.com/questions/309966/difference-between-ppa-purge-and-add-apt-repository-r)
Hopefully that does some good, and whatever happens next can be addressed as it comes.

---

### Post by cathect2 on 2014-02-09
So, I'd already followed this advice. However, upon reboot Unity just doesn't behave. The window decorations don't function properly. I have no cursor. It's there, but it is invisible, which makes for very painful and slow work. At present, I can't get the dash to appear. I actually went back through and reinstalled the ubuntu desktop and reinstalled unity. But I have the same issue.

Any ideas?

---

