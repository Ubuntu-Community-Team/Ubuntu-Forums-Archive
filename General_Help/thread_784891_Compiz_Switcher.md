---
title: "Compiz Switcher"
date: 2008-05-06
forum: General Help
---

### Post by aaaantoine on 2008-05-06
This thread has two purposes.  The first is a question.  I'm aware there is a reliable on/off switch out there for Compiz that can be applied to the panel.  However, I cannot seem to find it.  Where do I find it?

In lieu of such a contraption, I decided I can probably script my own.

I am sharing my **very crude** homemade Compiz toggle button, both for feedback and to perhaps provide others with a nifty tool.  Below are the instructions for creating one.  (Note: Instructions are for Ubuntu 8.04 Hardy.)

1. Right click your favorite panel, and select "Add to Panel..."
2. Click "Custom Application Launcher", and click the "Add" button at the bottom.
3. In the Name box, type "Toggle Compiz", or whatever you want to call it.
4. For now, type "compiz --replace" in the Command box.  This will be changed later.ls
5. Click OK.

6. Now, open a terminal and type...
```
ls ~/.gnome2/panel2.d/default/launchers
```
You should see a file named "compiz.desktop".  If not, then the part of this script that updates the panel icon will not work for you.

7. Create a file with the following contents.  These instructions assume you are creating the file "~/toggle_compiz".
```
#!/bin/sh

if ps -A | grep compiz.real
then
	sed -i 's/apple-green/apple-red/' ~/.gnome2/panel2.d/default/launchers/compiz.desktop
	sed -i 's/turned ON/turned OFF/' ~/.gnome2/panel2.d/default/launchers/compiz.desktop
	killall gnome-panel
	metacity --replace &
else
	sed -i 's/apple-red/apple-green/' ~/.gnome2/panel2.d/default/launchers/compiz.desktop
	sed -i 's/turned OFF/turned ON/' ~/.gnome2/panel2.d/default/launchers/compiz.desktop
	killall gnome-panel
	compiz --replace &
fi
```

8. Once you have saved the script, don't forget to make it executable.
```
chmod +x toggle_compiz
```

9. Remember that launcher you made?  Right-click it and select "Properties".
10. Change the Command to "/home/user/toggle_compiz", where user is your username.
11. Add a comment saying "Compiz is currently turned OFF".  If compiz is actually on at the moment, replace "OFF" with "ON".  Please note that UNIX is case-sensitive, and that the comment should be typed in exactly as I have written above.
12. Click the icon to change it.  The icon we are looking for should be in "/usr/share/pixmaps/apple-red.png".  If compiz is currently on, the filename should be "apple-green" instead of "apple-red".
13. Select the icon.  Click OK.
14. Click Close.

15. Try clicking it.  Let me know how it goes.

Alright.  So as I said, I submitted this script primarily for feedback.  For instance, I am not fond of "killall gnome-panel" whatsoever.  I'm hoping there's a better, slightly less destructive way to update the panel icon.

---

### Post by tommyhakinen on 2008-05-06
I thought in Hardy, there's fusion-icon that enables us to switch between Compiz and Metacity. I am using it right now.

---

### Post by aaaantoine on 2008-05-06
Ah, that's what it's called... I was fixated on the "compiz" part of the name...

Well, tonight wasn't a total waste.  At least I learned a thing or two about bash script... and sed.

---

### Post by Deeta on 2008-05-07
@other compiz switches:
I think you were looking for that :)
[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

Edit: CompizSwitch differs from Fusion icon in so far that it will not stay in memory and is one click operation instead of menu navigation as with compiz-fusion-icon

---

### Post by aaaantoine on 2008-05-08
Thank you, Deeta, but I think I will stick with the fusion-icon.  It also provides quick access to the settings manager, which I like.

---

