---
title: "serial mouse :("
date: 2004-11-02
forum: General Help
---

### Post by Porio on 2004-11-02
I know it's strange but the only mouse that can work on my computer right now is a serial one, but it doesn't work under Ubuntu, so I have to use Windows. So please tell me how to make it work under Ubuntu... :oops:

---

### Post by DaveB on 2004-11-08
Had same problem. Serial mouse is now working after editting the XF86Config-4 file.  Here is the procedure:
ctrl-alt-F1 to get to console.
login.
As root, make a backup copy of the XF86Config-4 file:
sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.bkup
  type your user password when requested.
As root, edit the file using an editor such as nano:
sudo nano /etc/X11/XF86Config-4
Page down to the mouse InputDevice section. You will likely have to modify only the 2 lines for Device and Protocol shown below. You need to know which port your mouse is connected to. Save the file; ctrl-x in nano and answer y or yes to the question.
Hit alt-F7 to get back to the mouseless X window.
Hit ctrl-alt-backspace to exit X.
In the console that X exits to, start X again by typing startx&
Serial mouse should now be working.

Hope this helps.
Dave

---------- example mouse  input device section ------------

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/ttyS0"
        Option          "Protocol"              "Microsoft"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

---

