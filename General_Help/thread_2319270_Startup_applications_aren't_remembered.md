---
title: "Startup applications aren't remembered"
date: 2016-04-02
forum: General Help
---

### Post by x6herbius on 2016-04-02
I'm having trouble getting Ubuntu to remember which applications I want to start when I log in. I'm trying to get this to work with Telegram by adding the binary to the list of startup programs. When I log back in, Telegram doesn't start and is no longer present in the list. Steam does work however, so I'm not sure what's going wrong. Does anyone have any ideas?

---

### Post by Ricardo_Velasco on 2016-04-03
Hello..

I don´t understand you problem.. 

Em.. The problem could be a privacy ( a menu selection).
More detail me your problem

---

### Post by howefield on 2016-04-04
> **x6herbius said:**
> I'm having trouble getting Ubuntu to remember which applications I want to start when I log in. I'm trying to get this to work with Telegram by adding the binary to the list of startup programs. When I log back in, Telegram doesn't start and is no longer present in the list. Steam does work however, so I'm not sure what's going wrong. Does anyone have any ideas?

Just tried it and seems to work perfectly, can you share exactly how you have added Telegram to the the start up list and which version of Ubuntu you are using ?

---

### Post by x6herbius on 2016-04-04
I'm on Ubuntu 15.10. I add Telegram to the list by going to Startup Applications, clicking Add, naming the item Telegram and setting the command to my Telegram executable, which is ~/Telegram/telegram.

---

### Post by howefield on 2016-04-04
> **x6herbius said:**
> ... and setting the command to my Telegram executable, which is ~/Telegram/telegram.

Are you sure that command path is correct ? I use the full path rather than ~/ (not sure if it should make a difference) and the executable is capitalised.

To rule out error, you could navigate to the executable, right click on it and select copy and then right click/paste into the autostart command field.

For info, I also use the -startintray option to start Telegram minimised to panel - obviously you don't need that, just saying :)

---

### Post by x6herbius on 2016-04-05
Well I use the browse button to select the executable so I'm pretty sure. That path was just from memory.

---

### Post by howefield on 2016-04-05
> **x6herbius said:**
> Well I use the browse button to select the executable so I'm pretty sure. That path was just from memory.

OK, well all I can do is confirm that Telegram (0.9.33) works when added to the list of start up applications in Ubuntu 15.10. What works for me is as per attached image.

---

### Post by x6herbius on 2016-04-07
I solved it - it turns out I'd created a startup entry when I used to use XFCE, and this has put an XFCE-Only attribute in the Telegram file in ./config/autostart which the Unity Start Applications manager wouldn't remove. Once I found out that's where the autostart files were located, I was able to fix it myself.

---

