---
title: "thunderbird under ubuntu 18.04.2 some notes"
date: 2019-04-11
forum: General Help
---

### Post by Claus7 on 2019-04-11
Hello,

I wanted to make thunderbird work under ubuntu 18.04.2 flashback so as to keep providing notifications while not occupying space on the taskbar. The problem was that if closing the application, then the notifications no longer worked. 

It should be mentioned that if the application is open, in order for it to provide notifications then someone has to go to Edit->Preferences->General and enable the "show alert" option. In order to have the menu bar enabled you have to right click on top of the thunderbird application and choose it.

Still, every time the application is closed, no notifications are available. In order to bypass this, under window rules of compiz one can provide an exception to the thunderbird window using the Skip taskbar option and writing: class=Thunderbird. 
Now, every time thunderbird is minimized, no taskbar icon is available, yet if brought on the foreground then the minimize, maximize and close buttons are not shown. This has the implication that in order to minimize anew someone has to press Super+h instead. Also, the window cannot be accessed from compiz window management options such as the shift switcher, yet it can be seen in the background.
Thunderbird can be brought back to the foreground by pressing the envelope icon on the panel bar of indicator applet complete. For someone to verify that thunderbird is still working while minimized the system monitor is an option in order to do so.

Some add-ons doing the same work do not work for the latest versions of thunderbird.

Finally, if both imap and pop options are available, the imap has the advantage that it creates all folders found in the mail, instead of just copying the inbox folder only.

edit: there is no actual need to minimize as long as another window/program opens, which automatically makes thunderbird to disappear. Also, if thunderbird is closed, one can verify this, since there will be no small right arrow pointing to thunderbird, while clicking the envelope icon of the panel bar. 

Regards!

---

