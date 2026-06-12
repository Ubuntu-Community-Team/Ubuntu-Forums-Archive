---
title: "A window tiler alternative to Python Windows Organizer"
date: 2024-05-24
forum: General Help
---

### Post by Ralph L on 2024-05-24
I am currently running Xubuntu 22.04, but will be switching to Xubuntu 24.04. I have become very dependent on Python Windows Organizer to "tile" my desktop and easily make use of all available space. However, PYWO uses python 2.7 and Xubuntu has moved on to a new version, I believe, is python 3. PYWO is no longer maintained. I got it to work in Xubuntu 22.04 by "kluging" in run time routines from python 2.7. I had a hard time doing that and may not be able to do it with Xubuntu 24.04. So I am looking for an alternative window tiler, or a way to get PYWO to use python 3. 

Anybody have any suggestions???

---

### Post by currentshaft on 2024-05-24
a

---

### Post by dragonfly41 on 2024-05-25
There are several tools.
 Here is one.  [X-Tile]("https://www.giuspen.com/x-tile/")

Perhaps also [PyAutoGUI]("https://www.topcoder.com/thrive/articles/python-for-gui-automation-pyautogui").

P.S. The list goes on. I should add Albert. You can write a Python extension to run any action from prompt field.

---

### Post by Ralph L on 2024-05-25
Thank you for the responses. I appreciate them.

dragonfly41. I will look into your suggestions. Thank you.

Currentshaft, regarding what is missing from (X)ubuntu that I use a windows organizer.
1. To my knowledge all xubuntu has is drag and drop with the mouse. To move a window, ciick on it and drag to where you want it. To resize a window, click on the edge and drag the edge. To get windows to fit precisely requires a steady hand with the mouse and is quite difficult with a touchpad, which I use.
2. PYWO divides the screen into six areas: 2 vertical and 3 horizontal. It allows any window to occupy any or all of these areas controlled by holding down the ctrl key and pressing a keypad key. For example, if I want to move a window to the upper right corner (1/6 of the screen), I hold ctrl and depress keypad 9. If I want to occupy the upper right and upper middle area, I depress keypad 9 twice. If I want the window to be full screen, I depress ctrl keypad 5 (center of the keypad). If I want a window to occupy the right 2/3 screen, I press crtl keypad 6 twice. And so on with all the keypad keys.
3. The windows fit exactly with no need to fiddle with the mouse. However, if I want a window sized other than what PYWO provides, I can still use the old fashioned drag and drop with the mouse.
4. If I shutdown the computer with windows in a certain place, the windows will be restored to those positions, when I restart. For example, I normally keep Firefox on the right 2/3 of my screen and Thunderbird on the left 1/3. When I restart them, they will go back to those positions (this my happen without PYWO, I haven't run without PYWO for years so I don't know). 
5. An old website discussing PYWO (in 2010) is [http://www.webupd8.org/2010/10/pywo-python-window-organizer-easily.html](http://www.webupd8.org/2010/10/pywo-python-window-organizer-easily.html) .

---

### Post by dragonfly41 on 2024-05-25
I overlooked xdotool and Actiona. And remember you can juggle/move windows to workspaces.

---

