---
title: "Start application minimzed??"
date: 2020-12-16
forum: General Help
---

### Post by zamfp on 2020-12-16
Hi there :)

I would like to have ubuntu launch a couple of apps minimized on boot (specifically spotify and 1password). Is there any way to do this???  I would appreciate any feedback.

Cheers

---

### Post by TheFu on 2020-12-16
Check out **wmctrl**
There might be a way to do it based on the WM or the DE, but we don't know which you are using or which release you have.

---

### Post by #&amp;thj^% on 2020-12-16
TheFu is right: [https://askubuntu.com/questions/663187/how-can-i-run-a-program-on-startup-minimized](https://askubuntu.com/questions/663187/how-can-i-run-a-program-on-startup-minimized)
The script needs both wmctrl and xdotool.

---

### Post by TheFu on 2020-12-16
That script link is awfully complex for what it needs to do. Shouldn't be more than 2 lines, total.  Let me see if I don't have an example here.

Step 1: run the program. **firefox &**
Step 2: **wmctrl -r firefox -b add,hidden**

So, 
```
#!/bin/bash
/usr/bin/firefox &
/usr/bin/wmctrl -r firefox -b add,hidden
```

Tested and working here.  I actually run firefox inside a firejail constrained environment. Still works.

---

### Post by #&amp;thj^% on 2020-12-16
That would be nice, would it accomplish the OP's goal?
> I would like to have ubuntu launch a couple of apps _minimized on boot_
**EDIT:*****Brain Fart on my end, Put into startup Apps..:)

---

### Post by TheFu on 2020-12-16
Most noobs don't know they can't run GUI programs at boot, only after login and the WM is running, controlling windows.

Depending on the DE used, dropping that script into the session auto-start location should make it work just after login.

Heavy programs need to be given a little time to start and open. Add a **sleep 2s** between the commands. Might need longer delay on slower computers.  In the old days, programs would support normal X/Windows options, but all these new-fangled programs stopped that for some reason.  Any options should be in the manpage for each program.  Chromium-browser claims to support GTK+  command-line  flags. It also has a ~/.config/chromium config directory. I don't see iconify or minimize options there.

I didn't test spotify or 1password, as I never use either of those program.  Further, I use fvwm, so I only tested it there. It is a standards compliant WM. Most WMs are standards compliant, but we don't know what the OP is using or even which release of Ubuntu - so an educated guess is all we have.

---

### Post by #&amp;thj^% on 2020-12-16
Works here on Mate as well, with firejailed Apps. As TheFu mentions on some applications, they do not run only one pid
Nice Work, hope the OP is pleased as well.

---

### Post by ajgreeny on 2020-12-16
Just for the purpose of a try-out, not because I wanted or needed it, I have just tried this out in Xubuntu 20.04.
Unfortunately it was a total failure.
I tried it on firefox, mousepad, xfce4-terminal and all failed; the script starts the application as expected but the minimise part of the script using wmctrl fails.

---

### Post by TheFu on 2020-12-16
> **ajgreeny said:**
> Just for the purpose of a try-out, not because I wanted or needed it, I have just tried this out in Xubuntu 20.04.
Unfortunately it was a total failure.
I tried it on firefox, musepad, xfce4-terminal and all failed; the script starts the application as expected but the minimise part of the script using wmctrl fails.

