---
title: "a program/library for dialog with a window"
date: 2020-02-07
forum: General Help
---

### Post by Skaperen on 2020-02-07
i know this is not hard with a text console as i have done so myself.  i want to have a script carry out a dialog (or at least provide timed input) with a window (in X).  does anyone know if the tools for this exist and where i might find such?  i would be coding this in Bash, C, Pike, or Python.

---

### Post by thehipho on 2020-02-07
Hi, running a bash search and I just found this!

[FONT=lucida console]gtkdialog - GUI-creation command-line utility based on GTK+ library[/FONT]

I haven't tried it yet, and don't know if it's relevant to what you need.

---

### Post by yancek on 2020-02-07
Zenity should be available, never used it so have no opinion.  I've used kdialog which serves my purposes though I'm not sure it's available in repositories although it should be with Kubuntu as it is KDE.

---

### Post by Skaperen on 2020-02-08
i'm not looking for something the command itself uses.  i'm looking for something that works with a program that plays the part of a fake human that interacts with the window that command brings up.  it needs to be able to operate with the window after the window is open and leave that window open after it is all done so the real human can still use it.  my intent is to make a script to initialize a GUI program in ways that can only be done through that window.

---

### Post by TheFu on 2020-02-08
Look for testing tools. 

There are a bunch of options. AutoX, xdotool, xautomation, AutoKey, PyAutoGUI, XAUT.

---

