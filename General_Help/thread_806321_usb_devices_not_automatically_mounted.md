---
title: "usb devices not automatically mounted"
date: 2008-05-24
forum: General Help
---

### Post by tech0007 on 2008-05-24
I'm currently on hardy and up to date. My usb devices (like PSP and mp4 player) do not automatically mount anymore.  I didn't change anything except update the box regularly thru apt-get. The PSP and mp4 player are detected (when I run dmesg or lsusb), but I have to run mount in the terminal to use them.  Any ideas?

---

### Post by tech0007 on 2008-05-24
bump

---

### Post by prshah on 2008-05-25
> **tech0007 said:**
>  The PSP and mp4 player are detected (when I run dmesg or lsusb), but I have to run mount in the terminal to use them.  Any ideas?

Click on System-Preferences-File Management-Media. What is shown for "Software"? And at the bottom, what is the status of the checkbox: "Browse media when inserted"? 

Maybe you can try toggling that last option off then on again?

---

### Post by tech0007 on 2008-05-25
> **prshah said:**
> Click on System-Preferences-File Management-Media. What is shown for "Software"? 

It says "Open Autorun Prompt".

> And at the bottom, what is the status of the checkbox: "Browse media when inserted"? 

Maybe you can try toggling that last option off then on again?


It's checked.  Tried but it didn't work.

---

### Post by Bloch on 2008-05-25
Do you have the problem with memory sticks too?

This solution might apply


[http://ubuntuforums.org/showthread.php?t=773996](http://ubuntuforums.org/showthread.php?t=773996)

---

### Post by tech0007 on 2008-05-25
> **Bloch said:**
> Do you have the problem with memory sticks too?

This solution might apply


[http://ubuntuforums.org/showthread.php?t=773996](http://ubuntuforums.org/showthread.php?t=773996)

Thanks. I tried that but I don't see usefree in the list.

---

### Post by geekATlarge on 2008-05-25
I've just fixed a similar problem on my system. Look at: [Failed to initialized HAL, can't mount USB, log-out icon locks-ups]("http://http://ubuntuforums.org/showthread.php?t=806813")

---

