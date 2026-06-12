---
title: "Script for Keyboard Layouts."
date: 2008-07-03
forum: General Help
---

### Post by t4ggs on 2008-07-03
Hi, I'm having this problem:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277)
and want to make this script run when system enter in ubuntu
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277/comments/60](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196277/comments/60)

my question is how do I write this script in the computer? i mean how do i save it??

---

### Post by Rhubarb on 2008-07-03
Applications --> Accessories --> Text Editor
Paste this in:
```
#!/bin/bash
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "[]"
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/options -t list --list-type=string "`echo -e "[grp\tgrp:alt_shift_toggle]"`"
```
Then File --> Save As...
Save it as something like "keyboard.sh" in your home directory somewhere.
Find keyboard.sh in Places (in nautilus), right click on it --> Properties.
Go to the Permissions tab, and check the execute checkbox.
To make it run every time you log in:
System --> Preferences --> Sessions
Click the "+Add" button, give it a name (like "Keyboard fix" or similar), Press the Browse button and choose the keyboard.sh file you created, and give it a nice informative comment if you want.
Then just log out and log back in again, and that script should automatically run.

---

### Post by t4ggs on 2008-07-03
than u

---

