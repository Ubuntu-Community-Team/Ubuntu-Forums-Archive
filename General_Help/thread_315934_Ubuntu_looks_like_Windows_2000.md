---
title: "Ubuntu looks like Windows 2000"
date: 2006-12-09
forum: General Help
---

### Post by wee017 on 2006-12-09
After I installed xgl and run it, ubuntu looked like windows 2000. Here's a screenshot:

[http://img2.freeimagehosting.net/uploads/57193cd002.png](http://img2.freeimagehosting.net/uploads/57193cd002.png)

I am running beryl and xgl fine, but it looks bad, like a windows 2000 kind of thing.  How can I fix this?

---

### Post by wgscott on 2006-12-09
Before I answer that you will have to fix your link.

:-D 

The look is infinitely configurable.  Right now I am running Xubuntu and KDE using themes that make it look like OS X.  Just experiment a bit (unless you like the look of windoze 2K).

---

### Post by IYY on 2006-12-10
By 'looks like Windows 2000', do you mean that the GTK theme is set to Redmond? Try switching it to Clearlooks or Human in System > Preferences > Theme.

---

### Post by Azakus on 2006-12-10
Add this to your startup session
```
gnome-session-daemon
```

---

### Post by wee017 on 2006-12-10
Here's a new link:

[http://img329.imageshack.us/img329/3276/screenshotue0.png](http://img329.imageshack.us/img329/3276/screenshotue0.png)


and the code you gave me doesn't work, says command not found. Oh and Im running edgy btw..

---

### Post by igknighted on 2006-12-10
Go to gnome-look.org, browse through the metacity and gtk2.x themes until you find one you like, then go to System->Preferences->themes, drag and drop the .tar.gz file into the themese menu, it should install, then select it and you shouldn't have an issue from there.  If you dont want to download a new thme, you could browse the pre-installed ones in the themes menu.

---

### Post by wee017 on 2006-12-10
I did change the theme, but it only changes part of the look. It only changes the windows border, not the toolbars at the top and at the bottom.

---

### Post by wee017 on 2006-12-10
As you can see in the image I posted..

---

### Post by ButteBlues on 2006-12-10
GTK themes change the color scheme, Metacity themes change the window border.

As for your panels, you can delete panels, add/remove applets, etc. It's all simple.

For example, you could right click on a blank area of the bottom panel and select "Delete Panel" to delete it. Then you could, say, right click a blank spot on the top panel and in Properties set it so that panel is on the bottom.

---

### Post by wee017 on 2006-12-10
If metacity does change the window borders, then it doesn't work I guess.

Here's another screenshot:

[http://img141.imageshack.us/img141/1108/screenshot1by1.png](http://img141.imageshack.us/img141/1108/screenshot1by1.png)

See how the buttons are all gray and square? It didn't look like that before.. and how do I access GTK Themes?

---

### Post by ButteBlues on 2006-12-10
Click on Theme Details. 

Controls == GTK themes.
Borders == Metacity themes.
Icons == Icon themes.

---

### Post by wee017 on 2006-12-10
It worked for the windows, but again the overall theme is not changing.  In the bottom it shows the windows opened.  Before, the buttons were nice and rounded, now they are grey and square.  And the buttons everywhere else are the same, kind of like windows 2000.

---

### Post by wee017 on 2006-12-10
Do you know what I'm talking about or should I put up some more screenshots?

---

### Post by ButteBlues on 2006-12-11
The GTK theme affects your panels. Furthermore, your panel configuration does not change with your other themes. Right click on a blank area of the panel to see panel configuration options.

---

### Post by solidphp on 2006-12-17
This worked for me:

> 1) Try running gnome-settings-daemon from a terminal:

$ gnome-settings-daemon &

You should now see the widgets and icons you selected. To run this command at session login, go to System &#8594; Preferences &#8594; Sessions, go to the "Startup Programs" tab, click the "Add" button and type gnome-settings-daemon into the dialog box. 

Source:
[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL#Troubleshooting](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL#Troubleshooting)

---

