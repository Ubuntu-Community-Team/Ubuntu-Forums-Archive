---
title: "[SOLVED] Cut and paste not working"
date: 2007-10-01
forum: General Help
---

### Post by FakeOutdoorsman on 2007-10-01
I'm having problems with cut and paste with ctrl + c/v.  All pasted text ends up as: **ŸŸ**.  I can still c/p with the mouse select and middle button, and ctrl + c/v work with Windows XP in Virtualbox while running Ubuntu.  I'm not sure when exactly this started to happen so it's hard to pinpoint what might be causing this.

---

### Post by dcstar on 2007-10-02
> **FakeOutdoorsman said:**
> I'm having problems with cut and paste with ctrl + c/v.  All pasted text ends up as: **ŸŸ**.  I can still c/p with the mouse select and middle button, and ctrl + c/v work with Windows XP in Virtualbox while running Ubuntu.  I'm not sure when exactly this started to happen so it's hard to pinpoint what might be causing this.

Possibly you have accidently assigned a keyboard shortcut to one of those codes, check:

System-Preferences-Keyboard Shortcuts and see if you can spot the codes for CTRL-C & CTRL-V.

---

### Post by FakeOutdoorsman on 2007-10-02
You made me realize that it probably has something to do with Beryl.  There were no problems with the hotkeys in Gnome or Beryl, but I reloaded Beryl and everything is now fine.

---

### Post by FakeOutdoorsman on 2007-11-13
Found the solution here: [copy/paste corruption -> fixed in VirtualBox 1.5.2]("http://www.virtualbox.org/ticket/611")

"You will need to reinstall the guest additions from the Virtualbox 1.5.2 image."

---

