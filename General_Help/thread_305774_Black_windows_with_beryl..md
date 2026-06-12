---
title: "Black windows with beryl."
date: 2006-11-23
forum: General Help
---

### Post by cesiel1990 on 2006-11-23
I sometimes have problems with windows going black with I maximize them or make them larger.  I've enabled strict binding.  Does anyone have any other suggestions?

---

### Post by steevk on 2006-11-23
I have no suggestions, but as a fellow Beryl user, if this happens to me, I'd like to find out how to fix it.

Can you describe the problem a bit better? What do you mean by 'black' windows? The whole window is just blank black?

---

### Post by cesiel1990 on 2006-11-24
Yes in the window, except for the top bar.  I can see the windows when they are smaller though, I have a Geforce 6100 integrated video card if that helps anyone.

---

### Post by galv on 2006-11-26
I have a nVidia 7300 and have the same problem. :(

---

### Post by SlCKB0Y on 2006-11-26
Its a known bug. wait fro nvidia to fix the GLX_EXT_texture_from_pixmap implementation in their drivers.

Or use compiz. its much quicker and I dont get the black windows.

---

### Post by patrickfromspain on 2006-11-26
> **SlCKB0Y said:**
> Its a known bug. wait fro nvidia to fix the GLX_EXT_texture_from_pixmap implementation in their drivers.

Or use compiz. its much quicker and I dont get the black windows.
is compiz still being developted? Can we use compiz without XGL? Repos please? 

Thanx!

---

### Post by SlCKB0Y on 2006-12-02
```
deb http://gandalfn.club.fr/ubuntu edgy stable dev

```

That has the most up-to-date version. Compiz is in the official repos however though.

It now has support for metacity themes, which I think is pretty cool. After installing it, you might have to reboot, I had to.

---

### Post by Yfrwlf on 2006-12-11
> **cesiel1990 said:**
> I sometimes have problems with windows going black with I maximize them or make them larger.  I've enabled strict binding.  Does anyone have any other suggestions?

I have the answer, at least it was for me.  I was looking for the same solution, came to this forum, then messed around with some settings and I now have Beryl running with several maximized windows and none of them are black!  Someone said they stuck with Compiz because it didn't have that problem, but for some reason I don't get window decorations while in it and I'm not sure how to load Compiz themes.  But that's off topic ^^

To fix it, I right-clicked on the Beryl gem and went to the "Advanced Beryl Options" section.  This is the bad part, because I'm not sure what option changed the windows from being black, so please let me know by pulling up a black window and watching it after every change.  (I'm too scared to mess with the settings now!)  I changed the rendering path to "texture from pixmap".  I changed the rendering platform to "force AIGLX".  I then changed both the binding and rendering options to XGL.  I don't know if it was a combination of these options, or one of them, but that fixed it for me!  Hope that's the answer and just not a freak occurrence.  Let me know if it works! =)

---

### Post by sque on 2006-12-11
I found a way to reproduce this bug. So I tried all your settings one-by-one and for me the Rendering Platform->AIGLX did the job. But when I maximize a window, or when a new one is created it is significant slower than using the NVIDIA platform.

ty for the guidance :)

---

### Post by Yfrwlf on 2006-12-11
> **sque said:**
> I found a way to reproduce this bug. So I tried all your settings one-by-one and for me the Rendering Platform->AIGLX did the job. But when I maximize a window, or when a new one is created it is significant slower than using the NVIDIA platform.

ty for the guidance :)

Woot!  Glad I could be of help, and yes it does seem slower for me too, but I'll take slower over not being able to view my browser windows at all (unless they're really small) any day ;)  I hope Nvidia gets to fixing their driver bug soon!

---

### Post by Yfrwlf on 2006-12-11
Off-topic again, but just think, there are thousands of users using Nvidia cards out there.  If they open-sourced their drivers, these bug fixes would get done much much more quickly I think.

---

### Post by Shiva88 on 2007-01-03
Per Yfrwlf's advice above, I was able to resolve the dark windows issue by right-clicking on the beryl applet, and going to Advanced Beryl options > Rendering Platform > Force AIGLX.  That seems to have resolved the problem perfectly for me.  I'm on a Geforce Go7200 btw.

---

### Post by 23meg on 2007-01-03
> **Shiva88 said:**
> Per Yfrwlf's advice above, I was able to resolve the dark windows issue by right-clicking on the beryl applet, and going to Advanced Beryl options > Rendering Platform > Force AIGLX.  That seems to have resolved the problem perfectly for me.  I'm on a Geforce Go7200 btw.
That unfortunately is a workaround which reduces performance.

---

### Post by Steveway on 2007-01-03
Another Good working workaround is to change your renderpath from TFP to Copy in the advanced options in beryl-manager.

---

### Post by jonah1980 on 2007-01-06
take a look at this guys: [http://www.ubuntuforums.org/showthread.php?t=295689](http://www.ubuntuforums.org/showthread.php?t=295689)

---

