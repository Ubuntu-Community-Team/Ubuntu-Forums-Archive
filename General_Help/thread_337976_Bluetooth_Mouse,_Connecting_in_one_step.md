---
title: "Bluetooth Mouse, Connecting in one step?"
date: 2007-01-13
forum: General Help
---

### Post by tsav87 on 2007-01-13
Ok, I am able to see the mouse, and connect the mouse, but I have to enter code to do so.

Here is how I have been connecting the mouse.

Open Terminal...

Enter:  hcitool scan
Result: XX:XX:XX:XX:XX:XX     Name of Device

Enter:  hcitool --connect XX:XX:XX:XX:XX:XX

Connected.

Is there an application that will do this for me, like the Wifi-Radar but for bluetooth?

What I want to be able to do is do that in one step, or be able to not even have to do anything at all, just have the bluetooth always searching for new devices and allowing all of them to connect, but if possible, ask my permission before granting connection.

---

### Post by shameless on 2007-12-03
Found a nice article on it right 
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html]("http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html")
here

---

### Post by Linteg on 2007-12-03
I'm using gnome's bluetooth-applet (should show up in they tray when bluetooth is enabled), and have set my mouse as a trusted device and it works flawlessly, the mouse is working as soon as gdm starts.

---

