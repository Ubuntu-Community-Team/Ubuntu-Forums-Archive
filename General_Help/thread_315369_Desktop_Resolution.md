---
title: "Desktop Resolution"
date: 2006-12-09
forum: General Help
---

### Post by m3l7down on 2006-12-09
Hey guys,

I got a small question.

Other than the VGA selection at the Ubuntu Live Boot menu, is it possible to force Ubuntu to accept higher resolutions? Right before I installed, I set VGA to 1024x768. Now I want to go higher, but I don't want to reinstall the OS. I know my video card is capable of higher resolutions, but I don't know how to access them. Can you guys help me out here?

Thanks, :D

---

### Post by 3rdalbum on 2006-12-09
Press Alt-F2 and paste this command in:

```
gksudo gedit /etc/X11/xorg.conf
```

Type your password if asked.

A fair way into the file, you will see something similar to this:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
...

```

Etc, etc. In each "Subsection "Display"", add a higher resolution to the Mode line. You can see that I've added the resolution "1152x864" to my xorg.conf file - the resolutions should be sorted highest to lowest, like in mine, and you should add the higher resolutions to all Subsection "Display"s.

Save the changes, log out, and log back in again. If that doesn't work, restart the computer and go to System > Preferences > Screen Resolution to select the new resolution.

---

### Post by PapaNerd on 2006-12-09
A word of caution ... be really careful that you enter a resolution that your monitor will support.  If you end up with a line something like this in the file:
Modes   "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
and your monitor will only handle up to (for example) 1600x1200, then you will end up with a blank screen.  At that point, the options for recovery are limited to things like attaching a monitor that supports the highest resolution listed, booting from the Live CD and mounting the drive to re-edit the file, or reinstalling the OS.

---

### Post by xabbott on 2006-12-09
If you dont want to manually edit xorg.conf do 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also if you mess up X all you have to do is ctrl+alt+F2 to a terminal and fix it. You don't need to reinstall, use a live cd, or get another monitor.

---

### Post by m3l7down on 2006-12-09
Thanks for the help!


For some reason though, this doesn't work. I have changed all the subsections, and I have a space between the new value and the old ones. Nothing is different in my syntax, and I am sure I have the correct resolution size. 1152x864. Can someone please tell me why the computer doesn't recognize the new value?

EDIT: Well, I just deleted the 640x480 value from the strings, but it remains in the resolution chooser. It seems like its not even reading this file that I am editing. What am I doing wrong?

---

### Post by blade1088 on 2006-12-09
So about this blank screen dilemma...I edited my xorg.conf file and obviously entered a value Ubuntu did not like. (1440x900 to be exact) When I rebooted, however, I got the blank screen. How exactly do I go about fixing this? I do have a good deal of knowledge in Windows, but am completely new to Linux and would appreciate any help. Thanks in advance!

---

### Post by riven0 on 2006-12-09
> **blade1088 said:**
> So about this blank screen dilemma...I edited my xorg.conf file and obviously entered a value Ubuntu did not like. (1440x900 to be exact) When I rebooted, however, I got the blank screen. How exactly do I go about fixing this? I do have a good deal of knowledge in Windows, but am completely new to Linux and would appreciate any help. Thanks in advance!

Hit alt+ctrl+F1. You should get to a terminal screen. Log in and then type > sudo nano /etc/X11/xorg.conf

You can edit the file from there. To save Ctrl+S, or Ctrl+alt+X and it should give you the option to save.

Otherwise, the easier way is just to type > sudo dpkg-reconfigure xserver-xorg and follow the directions.

---

### Post by blade1088 on 2006-12-09
When I attempt to login in the terminal, I enter my username and press enter. It then prompts me to enter my password, but does not allow me to type. The only key I seem able to press is enter, and then it claims I have entered an invalid password. Any ideas?

---

### Post by riven0 on 2006-12-09
> **blade1088 said:**
> When I attempt to login in the terminal, I enter my username and press enter. It then prompts me to enter my password, but does not allow me to type. The only key I seem able to press is enter, and then it claims I have entered an invalid password. Any ideas?

hehe...:)  Ubuntu doesn't show any input when you type the password. It's for security reasons. Just go ahead, type the password and press enter, it should log you in.

---

### Post by blade1088 on 2006-12-09
Very sly...quite irritating to an unsuspecting new user though. I'm gonna try this again...thanks :-)

---

### Post by strabes on 2006-12-09
m3l7down: you're trying to change the BOOTSPLASH screen resolution not the X resolution, right? xorg.conf is for your X server. If you want to change the resolution of the bootsplash screen, you need to: ```
sudo gedit /boot/grub/menu.lst
```

At the end of the line that looks (similar to) this: > kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash

add one of the values listed on the table [here](http://en.opensuse.org/SDB:Setting_up_Unsupported_Graphics_Cards_with_the_Framebuffer_Device_(GRUB))  to change the resolution and color depth of the bootsplash.

---

