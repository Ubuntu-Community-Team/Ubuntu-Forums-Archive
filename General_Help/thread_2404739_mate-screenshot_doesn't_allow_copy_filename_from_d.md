---
title: "mate-screenshot doesn't allow copy filename from dialogue box for pasting elsewhere"
date: 2018-10-28
forum: General Help
---

### Post by Kevin McCready on 2018-10-28
My life would be sooooo much better if I could copy from the filename from the dialogue box.

I've tried shutter, kgrab, screengrab, kazam, flameshot and none of them is as simple as mate-screenshot.

I like mate-screenshot because it pops up with an interactive dialogue and I can easily choose to do 
1. onscreen selection of the area to grab 
2. grab the active window
3. grab the desktop

Any help would be appreciated.

---

### Post by ajgreeny on 2018-10-28
You could also have a look at xfce4-screenshooter which in Xubuntu will offer you the option to save wherever you want, and also to get the whole screen, select a region or just the active window.

In Xubuntu it is very easy to set up with keyboard shortcuts for those three options; in Mate I'm afraid I have no info about that, nor do I know how well it will work in Mate.

---

### Post by wyatt26 on 2018-10-28
1: Launch mate-screenshot -h from terminal
2: Ensure that there is no option to copy screenshot to clipboard from commandline.
Expected results:
User is able to copy screenshot to clipboard as with "gnome-screenshot -c".


Actual results:
User can't to copy screenshot to clipboard from commandline.

[URL="https://dissertationeducators.co.uk/services/nursing-dissertation-help.php"]
[/URL][[COLOR=#000000][FONT=Calibri]Nursing Dissertation Help[/FONT][/COLOR]]("https://dissertationeducators.co.uk/services/nursing-dissertation-help.php")

---

### Post by Kevin McCready on 2018-10-28
Thanks so much for your help. I now have a solution which does what I want.

I opened Keyboard Shortcuts, then put 
gnome-screenshot -i
into the print shortcut

---

