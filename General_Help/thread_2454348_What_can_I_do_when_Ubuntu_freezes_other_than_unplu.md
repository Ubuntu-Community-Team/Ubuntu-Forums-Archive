---
title: "What can I do when Ubuntu freezes other than unplug power?"
date: 2020-11-27
forum: General Help
---

### Post by sotires on 2020-11-27
Is there a Ubuntu equivalent to ctrl-alt-del? I can't get into system monitor if the system has frozen. Sometimes it unfreezes again after wait, sometimes very long. I don't know if it's a hardware problem or a script  slowing a web page from loading, but it's a pain and I would like to find a solution. Currently using Ubuntu 20.04 but it already occurred with earlier versions.

---

### Post by yancek on 2020-11-27
What happens when you try Ctrl+Alt+Del on Ubuntu?  There is no real reason it should not work as it has been available on computers since 1981.

[https://www.mentalfloss.com/article/51674/history-ctrl-alt-delete](https://www.mentalfloss.com/article/51674/history-ctrl-alt-delete)

---

### Post by CatKiller on 2020-11-27
For your immediate question, the [Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key) is a much better choice than yanking the plug.

Your symptoms sound like you're running out of RAM.

---

### Post by Impavidus on 2020-11-28
When your computer appears to freeze, it's often only the GUI that's broken. Maybe you can still use ctrl+shift+F3 (or one of the other F-keys) to get to the TTY (one of the ctrl+shift-F<something> combis will bring you back to the GUI; exact keys vary with version and flavour of Ubuntu). In the TTY you can login on the command line and see if you can fix it, or at least reboot cleanly.

---

### Post by ajgreeny on 2020-11-28
The most useful move you can make is to diagnose why your computer freezes.
What hardware do you have?

Show us the output of command ***inxi -Fzx***
That will give us more info with which to help you.

---

### Post by HermanAB on 2020-11-28
There used to be a kernel panic morse code LED flasher. Other than that, you need to plow through the log files to try and find out what happened.

---

### Post by VMC on 2020-11-28
Usually getting another VT [Ctrl+Alt+F1-12],  then  Ctrl+Alt+Delete will work.

---

### Post by WB0HYQ on 2020-12-29
I've had this same thing happen to me at least 6 times since I upgraded from 18.04 to 20.04. When my system freezes, NOTHING will work. The mouse is dead and no keyboard keys will respond in any Ctrl/Shift/Alt capacity. When it happens, I look at the network card on the back and the LED isn't even active. The computer, for all practical purposes is powered up--dead, but it doesn't know it. I can only hold the power button down and recover that way. Any log I can find doesn't indicate what happened, or give me a clue as to how to keep it from happening again. The last three halts were as I was using VLC, Firefox (logged in to YouTube), and listening to music radio in the background on Firefox. I suspect it is video/audio related, but can't prove it. I am thankful this is LINUX instead of Windows, as Windows would freak out if I simply killed the power.

Bill

---

