---
title: "global Xmodmap not working"
date: 2007-05-28
forum: General Help
---

### Post by JohnBortion on 2007-05-28
Before I upgraded to Feisty Fawn, I was able to make a global Xmodmap file and place it in /etc/X11.  Now it doesn't seem to be working.  I've also tried putting it in my home directory.  I'm using Xubuntu.  Thank you.

---

### Post by RedSquirrel on 2007-05-28
I've always used the local one. I'm using gdm, and /etc/gdm/Xsession has lines to load ~/.Xmodmap.

You probably have to add a line to deal with /etc/X11/Xmodmap, something like:

```
[ -f /etc/X11/Xmodmap ] && xmodmap /etc/X11/Xmodmap
```Here is a guide I've looked at some time ago. It refers to KDE, but one can make the necessary adjustments. 

[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

There are probably a few more out there... good luck. :)

---

### Post by JohnBortion on 2007-05-28
Thank you.  X should read Xmodmap if it's in /etc/X11 but it does not.  I've added my script to the xfce startup in 'Autostarted Applications'.   More and more I'm convinced that if I want things to work, I have to roll my own Linux distribution, even though it would waste considerable time and energy.  I wish those who make Linux distributions would have the know how to do the simple things.

---

### Post by JohnBortion on 2007-05-29
In that last message, I sounded a little coarse.  In fact I didn't even know I had posted it.  This was from a conversation I had on IRC with a very kind person from #xubuntu.  I thank you for your help.  I would not be using Xubuntu if I didn't think it was the best Linux Dist I have ever used.  Not to mention the quality people I've encountered so far who are also using this dist.

This is the simple script I've added to the 'Autostarted Apps' or whatever:

#!/bin/sh
xmodmap /etc/X11/Xmodmap

I still don't know why X doesn't read it like it used to.  It just changes the control key to that it makes it easier to use emacs and the command line so that my pinky won't get worn out.

---

### Post by RedSquirrel on 2007-05-30
Yeah, I find it surprisingly straightforward to get most things working in Ubuntu. It really doesn't take me very long to go from a blank hard drive to a functional system. That's one of the many things I like about Ubuntu.

I'm not sure why it's no longer loading the global Xmodmap, but at least there are a number of simple solutions to the problem. 

It can be frustrating when little things suddenly stop working like that, but I am always delighted when I can find a solution. :)

---

