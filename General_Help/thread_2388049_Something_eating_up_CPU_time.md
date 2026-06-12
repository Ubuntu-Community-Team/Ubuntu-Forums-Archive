---
title: "Something eating up CPU time"
date: 2018-03-27
forum: General Help
---

### Post by rossignol on 2018-03-27
This started about a week ago - something running in the background is sucking up CPU time, continually slowing the computer to at least a crawl, if not stopping everything on the screen from 30 seconds to a minute or more.

How do i find what the problem is and fix it?

---

### Post by QIII on 2018-03-27
Hello!

A fairly quick way would be to run
```
top
```
in the terminal for a while and tell us what process you see consuming the most CPU resources when this starts to happen.

---

### Post by rossignol on 2018-03-27
Have tried that. Unfortunately, I cannot get the terminal to STAY on the screen for that observation, and once things lock up,the cursor is also frozen, so i cannot get it back visible!

---

### Post by QIII on 2018-03-27
What do you mean by not being able to get it to stay on the screen?

---

### Post by rossignol on 2018-03-27
As soon as i click on something (web page or anything else), the terminal window disappears.

---

### Post by QIII on 2018-03-27
Which release of Ubuntu are you using and which Desktop Environment?

---

### Post by rossignol on 2018-03-27
ubuntu 17.10, fully updated. Not sure what you mean by Desktop Enviroment, other than maybe Gnome.  The only thing I run is Firefox for mail and web browsing, and occasionally Rythmbox.

---

### Post by ansgar.snow on 2018-03-28
Next time try to login into non-xorg console with ctrl+alt+f1 then run top and kill some ps.

---

### Post by ajgreeny on 2018-03-28
You could open a terminal, right click in the titlebar and choose to always keep on top (I'm not sure what the gome terminal context menu says but it should be obvious), then when you click in the browser the terminal will stay visible.
You can resize or move the terminal to show just the twelve (or so) top lines only, and then you should see exactly what is in the top output.

---

### Post by speartip on 2018-03-28
May or may not be related as you haven't given much info yet. But I had a problem with the 4.13.xx Kernel eating up my cpu as per this post:
[https://ubuntuforums.org/showthread.php?t=2384513](https://ubuntuforums.org/showthread.php?t=2384513)
Had to revert to the 4.4 kernel to resolve it.
Running top or htop in a terminal is the only way you'll be able to pinpoint the cause.

---

### Post by rossignol on 2018-03-28
Got it always on top now. Thanks. If i can't sort out whatever is doing this, I'll probably just resort to reformatting the drive and reinstalling Ubuntu. Whatever it is that is doing this is pretty new - only a couple weeks. Never did this for the last 8 months since upgrading from Ubuntu 16**.

---

