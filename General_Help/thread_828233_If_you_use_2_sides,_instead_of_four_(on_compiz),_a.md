---
title: "If you use 2 sides, instead of four (on compiz), and drag a window off the edge..."
date: 2008-06-13
forum: General Help
---

### Post by diablo75 on 2008-06-13
I don't know if this is a bug or if it's just my video card...

But I prefer to just use two workspaces, instead of 3 or 4...though I suppose I could go to three...

Anyway, when I drag a window off of the edge of the screen, the rendering goes absolutely nuts.  You can see the skydome and a mess of polygons occasionally flutter around in random bits of the screen...  I would imagine it's what my card would do if it were trying to spin the two-sided "cube" a billion times a second or something....

Does anyone else experience this if they reduce their workspace count to two surfaces?  I know how to move windows using the CTRL-SHIFT-ALT-Arrow Key, but it shouldn't require me to do that because of some odd mouse initiated behavior.

---

### Post by Ub1476 on 2008-06-13
Have you checked the zoom & speed ++ settings for the Cube settings in ccsm? Also try to deactivate some cube plugins (skydome, reflection etc), and see if they're the problem.

You can search Launchpad for the bug too (which it surely is one some way).

If you have an ATI card, those drivers aren't very good yet.

I prefer to use the "viewport" plugin instead of the Cube when I only use two workspaces though.

---

### Post by diablo75 on 2008-06-13
My card is an nVidia 5200.  It has absolutely no problems rendering when I use CTRL-ALT-Leftclick and move the mouse around.  Nor does it look bad when I just use CTRL-ALT-Left/Right.  I don't think this problem is rooted in my video card's ability to render.  Perhaps someone could help me confirm the bug, and then I/we can submit it to launchpad?

---

### Post by ravenvii on 2008-06-13
Yeah, I saw that too. My theory is that the "physics" engine cannot handle the transition of a window among a 2D surface, and thus freaks out when you try to move the window to the flip side.

In theory, there's a easy fix by simply making the window cut off at one side, and start to appear on the other, thus making it smooth.

But what do I know, I might be completely off.

---

### Post by LeoSolaris on 2008-06-13
Mine only pixalizes when I drag it from one to the other, and it only does it for a moment. I am thinking of dropping the cube and going to viewport since I only use two, and if by 'use' you mean ignore any of them but the first one. Long time windows user, still not used to it.

Leo

P.S. Here is what happens when I partly move the window off screen, and snap a picture. Same window, unmoved, just rotated the cube.

---

### Post by Happy_Man on 2008-06-13
Wait, you mean a Nvidia Geforce FX 5200? I have the same card, and no wonky drag issues occur when I do it...

---

### Post by pmaconi on 2008-06-13
My Nvidia GeForceGo 6150 does the same thing when I drag it across a two-sided cube. 3+ sides works great and manually flipping sides with the mouse or keyboard is also fine. However, I normally use 4 sides so this doesn't really affect me.

---

### Post by Forlong on 2008-06-14
Why would you want to use the Cube plugin with only two viewports anyway?

Just switch to Desktop Wall. It makes much more sense in this case.

---

