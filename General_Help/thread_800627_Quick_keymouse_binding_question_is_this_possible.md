---
title: "Quick key/mouse binding question: is this possible?"
date: 2008-05-20
forum: General Help
---

### Post by Tken on 2008-05-20
Can anyone think of a way to bind a keystroke combination to be used only when both the left and right mouse buttons are held down together?  My intention is for these two buttons to activate Compiz's cube rotation.

So far, I've tried to get Compiz's settings manager to bind to the two mouse buttons at once (of course), but that wouldn't take, even if I typed it in manually.  I've also tried both xbindkeys and btnx (which I use for all my other bindings), but neither seems to have this functionality.  

I'm still very new to Ubuntu (installed two days ago), so that's all I know of to try.  But I'm sure you guys can think of some more ways to go about it.  :)

Thanks in advance.

---

### Post by sdennie on 2008-05-20
I think that by default Ubuntu considers pushing both buttons is the same as pushing the middle button (used to be very important to have a middle button on Unix systems).  I would see if you can find a way to bind your action to button 3 or 4 and see if that helps.

---

### Post by Tken on 2008-05-20
Nope -- I already have the middle button bound to close the current window, but left+right clicking doesn't do anything.  And that's with "Emulate3Buttons" set to "true" in xorg.conf, which it sounds like would be the relevant option (though I have no idea whether btnx overwrites that).

It seemed like my best shot was with Compiz's bindings...I thought something like <Button1>Button2 or Button1Button2 would have the correct functionality, being so similar to something like <Super>Button1, but alas, Compiz doesn't recognize either as a valid binding.

---

