---
title: "xubuntu help"
date: 2007-11-04
forum: General Help
---

### Post by kinghippy on 2007-11-04
I installed Xubuntu on my laptop. The initial screen resolution settings were 800 by 600, and this resulted in a box with a large black border on my laptop...so I decided to change my screen resolution settings. When I went into the resolution preferences, 800 by 600 was the largest resolution available. (The only other option was 640 by 480.)

Here's the thing, I really didn't like the small box, so I decided to get creative and change it. That's when my problems started. I should mention that before I made these changes, my terminal came up just fine. In fact, I used the terminal to make the changes:  I went into my terminal as the superuser and opened xserver-xorg file, and ran it to manually change the screen resolution settings. So far, so good. When I logged back in, my screen was 1024 by 768, and all seemed well. The screen looks great, and I thought that everything was well.

Here's the problem:  Now, when I try to access my terminal, the screen flickers, and I get taken back to the login screen. It is maddening. I can't think of any way to fix the problem without using the terminal, which is where the glitch is. Does anyone have any ideas as to an easy fix to this problem, or am I pretty much stuck with having to do a reinstall?

---

### Post by bapoumba on 2007-11-04
Could you please give your video card specs?

---

### Post by kinghippy on 2007-11-04
I'm not really sure how to find that out. I'm sort of a newbie. The graphics chip says Intel 815 ... I should add that when I changed the screen resolution back to 800 by 600, the problem was not fixed.

---

### Post by vambo on 2007-11-04
A look at this might be worth it [http://ubuntuforums.org/showthread.php?t=417661]("http://ubuntuforums.org/showthread.php?t=417661")
especially post #6.
Hope this is of use.

---

### Post by kinghippy on 2007-11-04
Thanks vambo!  I tried changing the color depth to 16, but that did not fix the bug. I am going to try to download the gnome-terminal, but I will have to wait until my roommate decides to quit gaming on the laptop cable connection, and who knows how long that will be. :(

---

### Post by vambo on 2007-11-04
You could just try an xterm to see if it makes any difference - /usr/bin/xterm.
Already there - no need to download it

---

### Post by kinghippy on 2007-11-04
Thanks for the help!  That link did work, so I just made a link to it on my desktop. It's not perfect, but it works. Thanks a million.

---

### Post by vambo on 2007-11-04
Good stuff. You never know you might get to like xterms ;)
Just one thing. If everything is OK could you mark this as solved?

---

### Post by kinghippy on 2007-11-04
Sure ... how do I do that?

---

