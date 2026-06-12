---
title: "[SOLVED] Oh no my Firefox Window border is gone"
date: 2008-05-13
forum: General Help
---

### Post by dstein on 2008-05-13
This seems to only be a problem in Firefox, but there is no window border. I cannot resize or move the window. It just occupies the entire screen, with no border on top. The window spans the full screen, so there is no gnome menus, which I usually have on the top and bottom of my screen. Please help. Thanks.

---

### Post by dstein on 2008-05-13
Problem solved. How? - I wish I knew. If I have the problem again or figure out why it stopped, I will post.

---

### Post by cjax1 on 2008-05-13
Sounds to me like you had Firefox in full screen mode. Press F11 for full screen, no borders, and F11 again to get out of full screen. That's my guess anyway.

---

### Post by ealott on 2008-10-08
I am experiencing the same problem in Intrepid Ibex Beta 1 64 bit.  I'll post a solution or at least what I did that resulted in firefox fixing itself whenever it chooses to do so.

---

### Post by apedraza on 2008-10-28
Help! I am having the same issue. Ibex 32 bit RC. Firefox takes out the whole screen and I can't see the gnome toolbars.

---

### Post by aktiwers on 2008-10-28
To fix this problem, make sure you have  compizconfig-settings-manager installed or install it like this:
(from Terminal type this in, Find Terminal under Applications => Accessories => Terminal)
```
sudo apt-get install compizconfig-settings-manager
```When it is done, type in:
```
ccsm
```To open the settings manager. 
Go to "General Options" and disable "Unredirect fullscreen Windows".

That should permanently fix the problem.

---

### Post by Ender Black on 2008-12-02
That didn't solve it for me.  But unchecking Workarounds did.

---

### Post by utnubuuser on 2008-12-02
cool  -- thanks

---

### Post by flerchjj on 2008-12-20
This happened to me and I did not have firefox in fullscreen mode.
Going into fullscreen mode and then coming out seemed to fix the issue.

---

### Post by kg4tah on 2008-12-21
I had the same problem with firefox going into full screen mode only with certain web sites.  I found a fix that works for me but others may not like the solution.  I went into display properties and changed visual effects to none.  That fixed the issue and I have not had any further problems with it going into full screen.

---

### Post by flanker on 2008-12-21
I'm getting the same issue every now and again. Pressing f11 a couple times restores the window. I've tried disabling "Unredirect fullscreen Windows" to no effect but disabling compiz does indeed prevent the issue occurring.

Any other ideas?

---

### Post by fooman on 2008-12-21
> **flanker said:**
> I'm getting the same issue every now and again. Pressing f11 a couple times restores the window. I've tried disabling "Unredirect fullscreen Windows" to no effect but disabling compiz does indeed prevent the issue occurring.

Any other ideas?

when it happened to me, i fixed it by first doing the f11 thing twice to get to a normal size screen... then i clicked the unmaximize button and used the cursor to resize the window to a slightly smaller size.  

close firefox, reopen firefox, maximize firefox window.

done.  problem has never come back.

---

