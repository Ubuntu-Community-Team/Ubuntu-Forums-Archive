---
title: "Problems during startup (Ubuntu 12.04)"
date: 2013-06-14
forum: General Help
---

### Post by Leon Ponce on 2013-06-14
[COLOR=#404040][FONT=Roboto]I have disabled the auto-login option in 12.04 and after I updated my computer and restarted it I got [this message]("http://i.imgur.com/pg4H2BY.jpg"). Now I keep getting [this other message]("http://i.imgur.com/9eWsTPR.jpg"). What can I do?

[/FONT][/COLOR]

---

### Post by slickymaster on 2013-06-14
Unless you need speech-dispatcher, which you would if you use applications such as ‘screen readers’, you can just disable it. Install Boot-up-manager:```
sudo apt-get install bum
```run it:```
gksudo bum
```and disable speech-dispatcher by removing the ‘check-mark’ and then from the menu go to ‘File’ -> ‘Apply’ and you should be good to go.

---

### Post by Leon Ponce on 2013-06-14
I have to say that when this happens the GUI doesn't load. I get stuck on this screen and nothing load. So any solution that will need a GUI wont work.

---

### Post by slickymaster on 2013-06-14
If you hit Ctrl+Alt+F1, can you manage to get a terminal window?

---

### Post by Leon Ponce on 2013-06-14
I get a terminal with Alt+F4

---

### Post by slickymaster on 2013-06-14
> **Leon Ponce said:**
> I get a terminal with Alt+F4

That's good.
Log into the terminal and please post the output of:```
cat /etc/default/speech-dispatcher
```

---

### Post by Leon Ponce on 2013-06-15
I ended up formating, it was easier and faster, but thanks for the help :p

---

