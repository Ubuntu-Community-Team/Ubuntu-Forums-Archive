---
title: "Sony Vaio Backlight/Brightness Problem"
date: 2013-02-04
forum: General Help
---

### Post by Prolixed on 2013-02-04
Hey every one. I am having a huge problem. I have a Sony Vaio SVT131190X that is dual booting Ubuntu and Windows and when booted in Ubuntu the brightness wont work. It wont work if I manually change the sliders position, if I use the keyboard, or if I type in any command other than "xrandr --output LVDS1 --brightness X"

I've tried multiple methods that I pulled up from the forums, with no luck, such as....
[http://ubuntuforums.org/showthread.php?t=1943652](http://ubuntuforums.org/showthread.php?t=1943652)
[http://ubuntuforums.org/showthread.php?t=1979932](http://ubuntuforums.org/showthread.php?t=1979932)
[http://ubuntuforums.org/showthread.php?t=1979932](http://ubuntuforums.org/showthread.php?t=1979932)

I was wondering how I can fix this? Any suggestions? Anything will help, thanks for your time!

Edit: What happens when I put lspci | grep
```
garett@ubuntu:~$ lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
```

---

### Post by Toz on 2013-02-04
Hello and welcome to the forums.

Have a read of this thread ([http://ubuntuforums.org/showthread.php?t=2091342]("http://ubuntuforums.org/showthread.php?t=2091342")) and the thread it references ([http://ubuntuforums.org/showthread.php?t=2088190]("http://ubuntuforums.org/showthread.php?t=2088190")) where a workaround was developed for a Sony Vaio T model laptop.

---

### Post by Prolixed on 2013-02-04
I tried the first links suggestions with the second link, but found that the second link worked the best! I have seen much of your work and am very grateful that you can help out everyone and that you could help me out! Thanks so much and thanks for your time!

---

