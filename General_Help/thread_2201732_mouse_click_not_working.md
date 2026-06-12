---
title: "mouse click not working"
date: 2014-01-25
forum: General Help
---

### Post by malapradej on 2014-01-25
I have been using Xubuntu and Ubuntu on our older home PC for almost 2  years without much trouble until today when the mouse seemed to not work  properly. I can move the pointer around and click but after a while the  left and right click does not work. I can hover over a button and  clicking shows the visual effect of lowering the button but it won't  respond with the action required. It seems to happen sooner when opening  a firefox window, but is not restricted to firefox. I have looked on this forum and others for advice and I have tried the  following: compiz --replace metacity --replace I have even reinstalled the Xserver. I checked the ximput to see if the buttons were not assigned but  everything seems OK. I am on the 3.2.0-54 kernel and running Xubuntu/Ubuntu 12.01. And I have  tried different mice on different usb ports and they all do the same  thing. Help will be much appreciated.

---

### Post by malapradej on 2014-01-28
I guess if I don't get any help from the community I would be forced to reinstall everything..... A pity.

---

### Post by ibjsb4 on 2014-01-28
Maybe an update would get you going again.

```
sudo apt-get update && sudo apt-get upgrade
```

If you want to upgrade your kernel:

```
sudo apt-get dist-upgrade
```

---

### Post by malapradej on 2014-01-28
Update and upgrade was definitely one of the things I tried. I am going to try a dist-upgrade and see if it works. Thnks for replying.

---

### Post by malapradej on 2014-01-28
You're a star. I don't know how or why my previous kernel got corrupted but the dist-upgrade worked:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by robin7 on 2014-01-28
Great!  Be sure to mark the thread [SOLVED] so others can find the answer more easily if they're having the same trouble.

---

### Post by brel on 2014-02-03
I've a quick question: did the click eventually work or did the mouse click stop working completely? My problem is similar in that I click and like you the animation seems to work but the button is not clicked. However if I click a bunch of times and move the mouse a bit, eventually the click works.

---

### Post by arias2 on 2014-05-10
> **brel said:**
> I've a quick question: did the click eventually work or did the mouse click stop working completely? My problem is similar in that I click and like you the animation seems to work but the button is not clicked. However if I click a bunch of times and move the mouse a bit, eventually the click works.

Did you ever find a solution to this? I've been battling this problem for a few weeks now. The mouse clicks just stop working completely but after a while it finally comes back if I keep at trying to use it as opposed to when I leave my terminal for awhile while it's frozen and come back it still remains frozen.

Unplugging my mouse and re-plugging into same or different usb port it remains frozen. All I can do is log out and log back in using ctrl-alt-del to circumvent the downtime while it's frozen.

The only thing frozen is the button functionality. I can move my pointer around just fine.

---

