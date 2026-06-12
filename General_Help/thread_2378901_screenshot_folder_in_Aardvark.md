---
title: "screenshot folder in Aardvark"
date: 2017-11-28
forum: General Help
---

### Post by JamButty on 2017-11-28
In prior versions, I was always prompted for a folder when I made a screenshot, allowing me to put it where it belongs and name it appropriately. In Aardvark it just dumps a generic named file into Pictures. Very Windows. How do I get my folder choice popup back?

---

### Post by #&amp;thj^% on 2017-11-28
This has been filed as bug but there is a work around of sorts
try this:
```
gsettings set org.gnome.gnome-screenshot auto-save-directory 'file:///home/**yourusername**/Downloads'

```
Change the** "yourusername"** to your login user name. and change the directory>> here I used_ "Downloads"  _so you get to pick here.
Second, create a shortcut in Settings > Keyboard, pressing the "+" button there. Assign a name (e.g. "New screenshot") and the command to gnome-screenshot.

Third, click the "Disabled" label in the new shortcut and press the** "Print Screen" **key from your Keyboard. Confirm the dialog that will ask you if you want to reassign the key to this new shortcut.

It's not directly possible to change the directory where screenshots are saved (without patching gnome-shell and/or gnome-settings-daemon).
Not very elegant but it works.
Regards

---

### Post by JamButty on 2017-11-28
1fallen - not getting that to work.
It took a while to figure out that the shortcut key assignment will not accept any function keys, only minimal keyboard with shift, cntrl. e.g. what I use, FN-"Print Scr" will not be recognized. Tried cntrl-shift-P with both "gnome-screenshot" and "org.gnome.gnome-screenshot" as the command. It shows the shortcut as active, but that key sequence does nothing. One video about keyboard shortcuts showed an "add" button appearing after the keyboard sequence is typed. I never get that, so maybe the whole thing is off.

In any event, if I understand you, even if this worked it would only reassign where the generic named file is dumped (e.g. from Pictures to Download) rather than giving me a choice and renaming possibilities.

---

### Post by #&amp;thj^% on 2017-11-30
There is also xfce4-screenshooter and scrot. (Just Thinking out loud ;))
Scrot is mainly CLI>>Info on Scrot:[http://manpages.ubuntu.com/manpages/artful/man1/scrot.1.html#contenttoc2](http://manpages.ubuntu.com/manpages/artful/man1/scrot.1.html#contenttoc2)

xfce4-screenshooter  dose need a few depends Listed below: [https://packages.ubuntu.com/artful/xfce4-screenshooter](https://packages.ubuntu.com/artful/xfce4-screenshooter)
```
 
    libc6 (>= 2.17) [arm64, ppc64el]
        GNU C Library: Shared libraries
        also a virtual package provided by libc6-udeb 

    libc6 (>= 2.7) [not arm64, ppc64el]

    libcairo2 (>= 1.2.4)
        Cairo 2D vector graphics library 

    libexo-1-0 (>= 0.5.0)
        Library with extensions for Xfce (GTK-2 version) 

    libgdk-pixbuf2.0-0 (>= 2.22.0)
        GDK Pixbuf library 

    libglib2.0-0 (>= 2.37.3)
        GLib library of C routines 

    libgtk2.0-0 (>= 2.24.0)
        GTK+ graphical user interface library 

    libsoup2.4-1 (>= 2.26.1)
        HTTP library implementation in C -- Shared library 

    libx11-6
        X11 client-side library 

    libxext6
        X11 miscellaneous extension library 

    libxfce4ui-1-0 (>= 4.9.1)
        widget library for Xfce - Gtk+2 variant 

    libxfce4util7 (>= 4.9.0)
        Utility functions library for Xfce4 

    libxfixes3
        X11 miscellaneous 'fixes' extension library 

    libxml2 (>= 2.7.4)
        GNOME XML library 

    xfce4-panel (<< 4.13)
        panel for Xfce4 desktop environment 

    xfce4-panel (>= 4.11)
```
Both of these are available through you package-manager
Sorry that workaround was not satisfactory.
BTW Gnome has no intention ATM of fixing their screenshot app.

---

### Post by vasa1 on 2017-11-30
JamButty, 1fallen, what happens when you run```
gnome-screenshot -i
```from a terminal?

After you click "Take screenshot", doesn't the choice of filename and foldername become available? I've had no problems on 16.04 and 18.04. I'm not on wayland in 18.04.```
$ apt policy gnome-screenshot
gnome-screenshot:
  Installed: 3.25.0-0ubuntu2
  Candidate: 3.25.0-0ubuntu2
  Version table:
 *** 3.25.0-0ubuntu2 500
        500 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
$ 
```

I'll give 17.10 a try as well later.

I set up keyboard shortcuts for 
[LIST]
[*]whole screen
[*]selected area
[*]active window or 
[*]delayed screenshot of the whole screen (for dropdown menus and stuff)
[/LIST]
 
with all pics being saved to one folder with "timestamp.png" as the filename. Later, I rename and move images that I really want to keep. So I mostly don't use the interactive mode.

Edit: *gnome-screenshot -i* in 17.10 (also not wayland) gives me a choice of specifying filename and file destination.

---

