---
title: "Blank: Wallpaper without menu bar"
date: 2008-07-07
forum: General Help
---

### Post by maxa on 2008-07-07
I recently installed Ubuntu on a Gateway laptop (MX3230). When I login, all I see is the wallpaper (the default crane wallpaper). My cursor works fine, and I can also right click; but I see no menu bar up top. I get the impression that my desktop extends off the viewable portion of my screen, because if I can move the cursor beyond the right and bottom borders, and even bring up the *Trash - File Browser* window if I double-click off screen to the right. So far, I've been able to "fix" the problem by reinstalling Ubuntu; but every time I restart the computer after having done so, the same problem presents itself.

---

### Post by AndyCee on 2008-07-07
Bad simple fix: You could move the bar. Ever tried it on the left of the screen?

Better: Try a different resolution & make sure your graphics driver is installed (Check System Hardware in Administration menu).

---

### Post by iaculallad on 2008-07-07
Press Ctrl+Alt+F1 combo, input your authenticated username and password then issue the command below:

```
sudo dpkg-reconfigure xserver-xorg
```

Answer all the questions logically, choose the BEST answer. When you come across the part about resolutions, uncheck (use the space bar) all but leave a resolution w/c fits your screen.

Then

```
sudo /etc/init.d/gdm restart
```

---

### Post by angry_johnnie on 2008-07-07
As far as my own experience goes, dpkg-reconfigure xserver-xorg, fixes only the keyboard, as of Ubuntu 8.04.

I haven't needed to try it lately, but unless there was an update or something, I don't think it will do the trick.

If alt + F2 is working, you could try this:

Press [B]Alt + F2
[/B]
Type **gnome-control-center**

Look for **screen resolution**

And try changing it to something you can use.

Alt + F2 should work.  I think all it needs is gnome-panel to be running.

---

