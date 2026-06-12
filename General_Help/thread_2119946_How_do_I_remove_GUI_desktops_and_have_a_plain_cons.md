---
title: "How do I remove GUI desktops and have a plain console login"
date: 2013-02-25
forum: General Help
---

### Post by THFCandy on 2013-02-25
I see that a lot of people on the forums have had problems losing their desktops and want to reinstate them. I have the opposite problem. I want to either rid my system of all GUI desktops ie. no Unity, Gnome etc, or disable them all so that I just have a plain console login when the system boots. Can someone tell me what I have to do to achieve this. Do I have to remove packages or is there some simple configuration switch that turns it all off?

---

### Post by Cheesemill on 2013-02-25
The following command will disable the display manager meaning your system will always boot in CLI mode:
```
echo "manual" | sudo tee -a /etc/init/lightdm.override 
```If you want to start the GUI just login and type:
     ```
startx
```

---

### Post by THFCandy on 2013-02-25
Thanks for the suggestion.
Have tried "echo "manual" | sudo tee -a /etc/init/lightdm.override" but when I boot I get a blank screen. If I do Alt F1 I get the alternative screen, which has the login prompt. Would like to get that straightaway on reboot. Any ideas?

---

### Post by cortman on 2013-02-25
There may be some useful information [here]("http://askubuntu.com/questions/70188/how-do-i-boot-into-console-mode?lq=1").

---

### Post by THFCandy on 2013-02-25
That was very helpful. Many thanks. Problem resolved.

---

