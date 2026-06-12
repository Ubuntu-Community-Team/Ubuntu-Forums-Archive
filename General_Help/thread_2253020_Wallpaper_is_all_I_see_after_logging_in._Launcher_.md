---
title: "Wallpaper is all I see after logging in. Launcher and other controls not accessible"
date: 2014-11-16
forum: General Help
---

### Post by vincentertainment on 2014-11-16
After logging into to Ubuntu 14.10 64 bit, all I see is my wallpaper. Any suggestions?

[LIST]
[*]Dragging my mouse to the left does not make the side launcher appear. 
[*]Pressing the Super (windows) key does not open the Lens 
[*]The top bar that normally displays reboot, time and date, etc is not visible 
[*]Logging into other accounts is the same. 
[*]I can right click which lets me change the wallpaper, but that's it. 
[*]I have to power down the machine to exit. 
[*]I've tried the repair options under alternate boot options already. 
[/LIST]
Thank You

---

### Post by CantankRus on 2014-11-17
First of all try the guest account to see if unity launcher shows. 

If guest account works try this in your account.
If you can open a terminal with ctrl+alt+t , reset and reload unity...
```
dconf reset -f /org/compiz/ && setsid unity
```

If ctrl+alt+t doesn't work try ctrl+alt+F1 to go to a tty and login.(if ctrl+alt+F1 doesn't work reboot and try from the login screen)
Use this command to send a terminal shortcut to your desktop...
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop && chmod +x ~/Desktop/gnome-terminal.desktop
```

ctrl+alt+F7 to get back to your desktop and run the reset and reload unity command.

---

### Post by vincentertainment on 2014-11-19
Thanks for the Help.
Somehow Unity had gotten uninstalled. After the setsid unity command gave me this error
setsid: failed to execute unity: No such file or directory
I opened Synaptic, searched for Unity and it wasn't checked.
I checked it, installed it, and then ran the command again. It gave me a long list of errors, but upon rebooting, everything worked fine.
Learning the Ctrl+Alt+T and Ctrl+Alt+F1 shortcuts were good lessons.
From the command you gave me to copy the terminal shortcut, I figured out the usr/share/applications directory is where all my programs were located.
That allowed me to launch Synaptic, my browser, and anything else I needed to work through this problem.
My problem is fixed and it was a great learning experience!
Thanks again.
Vincent

---

### Post by CantankRus on 2014-11-19
You may want to use synaptic or software centre to view your history
to see when unity was removed.
Removing compiz will remove unity.

When you remove a core package of the ubuntu desktop you also remove the [**_[COLOR="#B22222"]metapackage[/COLOR]_**]("https://help.ubuntu.com/community/MetaPackages") **ubuntu-desktop**.
Re-installing **ubuntu-desktop** will install core packages as dependencies.
Use synaptic... it gives more feedback as to what is being uninstalled/installed.

---

