---
title: "[SOLVED] Couldn't display &amp;quot;/usr/share/fonts/truetype&amp;quot;."
date: 2007-03-02
forum: General Help
---

### Post by IanVonSpeedfreak on 2007-03-02
Okay so I'm obviously new here and in need of help.
I wanna make sure you guys know I've been figuring a lot of things on my own up until now searching this forum.  So I did try to find an answer to this question already, but couldn't really find anything like it (probably because no one else was nearly foolish enough to make the same mistake).  Anyway, I just tried to install some new fonts, but instead of just using the su command to move them, I thought I would just *temporarily* change the permissions of the truetype folder (yeah, dumb, I know).  I thought dragging and dropping would be faster than using su to move all the font files, and it was, I acutally changed the /fonts/truetype directory to being completely open using chmod 777.  Problem is, I didn't realize just how the numbers for changing permissions worked, so I attempted to change it back using chmod 644, which, of course, stopped my programs that used the font folder from accessing it.  I've been trying to figure out just how to fix it all ever since (even looking up what the numbers do), but I've only been able to gain access to the font folder, I, and nothing else for that matter, is able to access truetype, even after using terminal to change permissions.  Please help, I don't really know what's going on.  If you think I'm leaving out any necessary details, I'll be sure to tell you.  Thanks in advance.

---

### Post by dcstar on 2007-03-02
> **IanVonSpeedfreak said:**
> 
......I thought dragging and dropping would be faster than using su to move all the font files, and it was, I acutally changed the /fonts/truetype directory to being completely open using chmod 777.  Problem is, I didn't realize just how the numbers for changing permissions worked, so I attempted to change it back using chmod 644, which, of course, stopped my programs that used the font folder from accessing it. 
......

My /usr/share/fonts directory is owned by root and is 755 (drwxr-xr-x ).

---

### Post by IanVonSpeedfreak on 2007-03-02
Thank you very much.  This time I just decided to reinstall the fonts (my browser closed and wouldn't reopen after a final mishap with the fonts), but I appreciate your reply, I'm certain I will need that information again.:)

-er, correction, I *still* had to reassign the actual font folder back to root, so yes, this knowledge was extremely important, thank you.

---

