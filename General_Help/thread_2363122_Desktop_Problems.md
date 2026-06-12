---
title: "Desktop Problems"
date: 2017-06-06
forum: General Help
---

### Post by wbee on 2017-06-06
Hello,

On the start-up page,where I enter my password,the time and language and so forth show up correctly in the upper right,on the top line.

When I hit enter and go to 16 04,the desktop comes up but the top line does not show up. That is,the line with the date and the star to log out on the right and the buttons on the left to reduce or remove the window are not there.

The icons that are beyond the margin that show up when you move the cursor to bring those into the window are not there either.

I tried rebooting and that did not fix it.

To shut down the computer,I have to press the button until it shuts down.

How do I repair this problem?

-----------

Thank you.

---

### Post by efflandt on 2017-06-06
What type of graphics card/chip do you have, are you using default drivers or others, and what grapics cable are you using for your screen? It is possible that either your desktop is not coming up completely or that your graphics is over scanning the display, so you do not see anything near the edge of the screen (especially if using VGA). If your monitor has a menu to adjust size and position, you might check that.

Otherwise see if Ctrl+Alt+T brings up a terminal window, or use Ctrl+Alt+F1 (that with F1 through F6 are vt's) to go to a virtual terminal and login. Then type "dmesg | less" without quotes, hit Enter key, and see if anything there reveals any significant issues. If you use Ctrl+Alt+F1, etc. Alt+F7 takes you back to X. Or you could also do "less /var/log/Xorg.0.log" and see if any major problems there.

If you can get to a terminal one way or another, you can shut down properly with "sudo shutdown -h now" or "sudo poweroff".

---

### Post by wbee on 2017-06-06
efflandt,

I'm using the on-board graphics contained in Biostar A780L3C motherboard with the default drivers. I'm using a VGA cable. I adjusted the size and position and there is no problem there,that I can detect. The F11 fullscreen and return are working property,an everything that is showing is in its proper proportion.

I could not get a terminal to open using the "t" part but got into the virtual terminal. I logged in with my user name. After I hit "enter" if completed the numerical code and asked for my password. When I entered it,it asked me for my password again.

---

### Post by wbee on 2017-06-06
I feel in over my head here,but would I do any damage if I installed and reinstalled the desktop? If not,what is the shell command to do so?

---

### Post by dragonfly41 on 2017-06-06
I had similar symptoms a few days ago .. lost display of some of the applets in top bar.
I can't remember in full how I solved it but looking back through my command line history I see that I ran these commands
```
sudo apt-get install indicator-datetime
sudo apt-get install indicator-applet-complete
```
I restored topbar applets.

The commands might give some clues to search further.

*[Later edit]*


I remember now .. from [this thread]("https://askubuntu.com/questions/136812/missing-panel-icons-at-top-right")


hold down Windows + Alt keys (both to the left of space bar)
right click on top bar .. select "Add to Panel"
a popup window appears and you can select applets

---

### Post by wbee on 2017-06-06
dragonfly41

I tried both entries.

The first returned "unable to locate package" and the second had no effect. But thanks.

---

### Post by dragonfly41 on 2017-06-06
And the third suggestion?

[Later edit]

[More to read here.]("https://askubuntu.com/questions/458117/missing-date-time-from-top-panel-of-unity-desktop-ubuntu-14-04")

---

### Post by wbee on 2017-06-06
dragonfly41,

I tried the third option and I should have been clearer,my fault.

The entire top bar is missing,not just pieces of information normally shown there.

---

### Post by dragonfly41 on 2017-06-06
That is a problem.
From my own searching around I would try this ..

Close all open files, apps etc.

Run the commands
```

sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity

```

then reboot .. 

Other than that, you could try installing classic-gnome-flashback which does not use Unity.

[http://tipsonubuntu.com/2016/10/16/install-classic-gnome-flashback-ubuntu-16-10/](http://tipsonubuntu.com/2016/10/16/install-classic-gnome-flashback-ubuntu-16-10/)

use that mode to investigate and restore Unity if you prefer (my current preference is classic-gnome-flashback).

---

### Post by wbee on 2017-06-07
dragonfly41


Thank you.  That worked. Ticking the unity plug-in worked.

---

