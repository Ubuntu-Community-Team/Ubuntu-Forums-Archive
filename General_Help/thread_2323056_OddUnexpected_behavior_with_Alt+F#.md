---
title: "Odd/Unexpected behavior with Alt+F#"
date: 2016-05-02
forum: General Help
---

### Post by archeryguru2000 on 2016-05-02
I'm having some odd behavior with my newly installed Ubuntu 16.04. I would normally (on previous Ubuntu machines and other Linux distros) press Alt+F1 to open the main menu, Alt+F2 for a run dialog, Alt+F4 to close an application, etc., etc. However, I'm now greeted with a change to tty1, tty2, or tty4, respectively. Interestingly enough, Ctrl+Alt+F1 (and F2, F4, etc.) still switches to tty1 (and tty2, tty4, etc.) as well (which, in my opinion, this later keyboard command is the de facto standard). Not only this, but when I navigate back to my desktop after the "accidental" switch to tty# (Crtl+Alt+F7 --> tty7), I see the originally expected behavior---e.g., the menu is now open; or the run dialog opens; or the application that I wanted to close now closes. Is there a setting that I need to modify to change this (back) to the correct behavior?

I've checked keyboard shortcuts as well as keyboard layouts, but I'm not sure what setting is causing this.

Thanks for all assistance.
~~archery~~

---

### Post by archeryguru2000 on 2016-05-03
Okay.  I may have made some progress.  Under keyboard settings, there's a tab that states Layouts.

[IMG]https://dl.dropboxusercontent.com/u/204375744/ubuntu/layout.png[/IMG]

Then choose Options.  Next, expand the dropdown option > Miscellaneous compatibility options.

[IMG]https://dl.dropboxusercontent.com/u/204375744/ubuntu/misc.png[/IMG]

I've checked the (previously unchecked) box stated: Special keys (Ctrl+Alt+<key>) handled in server.  Log out and log back in.

Now, when I press Alt+F1, I've opened my Menu.  When I press Alt+F2, I'm greeted with a run command. (etc., etc.)  This is good; however, now I do **not** possess the capability of changing to tty1, tty2, etc. by pressing Ctrl+Alt+F1, etc.

Any suggestion or guidance where to go from here?

---

