---
title: "KeyBoard Shortcut not found"
date: 2014-07-06
forum: General Help
---

### Post by kakashi_12 on 2014-07-06
1. I found where to assign keyboard shortcuts, System Tools, Preferences, Keyboard. Then Shortcuts tab. But there's nothing in there to change the keyboard shortcut to switch between WorkSpaces. I found out that the default is CTRL + ALT + (left of right). But I want to change it and it's not listed. I see a place to put "Custom", but not sure what the command would be for it.

NOTE: I am using GNome FallBack Desktop Environment.

---

### Post by kakashi_12 on 2014-07-06
Deleted.

---

### Post by kakashi_12 on 2014-07-06
Using Ubuntu 14.04

I found where to assign keyboard shortcuts, System Tools, Preferences, Keyboard. Then Shortcuts tab. But there's nothing in there to change the keyboard shortcut to switch between WorkSpaces. I found out that the default is CTRL + ALT + (left of right). But I want to change it and it's not listed. I see a place to put "Custom", but not sure what the command would be for it.

NOTE: I am using GNome FallBack Desktop Environment.

---

### Post by Bucky Ball on 2014-07-06
*Thread moved to **Multimedia & Video**.*

You might try installing arandr and giving that a try. It's in the repositories and should appear in 'Setting' once installed (am using xfce4 so might be different place for you). Launch it and have a tweak, see if you can get that to do what you are after. Good luck. ;)

---

### Post by Bucky Ball on 2014-07-06
*Threads merged.*

Be patient. Please do not post duplicate threads. Thanks.

---

### Post by kakashi_12 on 2014-07-07
Deleted.

---

### Post by Bucky Ball on 2014-07-07
If arandr is not showing the second display, something is not right. 

Open arandr>Outputs drop-down menu. Nothing there about your second display? If it's there, enable it then check which resolutions are available.

---

### Post by kakashi_12 on 2014-07-07
No menu bar shows. Just 3 buttons.

---

### Post by Bucky Ball on 2014-07-07
See the attached screenshot. Does your arandr look like that? If so, both monitors should be under 'Outputs'. If it doesn't look like that, unsure what you're using ...

---

### Post by kakashi_12 on 2014-07-07
deleted

---

### Post by kakashi_12 on 2014-07-07
Ok. I had to reformat cause I was messing with drivers. From now on, I'm not going to change the default driver unless someone else knows which ones are safe to install.

I ran nvidia-settings in the terminal and it said to install it first. So I installed it, then ran it and it still did not give me what I want.

I installed ARandR. The menu bar shows now. And I can see my TV in the dropdown list. Not sure how to get it active though????

---

### Post by kakashi_12 on 2014-07-07
As far as the keyboard shortcuts go, I also would like to change the shortcuts for the following....
Show Desktop
Terminal
Switch Workspace Left
Switch Workspace Right

---

### Post by kakashi_12 on 2014-07-08
Solved the keyboard issue.
Installed dconf tools via Ubuntu Software Center.
Opened it from Applications, System Tools.
Dconf Editor, Find OR navigate to the below
org, gnome, desktop, wm, keybindings.

Had to do a search to find keybinding for terminal. It was under...
org, gnome, settings-daemon, plugins, media keys.

Source: [http://ubuntuforums.org/showthread.php?t=2217877](http://ubuntuforums.org/showthread.php?t=2217877)

---

### Post by kakashi_12 on 2014-07-08
deleted

---

