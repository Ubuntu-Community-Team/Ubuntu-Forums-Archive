---
title: "Cedega Issues, Wine Issues (WineDoors as well)"
date: 2007-07-16
forum: General Help
---

### Post by Aryra on 2007-07-16
My computer is completely against Windows Emulation of any sort.

When I try to run Cedega, the computer locks up...I have to restart X...is it org? (ctrl-alt-backspace) to get it working again.

Wine isn't a great deal of help either. It can install Firefox (Windows) but thats just about it...nothing else works, not graphics stuff, not games, nothing.

WineDoors doesnt work right either, but I'm guessing that is a Wine issue...

Can someone help? And before someone says go ask Cedega for that particular issues, its "what I'm paying for" I'll tell you straight off that their support is useless. :P

---

### Post by misconfiguration on 2007-07-16
Sure here is the first thing you need to do, we need some more information about your hardware. Cedega can be WONDERFUL but at the same time it can be a very odd beast.

The first thing you should do is grab all of the information in the Cedega menu, Under one of the options menu (can't remember offhand) you'll find some hardware information. Click on the tab and click 'copy to clipboard', come in this thread and dump all of that information.

I know for a fact Cedega HATES any NV drivers > 9755

Send that stuff over and I'll try to help you out as much as possible.

---

### Post by Aryra on 2007-07-17
I can't even OPEN Cedega, thats the issue.

It just freezes for a bit then reboots the desktop.

Perhaps if I turned off my Nvidia drivers and tried again...

EDIT: Well you have instantly given me some help. It works when I don't have the graphics drivers installed. Sadly it kinda needs those to work properly -_-

---

### Post by misconfiguration on 2007-07-17
I would make sure all of the nvidia drivers are uninstalled 

I think the command is like this;

sudo apt-get remove --purge nvidia*

Then I'd download the driver switch to init 3 kill GDM and reinstall the nvidia driver!

---

