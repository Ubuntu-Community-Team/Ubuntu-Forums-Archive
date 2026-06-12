---
title: "Edgy Firefox font rendering issue"
date: 2007-04-08
forum: General Help
---

### Post by lwadurnew on 2007-04-08
I've just recently installed Edgy.  I've only noticed this issue in Firefox though i suspect it may be more prevalent.  When i type text into the address bar or form fields, rendering seems proper, but when i backtrack over the text, images of the caret remain.  It looks like i have a pipe wedged between each character.  The caret images do disappear when the text is repainted.  Anyone know what the issue might be?  This is extremely annoying.  I've searched all over and ANY help would be appreciated.  Thank you. :)

---

### Post by mikewhatever on 2007-04-08
Have also experienced this, but it disappeared with direct rendering. What's the output of this command? > glxinfo | grep rendering
Also, what's you graphics card?

---

### Post by lwadurnew on 2007-04-09
$ glxinfo | grep rendering
direct rendering: No

And I'm using an NVidia GeForce Go 7.

---

### Post by mikewhatever on 2007-04-11
> **lwadurnew said:**
> $ glxinfo | grep rendering
direct rendering: No

And I'm using an NVidia GeForce Go 7.

Try installing the latest driver with envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
You should have direct rendering after it is done.

---

