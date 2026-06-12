---
title: "keyboard layout problems involving compiz"
date: 2006-07-07
forum: General Help
---

### Post by digby on 2006-07-07
I was attempting to adjust my keyboard layout settings to get my win (super) keys to work.  In doing to, I have somehow managed to break my ctrl+alt key combo.  Both keys seem to function properly independently (i.e. I can still copy/paste w/ ctrl and open menus w/ alt), but I can't use the two together to rotate the cube in compiz.  

I tried resetting back to pc104 both in xorg.conf and under system>preferences>keyboard (where I first started tweaking and broke it).  I have tried using xmodmap to load different keymaps.  I ran dpkg-reconfigure xserver-xorg to try and reset the thing that way.  Nothing seemed to have any effect on the problem.

Then I made an interesting observation:  I don't load compiz automatically when gnome starts, and before I do, ctrl+alt+arrow keys swtich workspaces just like they should.  Also, when I run my compiz-starting script, I can (for just a brief moment) use those same keys to rotate the cube like I had previously.  But only for a second.  Then it goes back to its currently broken state.

Anyone have an idea what I should do?

---

### Post by digby on 2006-07-08
Ok - fixed... if anyone else has the same problem, here is what I had to do:

I finally tried starting compiz manually (instead of my startcompiz script) and got the following error message:```
compiz.real: water: GL_ARB_fragment_program is missing
```So I disabled the water plugin and all is well.

---

