---
title: "Desktop problems"
date: 2007-09-04
forum: General Help
---

### Post by eddiemar on 2007-09-04
I am a new user on Linux, just switched from Windows XP. I acidentally did something which now doesnt allow me to view items on my desktop, to move items to my desktop and to right-click on my desktop. I am using Ubuntu Feisty fawn. I am totally new and have no idea what to do to fix the problem. I would totally appreciate the help since i have tried everything and no progress has been made.

---

### Post by prince_niceguy on 2007-09-04
Not sure if I understand the problem correctly. Are you not able to right click on the desktop or you are not able to do anything with your computer???

---

### Post by eddiemar on 2007-09-04
first of all, thank you so much for helping me out. I am only unable to right click on my desktop. anywhere else, everything else is functioning perfectly.

---

### Post by eddiemar on 2007-09-04
Please I hope somebody could help, this is really driving me crazy and I would appreciate it very much. only on my desktop is the problem. I cannot use my right mouse click,  and icons that are in the desktop files do not appear on the desktop. everytime i log in the background is rested to no background.

---

### Post by amadeus266 on 2007-09-04
Try this...


Open terminal and enter "gconf-editor"

Navigate to app>nautilus>preferences and find show desktop and click to enable it.


That should fix your problem.

Edit: in trying out what I stated above, I suddenly couldn't right click!!! So I open Synaptec Package Manager and searched for and installed gtweakui.  After install you'll find it in your preferences menu. Open gTweakUI-Nautilus and click "Use Nautilus to draw desktop". Hope that helps.

---

### Post by eddiemar on 2007-09-04
I went to check it out and the box where it says show desktop is checked, its enabled already.

---

### Post by amadeus266 on 2007-09-04
look at my post again. I was editing it when you replied.

---

### Post by eddiemar on 2007-09-04
downloaded the twaek program and still is not working...

---

### Post by amadeus266 on 2007-09-04
Strange, you may have a bigger problem. Well, there went my idea. Anyone got a better one?

---

### Post by eddiemar on 2007-09-04
I don't know if this will help but since I also had a problem with my folders which didnt want to open, all folders that are in "Places", I downloaded Thunar and that solved the folder problem

---

### Post by wolfmind on 2008-03-18
@amadeus266:
your solution worked for me and i thought i gotta to reinstall ubuntu ;-)

thanks for your help!

---

### Post by Dr. Strange on 2008-05-14
Rig: Dell Latitude D400 / Ubuntu Desktop 7.10

Issue: Right-clicking on a blank area of the desktop did not open a menu as expected.

Steps:
1. Open a Terminal.
2. Command: sudo apt-get install gtweakui
3. Enter password.
4. Close Terminal.
5. "System" -> "Preferences" -> "gTweakUI - Nautilus"
6. Check "Use nautilus to draw desktop"
7. Close gTweakUI

Verified: The gTweakUI method worked for me.

---

### Post by noletters on 2008-05-29
The gTweakUI method worked for me too. 

I'm running ubuntu 8.04

thanks

---

