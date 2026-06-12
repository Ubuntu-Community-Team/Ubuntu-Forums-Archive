---
title: "Unable to type in Terminal/Root - it is just blank"
date: 2008-04-09
forum: General Help
---

### Post by danial-aalee on 2008-04-09
Hi,
Thanks in advance for looking into this issue of (mine).  I can open termial or Root but it opens only to a white space.  nothing - no windows header, menu line, no borders.  by guessing, I can move the cursor on top part and open menu items but nothing else.  I have tried to change settings colors or fonts (just in case font color is set to Invisible) but nothing - If I try to type anything in the area where it is supposed to be- nothing happens.  Also, not sure if it is related to it or not, windows control button on top left and right corner of the window (to close or minimize) are not there to any application window.  I believe it started when I tried to install Compiz.  Since, I am a new user of Linux (ignorance is not an excuse here), I don't know if I am using GNOME or KDE or any other desktop environment.  However, I just upgraded to UBUNTU 8.10 on AMD 64 X2 machine with 2G ram, Nvidia 6600 on board graphics. One more on same line, that I can not enable 'Custom' feature of Compiz. (may be this is the root of my problem). 
Any help, guidance, your time and assistance is very appreciated.
Thanks,
Danny

---

### Post by ryanhaigh on 2008-04-09
Ok this isn't really a solution as I don't think I completely understand your problem but it sounds compiz related so for the moment you may want to disable compiz till you get things back to normal.

If you log in you can then press alt-f2 which will bring up the run dialog box (although if I understand correctly you won't be able to see it) then type in metacity --replace which will replace compiz with the standard window manager.

You could also for the moment remove compiz by changing to a terminal (ctrl-alt-f1) logging in and using ```
sudo apt-get remove compiz
```

---

### Post by danial-aalee on 2008-04-09
Thanks for your time to look into it.

I can do <alt + f2> and can type a command in there and can run it.  However,' terminal' and 'root terminal' windows appear total blank- just like this message box window without borders and anything to it.  Last night, I installed KDE and I am using it right now and it is still the the same here - just a blank white square.  If I am not wrong, I was using xfce (Ubuntus' default session).

Later tonight, I will do exactly what you have suggested is to un-install Compiz and then see what happens.  I will update you with results.  Once again, thanks for your help.

Danny

---

### Post by bodhi.zazen on 2008-04-09
You can enter the command as a console.

Hit Ctrl-alt-F1 to get to the command line.

Ctrl-alt-F7 to return to KDE

Yes the white screen sounds like a problem with compiz.

---

### Post by danial-aalee on 2008-04-09
Thanks for your kind advice.  

I tried to do <ctrl+alt+f1> and it took me to a gibbrish screen (barely readable that something not found) - I was able to restore to kde with  <ctrl+alt+f7>.  

I am sorry, but I have to log off for the time being (gotta go to work) but will be looking into it later tonight but once again, thank you for your time and help. 
Danny

---

### Post by danial-aalee on 2008-04-10
THANKS  EVERYONE  :)

I was successfully able to uninstall Compiz and it appears to be things are back to normal.  I can see the terminal / root terminal and can get to it properly also windows control are back.  I apologize if my terminology is not so very correct.  I am new to Linux - should not be because I installed 7.10 back in time but really did not use it much.  However now I am working on it more diligently.  Slowly but surely I am coming out of the closet - oops that was Windows... :wink:

With the help of forums I was also able to set VLC as my default player, once again thanks to you all forum moderators and all helping hands.

Once again your efforts with no0bs like me are very very appreciated.

Danny :guitar::
):P

---

