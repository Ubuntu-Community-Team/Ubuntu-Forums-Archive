---
title: "Issue with Icon's in Unity Launcher"
date: 2015-04-26
forum: General Help
---

### Post by kyle13 on 2015-04-26
I have an interesting problem with my Unity Launcher. I removed an icon and I can put the icon back in, but after I do that each time I launch it it makes a new icon and ties the windows to that new Icon. I am not sure what needs to be done to resolve this as I haven't seen this issue before. Anyone have an suggestions?

I have tried creating the .desktop in the ~/.local/share/applications, but the icon doesn't show up in the launcher.

---

### Post by kostkon on 2015-04-26
There is a (possible) solution to your problem.

You need to specify the WM_Class property of the window of your application so that it can be mapped (and grouped if more than one window) correctly by your DE.

First, you need to open your application, then, you need to open a terminal and do:
```
xprop WM_CLASS
```
and when your cursor changes to a target, click on the window of your app to get its WM_CLASS property.
After that, open your .desktop file and add it there like this, e.g.:
```
StartupWMClass=gnome-terminal
```

Hope that helps.

---

### Post by mc4man on 2015-04-27
> I have tried creating the .desktop in the ~/.local/share/applications, but the icon doesn't show up in the launcher.
If you have an error in the .desktop then it won't be used, maybe check.

Otherwise I'd try - 
remove icon in question from launcher, log out/in
Then in a terminal run - 
gtk-launch name of .desktop minus the .desktop part
Then pin the launcher icon that shows up.

By "name of .desktop minus the .desktop part"  I mean   whatever.desktop would be - 
gtk-launch whatever

---

### Post by kyle13 on 2015-05-02
It is working now. The Google-Chrome-Stable that was already in there only had the New Tab option and another one that was Google-Chrome had a website set in it. It was odd how it would create a new icon even though one was docked (and disappear when I closed the application). I managed to find a copy of someone else google-chrome.desktop and using the gtk-launcher with it generate the right icon with options and it uses the locked icon when I launch the application. Thank you for all of the help.

---

