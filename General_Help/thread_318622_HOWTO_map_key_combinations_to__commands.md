---
title: "HOWTO map key combinations to / commands?"
date: 2006-12-14
forum: General Help
---

### Post by moore757 on 2006-12-14
Hello All, 

I have what I hope is a very simple problem.  I am currently running Ubunto 6.06 LTS Dapper, and am absolutely loving it. One thing I have always enjoyed about linux are some of the wonderful and unique graphical applications designed by the community.  

One of my guilty pleasures is the fantatic application 3ddesktop.  I have configured the application and it works swimmingly, however, I would very much like to be able to map a keystroke combination (such as CTRL + z) to stat the application for easy access.  

Essentially I would like to be able to map the /usr/sbin/3ddesk command to various keystroke combinations which are accessible regardless of the availability of a terminal.  

I have tried looking at the System -> preferences -> Keyboard shortcuts interface, but it does not allow for a user to assign commands to keyboard shortcuts, you can only chose from pre-defined sets

Additionally, and I know this may be a bit of a stretch, but what I would REALLY love would be able to map mouse clicks (such as clicking both buttons simultaneously) to start the application! (seeing as how the application already has fantastic inegration with the mousewheel, etc for swapping desktops)  

Any input on this matter would be greatly appreciated.

---

### Post by strabes on 2006-12-14
Not sure how you would do that kind of stuff with the mouse, but I know you can map the mouse with Beryl, which is a 3d-powered desktop. Generally clicking both buttons at the same time emulates a 3rd mouse button click in case you don't have a scroll wheel or something.

To map custom keyboard shortcuts, check [here](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/).

---

### Post by tweedledee on 2006-12-15
> **moore757 said:**
> Essentially I would like to be able to map the /usr/sbin/3ddesk command to various keystroke combinations which are accessible regardless of the availability of a terminal.  

I have tried looking at the System -> preferences -> Keyboard shortcuts interface, but it does not allow for a user to assign commands to keyboard shortcuts, you can only chose from pre-defined sets

Additionally, and I know this may be a bit of a stretch, but what I would REALLY love would be able to map mouse clicks (such as clicking both buttons simultaneously) to start the application! (seeing as how the application already has fantastic inegration with the mousewheel, etc for swapping desktops)  

Any input on this matter would be greatly appreciated.

I suggest you look at this thread: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441).  It describes how to map both keyboard and mouse buttons to do pretty much whatever you want, mainly using xbindkeys to trap the events and trigger the appropriate command(s).

---

### Post by mcduck on 2006-12-15
Keyboard shortcuts with custom commands at least are fairly easy to do, and no extra apps are required:

1. press alt-F2 and run gconf-editor
2. browse to apps/metacity/keybinding_commands
3. set the value of 'command_1' to the command you want to run
4. go to apps/metacity/global_keybindings
5. set the value of 'run_command_1' to the key combo you want to use

---

