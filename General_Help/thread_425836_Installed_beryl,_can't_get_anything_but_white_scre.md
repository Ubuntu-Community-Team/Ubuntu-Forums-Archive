---
title: "Installed beryl, can't get anything but white screen, tried uninstalling..nothin"
date: 2007-04-27
forum: General Help
---

### Post by billdotson on 2007-04-27
I am (or was) running Ubuntu Feisty.  I went to the restricted driver manager and clicked on it and it said my hardware didn't need any restricted drivers (I have an nVidia 7800 GT 256MB PCI-E x16) I went to the Beryl Feisty install wiki and followed the "1-2-3 install process".  Then I logged out and did ctrl+alt+backspace.  THen I logged in and everything acted like it was coming up, but then it just went to a white screen.  I couldn't do anything.

So then I ctrl+alt+backspace and logged into the failsafe terminal sessiosn and did sudo dkpg-reconfigure xserver-xorg.  When it was all done I booted back in and Beryl was still installed, but the window manager was set on metacity.  So I did sudo apt-get autoremove beryl emerald-themes and installed nvidia-glx (nvidia-glx from synaptic).  Then I did the 1-2-3 install from the beryl wiki again and restarted x (after logging out).  Same thing except the beryl manager wasn't default, but if I switched to it the screen went white (this also happened when I told beryl-manager to switch to compiz).

So then I did the sudo dpkg-reconfigure xserver-xorg and uninstalled the nvidia-glx and did the sudo apt-get autoremove beryl emerald-themes again.  Then I tried reinstalling beryl.  Restarted x as normal and same white screen.  Tried sudo dpkg-reconfigure xserver-xorg, and doesn't fix it.  Also tried uninstalling beryl wth sudo apt-get autoremove beryl emerald-themes at the failsafe terminal.. nothing.  

Thanks

---

### Post by hyperair on 2007-04-28
Did you set beryl-manager to start up at the beginning of a session? If you did, you could go to the folder: ~/.config/autostart and removethe beryl-manager entry from there.

---

### Post by billdotson on 2007-04-28
yes but it stayed up not near long enough for me to stop it

---

### Post by hyperair on 2007-04-28
I meant from the terminal.

Press Ctrl+Alt+F1
Login with your username and password

Type:
```

cd ~/.config/autostart
grep "beryl-manager" *

```
You should see some output resembling...
```
beryl-manager.desktop:Exec=beryl-manager
```
The beryl-manager.desktop is the name of the file. So, you have to delete it with this command:
```
rm beryl-manager.desktop
```

Replace "beryl-manager.desktop" with the name of your file that is returned by the grep command earlier.

After that you may want to restart the GDM
```
sudo /etc/init.d/gdm restart
```

Then login as usual.

---

### Post by Pox on 2007-04-28
Try adding 

```
Option "AddARGBGLXVisuals" "True"
```

to the "Screen" section.

---

### Post by tcpip4lyfe on 2007-04-28
if that doesnt work see if this thread helps.


[http://ubuntuforums.org/showthread.php?t=362381&highlight=beryl+white+screen](http://ubuntuforums.org/showthread.php?t=362381&highlight=beryl+white+screen)

---

### Post by billdotson on 2007-04-29
fixed it.  I removed everything, downloaded the script from nvidia.com and installed it.  Then I added the Option "AddARGBGLXVisuals" "True" section and it worked

---

