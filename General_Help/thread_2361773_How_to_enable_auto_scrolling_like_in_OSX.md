---
title: "How to enable auto scrolling like in OSX"
date: 2017-05-20
forum: General Help
---

### Post by mikewiz38 on 2017-05-20
I came from OSX over to Ubuntu a month or so ago.  In OSX, there was this feature that if you scroll in a window quick enough with a touchpad, it will keep scrolling but at a slower pace.  I really don't know what they called it but it's a nice feature to have.  


Is there something equivalent in Ubuntu that I can enable so that I can replicate this behavior?

---

### Post by &amp;KyT$0P# on 2017-05-20
It seems like you're describing something that has always "just worked" for me in Ubuntu.  I use two-finger scrolling on the touchpad.  When I scroll quickly, it keeps scrolling, gradually decelerating, after I stop touching the touchpad.

If that's not what you have in mind, can you please explain more?

---

### Post by ajgreeny on 2017-05-20
Not sure if this will help you but in a web browser (both firefox and chromium) a middle click with a mouse button enables autoscroll and by moving the arrow or cursor either up or down, the further you move the cursor the faster the autoscroll, so I assume whatever simulates middle click on a touchpad will also do the same.

This does not work in other applications, eg LOffice, where a middle click just pastes whatever is in the clipboard buffer.

---

### Post by mikewiz38 on 2017-05-31
> **halogen2 said:**
> It seems like you're describing something that has always "just worked" for me in Ubuntu.  I use two-finger scrolling on the touchpad.  When I scroll quickly, it keeps scrolling, gradually decelerating, after I stop touching the touchpad.

If that's not what you have in mind, can you please explain more?

Interesting...  This is exactly what I want but Ubuntu isn't working like this for me.  I don't think it ever has.  I did fart around with the libinput settings a lot but I think even OOTB it didn't do it.  

Is there a particular name this function is called that I can do more research into it?  The only thing I found was called 'natural scrolling' but that's not really what I was looking for.

Thanks!

---

### Post by &amp;KyT$0P# on 2017-05-31
> **mikewiz38 said:**
> Interesting...  This is exactly what I want but Ubuntu isn't working like this for me.  I don't think it ever has.  I did fart around with the libinput s
Hmm, my touchpad uses the Synaptics driver, not libinput.  Are you able to use the Synaptics driver for your touchpad?

---

### Post by mikewiz38 on 2017-06-05
> **halogen2 said:**
> Hmm, my touchpad uses the Synaptics driver, not libinput.  Are you able to use the Synaptics driver for your touchpad?

I could use the synaptics driver....and actually prefer it.  Unfortunately though, palm detection doesn't work so my cursor goes crazy when typing.  With libinput, palm detection works, but at a cost of a cursor/pointer that doesn't move as nice.

---

