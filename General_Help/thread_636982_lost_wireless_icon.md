---
title: "lost wireless icon"
date: 2007-12-10
forum: General Help
---

### Post by ebsbox on 2007-12-10
when i initially installed ubuntu on my dell inspiron 6000 laptop, i had a wireless indicator icon on the top panel.  Clicking this icon listed all available wireless networks and allowed me to connect to any othem that i chose.

My problem is i accidentally removed the wireless indicator icon from my panel, now i don't know how to get it back.  any ideas?

---

### Post by eggdeng on 2007-12-10
First thing to try would be right click on the panel, choose Add to panel & go through the tabs to see if you can find the app[let] in question.

---

### Post by ebsbox on 2007-12-10
yes that was the first place i looked.

---

### Post by venator260 on 2007-12-10
I have this problem as well on my laptop.

---

### Post by nikoPSK on 2007-12-10
I think it's called wireless-applet. I don't know. You could try:
```

sudo apt-get install wireless-applet
```

---

### Post by venator260 on 2007-12-11
That doesn't work, says there's no such package.

---

### Post by nikoPSK on 2007-12-11
sorry, I thought that might work as you install additional applets as so (example)

```
sudo apt-get install timer-applet
```

Sorry, I can of no further assistance

---

### Post by KevLeviathan on 2007-12-11
Wireless icon is stored in the "notification area"
So right click on the top bar, hit add, then drag the notification area up there and you're good to go!

---

### Post by PriceChild on 2007-12-11
[KevLeviathan]("http://ubuntuforums.org/member.php?u=74578") is correct. Make sure you have the "notification area", you should then get the network manager applet appear in that tray on your next log in.

If you want to get it back without logging in and out, once you've recovered your notification area, press alt+f2, and start "nm-applet" from the window that pops up.

---

