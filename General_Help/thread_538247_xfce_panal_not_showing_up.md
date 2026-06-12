---
title: "xfce panal not showing up"
date: 2007-08-29
forum: General Help
---

### Post by robotlovee on 2007-08-29
Hi. i just logged into my xfce and my panal was missing. i went into the settings and tryed to get it back and it wouldn't allow me to click on it but i can click on other things. i need help. thanks a lot!
:KS

---

### Post by robotlovee on 2007-08-29
Please Help Me I Want This To Come Back!!!!!

---

### Post by HermanAB on 2007-08-29
This is a known bug.

Delete the .config/xfce4 directory and log out/in again:
$ rm -Rf ~/.config/xfce4
ctrl-alt-del

Then, once you got it configured the way you want again, make a backup of the configuration:
$ tar -zcvf config.tgz .config

Cheers,

Herman

---

### Post by robotlovee on 2007-08-29
alright. i did that and now nothing is there. i right click on desktop and all i see is 
create launcher
create URL link
create folder
create from template
------------------------
desktop settings

and i can only ctrl+alt+f2 and put in firefox to get back here..
please help me.

ps. just the stuff on my desktop is there and home folder
no panel.

---

### Post by por100pre1 on 2007-08-29
ALT+F2 then type:

```
xfce4-panel
```

Let's see if this works... :-k

---

### Post by robotlovee on 2007-08-30
omg  your the best person ever & i love you :) thanks a bunch it worked great. i cna be so stupid sometimes i guess:)

---

### Post by por100pre1 on 2007-08-30
> **robotlovee said:**
> omg  your the best person ever & i love you :) thanks a bunch it worked great. i cna be so stupid sometimes i guess:)

:lolflag: Thanks. I'm glad to help! And remember: don't call yourself stupid, you are NOT. :guitar:

EDIT: (You are learning Linux, so that proves you are a smart person!! Enjoy. :) )

---

### Post by robotlovee on 2007-08-30
haha yea true. ubuntu is amazing/ :) i go onto my windows computer at my dads and im like right clicking on the desktop hoping to see a list of apps. and stuff ahh!:)

---

