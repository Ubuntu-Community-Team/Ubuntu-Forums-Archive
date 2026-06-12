---
title: "How to set the &quot;Windows flag&quot; button to have the taskbar appear in Xubuntu"
date: 2017-12-02
forum: General Help
---

### Post by 1jarwolf on 2017-12-02
Hello all. I wanted to ask if there is a way as to where I can press the "windows flag" button to open up the taskbar on my Xubuntu because I am too lazy.

---

### Post by Yellow Pasque on 2017-12-02
In keyboard settings, Application Shortcuts tab, bind a key to this command:
```
xfce4-popup-applicationsmenu
```

---

### Post by 1jarwolf on 2017-12-04
I have tried it and it technically right clicks. I wanted it to open the task bar menu, where it shows your programs and stuff. On a sidenote, I guess the key I am wanting to bind is the "Super" key.

---

### Post by Yellow Pasque on 2017-12-05
*shrug* Worked for me. Maybe you are not looking for the applications menu, but something else? THe application menu is the one that starts with "Run program.." and ends with option to logout.
I don't know what else you would mean by "taskbar menu". Try taking a screenshot.

---

### Post by Yellow Pasque on 2017-12-05
Okay, I see now. I use the standard xfce menu, and if you try to pop that up using the command, without having it in the panel, it does mimic a right click. I guess you are using the default Xubuntu menu (whisker menu), so try this:
```
xfce4-popup-whiskermenu
```

---

### Post by 1jarwolf on 2017-12-08
Dude, Dudette, you are AWESOME! Thank you so much!!!! It works now!! This is awesome!!!! This is why I love Ubuntuforums, and is the main reason as to why I use Linux over Windows as there is an actual community willing to help! Thanks again!!!


[SIZE=6][COLOR=#00ff00]SOLVED by [/COLOR][[COLOR=#00ff00]Temüjin[/COLOR]]("https://ubuntuforums.org/member.php?u=327594")[/SIZE]

---