ICCCM/EWMH WMs should support the wmctrl stuff.  Does xfce use a standards compliant WM?
[https://askubuntu.com/questions/143376/how-to-change-the-xfce4-default-window-manager](https://askubuntu.com/questions/143376/how-to-change-the-xfce4-default-window-manager) explains how to change the WM used by XFCE.

20.04 with openbox doesn't work.
20.04 with fvwm doesn't work.
20.04 with mate ... well ... none of the menus work, so I never got to the point to get a terminal open.  Ended up using ssh from another box to kill Mate-session.

Looks like 20.04 X11 changed things, in a major way. Probably some security fix, but that's just a guess. I don't use Wayland due to some workflow needs here, so Wayland working or not is completely unknown.

---

### Post by #&amp;thj^% on 2020-12-16
```
 wmctrl -m
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
[2]+  Done                    firefox

```
full menu functions here.
**EDIT:** I now know why mine works, I use the script shown in first reply in this thread, and both scripts have same name in startup apps.
Sorry for any confusion. If I remove mine, it fails, if I remove script example from TheFu's, and revert to mine it works.

---

### Post by TheFu on 2020-12-16
Which ubuntu release number?

I'm fairly convinced there was an X/11 security change that broke this method after 16.04.  

OTOH, I'd never use it because fvwm has an Iconify parameter supported for any started program, so it isn't necessary.  I have it configured so clicking on any border of any window with the right-mouse button iconifies that window to a specific location. It also can control window geometry and placement by workspace.  If I want a program to be on all workspaces, fine.  If I want it only on 2 of the 9 workspaces, fine.  So much more control than all the other WM/DEs that I've seen. The downside is configuration is via text files.

---

### Post by #&amp;thj^% on 2020-12-16
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.1 LTS
Release:	        20.04
Codename:	focal

---

### Post by ActionParsnip on 2020-12-16
If you use alltray you can send any application to the system tray. Worth a look. Works in any DE

---

### Post by ajgreeny on 2020-12-17
> **ActionParsnip said:**
> If you use alltray you can send any application to the system tray. Worth a look. Works in any DE
Thanks for the reminder; I had totally forgotten about that.
I used it a long time ago for something which I have now forgotten all about, but it certainly worked well, so as you say, it is worth investigating by **zamfp**.

---

### Post by #&amp;thj^% on 2020-12-17
I had problems with Alltray a while back. So Steve Cook and I came up with this method.
Other methods are also availible EG:
See if their preference sections allow for minimize on open. If they do, enable that feature then simply have the apps autostart at login.

If they don't have that feature, you will need to use something like "Devilspie" && "kdocker".

However, it should be understood, whether or not the application can be minimized to the system tray on startup, either via it's own preferences or via Devilspie, as opposed to merely minimized to your window tabs on your panel is dependent on whether the application has that capacity as a feature.

Assuming, then, for the purpose of this post, that your application has neither the capacity to minimize by itself on startup nor the capacity to be minimized to the Tray, you would need to use Devilspie in conjunction with a program called "kdocker".

[https://www.systutorials.com/docs/linux/man/1-kdocker/](https://www.systutorials.com/docs/linux/man/1-kdocker/) 13

kdocker allows any application, irrespective of whether it has the feature itself, to be minimized to the tray.

You can install kdocker with:
```

sudo apt-get install kdocker
```

You start an app minimized to the tray with kdocker with the following command:
```

kdocker <application name>
```

THEN RUN eg:
```

kdocker gimp
```


I think there's a problem with some window titles on KDE4 and above. It works with some KDE app windows, but not all. However, this helped me find a solution: adding the command xdotool windowminimize $(xdotool getactivewindow) 2 secs after starting Elisa did the trick. 
[list]
[*]kdocker: dock any application in the system tray
```

Command to display kdocker manual in Linux: $ man 1 kdocker
NAME
SYNOPSIS
kdocker [options]
DESCRIPTION

 KDocker is a program that will dock any application to the system tray

OPTIONS

-a

     Show author information

-b

     Suppress the warning dialog when docking non-normal windows (blind mode)

-d secs

     Maximum time in seconds to allow for a command to start and open a window
     [default: 5 seconds]

-e type

     Name matching syntax. Choices are:
      n = normal, substring matching [default]
      r = regex (regular expression)
      u = unix wildcard
      w = wildcard
      x = W3C XML Schema 1.1

-f

     Dock window that has focus (active window)

-h

     Display this help, then exit

-i file

     Custom icon path

-j

     Case sensitive name (title) matching

-k

     Regex minimal matching

-l

     Iconify when focus lost

-m

     Keep application window showing (don't hide on dock)

-n name

     Match window based on its title

-o

     Iconify when obscured by other windows

-p secs

     By default, when the title of the application changes,
     a popup is displayed from the system tray for 4 seconds
     Works well with xmms

-q

     Disable ballooning title changes (quiet)

-r

     Remove this application from the pager

-s

     Make the window sticky (appears on all desktops)

-t

     Remove this application from the taskbar

-v, --version

     Show the KDocker version string, then exit

-w wid

     Window id of the application to dock
     Assumes hex number of the form 0x###...

-x pid

     Process id of the application to dock
     Assumes decimal number of the form ###...

AUTHOR

 KDocker was written by Girish Ramakrishnan
 Revised and maintained by John Schember

REPORTING BUGS
Bugs and wishes to the KDocker Home Page <https://github.com/user-none/KDocker>

Pages related to kdocker

    kde4-config (1) - Prints KDE installation paths
    kde4-gnash (1) - GNU Flash (SWF) Player
    kdecmake (1) - Reference of available CMake custom modules.
    kdenlive (1) - An open source non-linear video editor.
    kdenlive_render (1) - Render program for Kdenlive.
    kdestroy (1) - destroy Kerberos tickets
    kdesu (1) - Runs a program with elevated privileges
```
[/list]
Anyway one of these suggestions should work for you. ;)
Al of my suggestions work on linux as a whole, and not just Ubuntu.

---

### Post by zamfp on 2020-12-20
Hi :) I cannot get any of these working, I'm afraid. I am using Gnome & 20.10. Any ideas??

Cheers

---

### Post by #&amp;thj^% on 2020-12-20
First off "I cannot get any of these working" dose not help us in the slightest.
Install 'kdocker'
```
sudo apt install kdocker
```
Then add the applications you wish to start, in "Startup Applications".
Example:
```
kdocker <command to your application here>
```
And then add again for your second application.
```
kdocker <command to your application here>
```
**_I always add a 2 second delay for those._**
Be aware some programs won't work.[B]
EDIT: [/B]Should go without saying, but a reboot is needed to see the change.

---

### Post by dragonfly41 on 2020-12-20
As an alternative to above, install Actiona from Synaptic.
In the Actiona GUI you can use the Window object to control different apps windows.
After testing in the GUI the script is run with the command .. actexec myscript.ascr.
Handy if you can learn old Actionscript2 (from Flash days) to write Code objects.
I use Actiona frequently for automation tasks. Similar to AutoHotKey in Windows.

---

