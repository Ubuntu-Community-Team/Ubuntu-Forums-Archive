---
title: "gnome-panel dissapears"
date: 2007-11-30
forum: General Help
---

### Post by repsol on 2007-11-30
I upgraded to Gutsy. The only issue left is when I boot up and move to another desktop my panels disappear. I then have to cntrl-alt-bkspace and relog in. On about the third try my panels stay. Is this happening to anybody else and is there a fix for this?

I have a Dell D620 with a Nvidia card
I am running Gutsy with no desktop affects.

Any help will be appreciated greatly

Thank you

---

### Post by dreamsR4living on 2007-12-05
I have the problem too, it has something to do with the Nvidia driver, probably a wrong configuration in xorg.conf Does anyone have a solution?

---

### Post by dreamsR4living on 2007-12-05
I found the solution for myself already. Hope it will work for you too.

Just enter the following command in terminal and restart the x-server.
```
gnome-panel
```

Somewhere else I found that the following command should work too.
```
gnome-panel & 
```

If you cannot reach the terminal (because your panels are lost), just hit Alt-F2 or Ctrl-Alt-F2 as an alternative.

---

### Post by sdb2028 on 2008-01-27
Having same problem, gnome panel just dissapeared. Top & bottom. How do I open a terminal if I don't have a panel to select it from?

---

### Post by dreamsR4living on 2008-01-27
Press Alt and F2 on your keyboard and fill in the command, I hope that will work.

---

### Post by sdb2028 on 2008-01-27
Alt+F2 has no response. Have desktop icos enabled through nautilus. I can access the file browser.

---

### Post by sdb2028 on 2008-01-27
Gnome panel back on! Had to find the "gnome terminal" execution file, enabled hidden files in the file browser. (good thing I had the desktop icons enabled). ran "gnome-panel from terminal -> saved session -> rebooted ->everything came back up the way it was suposed to. Thanks for your help e-1.

---

