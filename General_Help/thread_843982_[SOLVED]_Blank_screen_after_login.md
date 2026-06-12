---
title: "[SOLVED] Blank screen after login"
date: 2008-06-29
forum: General Help
---

### Post by OsakaWilson on 2008-06-29
After I log in with my username and password a few moments goes by, I hear the hard disk working, then the screen goes blank (a whitish color). I, however, can login in Failsafe Gnome mode and it boots up normally into failsafe mode. 

Does anyone have any suggestion on what may be wrong?

I'm using Hardy on an Acer laptop, 64 bit.

---

### Post by PmDematagoda on 2008-06-29
When you reach the blank white screen, press Ctrl+Alt+F1, execute:-
```
killall compiz.real
```
and then switch back with Ctrl+Alt+F1 and see if that's fixed, if so, then you may want to try running Compiz by reinstalling the driver.

---

### Post by Raistlin355 on 2008-06-29
Would you happen to be using an ATI video card?

---

### Post by OsakaWilson on 2008-06-29
Wow. I didn't expect such quick replies.

PmDematagoda, 
I'm trying that now. 


Raistlin355,
I looked all around my preferences and don't see a reference to the video card. How do you check?

---

### Post by OsakaWilson on 2008-06-29
PmDematagoda, 
I executed killall compiz.real in the command line after doing the Ctrl+Alt+F1 and logging in. It seemed to accept it because nothing happened except a new ~$ line. However, Ctrl+Alt+F1 had no effect while on the command line, so I couldn't go back and check if it worked. Since I don't know how to restart or shutdown out of the command line, I did a hard restart and, of course, the same problem occured. Should ctrl+alt+F1 take me from the command line back into the GUI? What was supposed to happen so that I could check if the killall command worked?
Pardon my lack of knowledge.

---

### Post by OsakaWilson on 2008-06-29
I am now in the command line after executing the killall command. The ctrl+alt+F1 has not effect, so I am just sitting at that point. 

While I had the system open with the failsafe Gnome login, I checked the drivers and it said that I am not using any proprietary drivers, if that helps.

---

### Post by untermensch on 2008-06-29
You could also try ctrl + alt + f1, once there enter sudo shutdown now. It will come up with a list of four options (atleast it does for me) one of them should say fix x. or xfix or something, either way, choose that option. It will attempt to fix your GNOME.

---

### Post by OsakaWilson on 2008-06-29
Ubermensch,
I did that and it seemed to work. Thank you very much.

---

### Post by Raistlin355 on 2008-06-29
```
sudo lspci | grep -i vga
```

Sorry it took so long to reply, had to sleep you know.  However it looks as if you have solved the problem so good job everyone!

---

### Post by untermensch on 2008-06-29
=] Awesome! glad I could help.

---

### Post by syn4hun on 2008-07-14
got the same problem, when i kill compiz.real it's solved, i'm running an ati vid card

---

