---
title: "changing workspace with mouse wheel"
date: 2016-05-06
forum: General Help
---

### Post by dtree46 on 2016-05-06
How is the workspace changed using the mouse wheel?

Using 14.04.

---

### Post by QDR06VV9 on 2016-05-06
If you have not yet installed
```
sudo apt-get install compizconfig-settings-manager

```

Open the compizconfig-settings-manager and look for Viewport Switcher and make sure it is enabled or ticked && now make sure Rotate Cube is also ticked.
Screen Shots Included.
You also may find this useful: [http://www.omgubuntu.co.uk/2010/11/omg-5-five-ways-to-switch-between-workspaces-in-ubuntu](http://www.omgubuntu.co.uk/2010/11/omg-5-five-ways-to-switch-between-workspaces-in-ubuntu)

---

### Post by mc4man on 2016-05-06
I also use as shown above, best method. 
Just to note you can use 'Desktop-based viewport switching' with the default wall plugin if for some reason you don't like rotate.

---

### Post by buzzingrobot on 2016-05-06
Very often the scroll wheel generates Button 5 and Button 4. You can launch xev in a terminal to check your mouse.  xev opens a little box on screen.  If you place the mouse cursor in the box and click a mouse button, or move the wheel, you'll see a readout of data in the terminal that will include the button number corresponding to that action.

So, if you do use the Viewport Switcher, you'll see two relevant options in that section of CompizConfing Settings Manager.  Set each to a button number that corresponds to wheel movement.

You'll need to scroll over an empty region of the desktop for this to work.

---

### Post by dtree46 on 2016-05-07
buzzingrobot
Thanks for replying.
What is meant by 'two relevant options'?

---

