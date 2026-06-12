---
title: "Why does my capslock light randomly start blinking?"
date: 2014-08-17
forum: General Help
---

### Post by josephellengar2 on 2014-08-17
Hi. For the last few days, my capslock light has started to flash for no apparent reason. It's not a kernel panic-- the computer still works and doesn't lock up. It doesn't seem to have much pattern. Sometimes it doesn't stop blinking until I restart the computer or put it to sleep and wake it back up, and sometimes it stops if I wait a few minutes. I am fairly but not 100% sure that the computer is not overheating.

Any ideas?

Thanks!

---

### Post by tgalati4 on 2014-08-17
Try cleaning out the keyboard with compressed air.  Does the light correspond with using the Caps key?  Does it stay on if you hold the Caps key down?  Check for keyboard errors.  Open a terminal:

```
dmesg | tail -100
more /var/log/Xorg.0.log
```

If this is a laptop, you might need to reseat the ribbon cable that connects the keyboard.  Not an easy task.

---

### Post by josephellengar2 on 2014-08-17
Looks like I was probably wrong. All of the messages in my log files wer about the computer overheating. It makes sense since I've been encoding video for a few weeks (it is a laptop) but, on the other hand, today is the first time I've seen this. Not sure why it would only start blinking now.

I have already checked the ribbon cables and I disabled the caps lock key a while ago, so pressing it does nothing. Well, at least it's not kernel panics. 

Thanks!

---

