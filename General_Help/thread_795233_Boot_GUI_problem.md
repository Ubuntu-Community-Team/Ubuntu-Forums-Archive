---
title: "Boot GUI problem"
date: 2008-05-15
forum: General Help
---

### Post by masterscoach on 2008-05-15
I need help on the Boot GUI for Hardy.  When the system begins to boot the first part (text then graphical works OK).  My problem begins when the boot reaches the place for username and password.  What I see is at that point, my screen resolution appears to go to VGA or something low and all wording is off screen.  To log into the system, I usually have to play with the tab and control keys and try to get to a point where I can log in.  There may be a consistent way to do this, but I haven't found it.  When I say I do log in, it is with a blank screen.  After this step, resolution is OK and the system runs very well.

I am running a dual core intel chip and NVIDIA video card.  I have checked to bios settings and they don't seem to be wrong.  

Any suggestions would be welcome.

---

### Post by pastalavista on 2008-05-15
In the terminal type:
```
 gksudo gedit /etc/usplash.conf
```
then set the X and Y values to the proper screen resolution for your machine. I had a similar problem (plus a very slow boot process and no splash screen) and this fixed it for me.

---

### Post by masterscoach on 2008-05-15
thanks.  I set the x to 1152 and y to 864.  Unfortunately I see no difference in how it boots up.  Its funny.  Part way up everything seems to be working fine.  I know I am having a problem when the screen goes to a blue color and the time passing icon appears in the lower right corner, partially off screen and about a dime in diameter.  After that all I get is a blue screen.  As I said before using tabs and enter I work my way into the log in.  the brown Ubuntu bar comes up next, a little off center high and to the left of center but when the screen gets to the desktop, all is well.

---

### Post by ermannobonifazi on 2008-06-02
Try setting VGA=xxx (some option here) in your boot option.
Please check this info here too: [http://www.blogmanno.com/?q=node/68](http://www.blogmanno.com/?q=node/68)

---

