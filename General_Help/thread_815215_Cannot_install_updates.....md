---
title: "Cannot install updates...."
date: 2008-06-01
forum: General Help
---

### Post by DJSchmidty on 2008-06-01
K, so a while ago I had this problem, the update icon comes up in the top right, but when it lists the updates that need to be installed, and I click install updates, it never asks me for a password, it just sits there.  I tried restarting, i tried doing this in terminal with "sudo apt-get update" but the icon is still up there.

Anyone have a suggestion?

Thanx..

---

### Post by Amarsingh0793 on 2008-06-01
This happens with me too. Add Force Quit to your Panel and do the following:
1) Click the icon to bring up the update manager.
2) Click install updates
3)If it does not work click on the force quit icon and click on the update manager window.
4) Try opening update manager again (click on the icon)

This usually works with me so I hope it works for you.

Hope this helps!

---

### Post by Prospero2006 on 2008-06-01
For more output go to the terminal and type this:
```

sudo apt-get update
sudo apt-get upgrade

```

The output there should help.

---

### Post by DJSchmidty on 2008-06-06
How do I add force quit to the panel?

---

### Post by Amarsingh0793 on 2008-06-06
Right click the panel and then click Add to panel. Then find force quit.

---

### Post by DJSchmidty on 2008-06-09
k, added force quit to the panel, but still won't ask me for a password.  Just sits there and hour glasses.  I force quit the update manager and open it again, and same thing happens....

On another note, I do the code above (sudo apt-get update
sudo apt-get upgrade) and it seems to install most updates, but 5 still remain.

What gives?:confused:

---

