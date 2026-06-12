---
title: "Is there a solution to this list of bugs?"
date: 2007-11-19
forum: General Help
---

### Post by MR.UNOWEN on 2007-11-19
So I've been using Ubuntu(GG) for some time and was wondering if there is a solution for the following bugs.

1. When Ubuntu loads after login I get a orange screen and then the desktop shows. Is there a ways to have it display that it's loading or speed up the process and how do I make it a different color?

2. When the login screen shows up, it shows up in a blocky way. It's not a smooth transition or just a immediate display without it showing up block by block. Is there a way to make it show up smoother.

3. Recently the loading has been taking a little longer than usual, is there a reason why?

4. The mouse pointer is inconsistent, one moment it's the default mouse, the next it's the one I selected. Is there a solution to this?

5. Why does it take a few seconds when I access a fat 32 hard drive? All the others load just fine, but when I access a fat 32, the file browser goes dark for about 5-10 seconds before loading. I loads fine after the first time. What can I do to speed it up? BTW I have it load at start up and using Storage Device Manager to do so.

6. I configure Ubuntu to shut down when I press the power button, but it differs from when I shut down from menu. In menu it's a smooth transition with loading bar going backwards, but when I press the button it displays  a bunch of text with [ok] a and failed (the failed ones had something to do with usb) and then turns off. Can this be fixed by me or is it bug to be fixed by the developers?

Otherwise everything else is working fine. Let me know what need to be reported as a bug and what can be worked out?

---

### Post by MR.UNOWEN on 2007-11-20
Anyone?

---

### Post by hardyn on 2007-11-20
1) buy faster computer, or video driver, differnt color can be achiched through desktop preferences, or by right clicking in the centre of the desktop.
2)use a better video driver, faster computer
3)possibly, more info needed.
4)more explination required.
5)add to the fstab file
6)it might be doing something else at the same time, or had been designed this way, or is a bug

What is your hardware?  you are complaining quite a bit about speed releated issues, and i agree, that your computer sounds slow, but some more information would be nice.

---

### Post by MR.UNOWEN on 2007-11-20
Could you go into detail for #5 solution?

As for #4 an example would be when I click on Firefox, the default pointer shows up for a few sec, then it switches the pointer i selected.

Also my computer is plenty fast. I'm able to do screen effects, so I doubt displaying the login screen is an issue.

---

### Post by FuturePilot on 2007-11-20
1.
```
gconftool-2 -t bool -s /apps/gnome-session/options/show_splash_screen true
```
This will make a splash screen display when you login. As for the background color try going System>Preferences>Appearance. Go to the Background tab and there you will be able to change the color. (I think that's the one)

4. Try logging out and then log back in. Should fix it.

5. There was a bug back during Gutsy development ([https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567") ) it should be fixed unless you manually added that drive to your fstab.

---

### Post by MR.UNOWEN on 2007-11-20
> **FuturePilot said:**
> 1.
```
gconftool-2 -t bool -s /apps/gnome-session/options/show_splash_screen true
```
This will make a splash screen display when you login. As for the background color try going System>Preferences>Appearance. Go to the Background tab and there you will be able to change the color. (I think that's the one)

4. Try logging out and then log back in. Should fix it.

5. There was a bug back during Gutsy development ([https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567") ) it should be fixed unless you manually added that drive to your fstab.

The back ground is set to blue, but it still shows as orange so it's most likely from the login screen. Also the background for the login screen is also set to blue.

As for the hard drive, I used Storage Device Manager to add the partition on start up.

---

