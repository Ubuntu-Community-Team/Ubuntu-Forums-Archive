---
title: "[SOLVED] pidgin: can't press the &amp;quot;k&amp;quot; key anymore: Turns on/off the logging feature."
date: 2008-04-16
forum: General Help
---

### Post by darkazurka on 2008-04-16
Hello,

got a problem with pidgin lately, when I press the "k" key in **lowercase** then it turns on or off the logging, as seen in the menu->Options (when having an open conversation window).
I thus have to write messages in Uppercase K, but as you see I want to type in lowercase, else my messages will _looK liKe_ this. 

This happened after I opened Applications->System Tools->Configuration editor and in there I changed various settings in apps->Metacity->general or some related stuff. I can't be sure the problem is I messed with the settings.
I also tried disabling all plugins, but that didn't help.

Anyone can help?

---

### Post by y-lee on 2008-04-16
**EDIT:** see next post

> This happened after I opened Applications->System Tools->Configuration editor and in there I changed various settings in apps->Metacity->general or some related stuff.

Do you have any backups of your home folder? If so try restoring it to an earlier state to fix the configuration problem. If not :confused: ... I gots things to do now but I will have a look thru the configuration editor and pidgin options and see what i can find latter if no one else has any ideas :) No promises on finding anything cause i never saw an issue like this.

Another option would be to  try and uninstall and maybe purge pidgin and the reinstall it. See if that fixes it, it might if ya changed some pidgin stuff in the config files but might not if it is a gnome or Metacity option or keyboard bindings ya changed. :confused:

---

### Post by y-lee on 2008-04-16
Ok I think I might have it as I found a related issue online

First be sure pidgin is not open and then open your file manager and set it to view hidden files and folders. If you use nautilus then click **View** and the **Show Hidden files**. find the **.purple** folder and then open the file **accels **and open it in whatever text editor you wish to use.

In this file look for a line that looks like 

```
; (gtk_accel_path "<main>/Options/Enable Logging" "")
```

in your case in might and probably does look something  like 

```
; (gtk_accel_path "<main>/Options/Enable Logging" k"")
```

change it to look like the first line above. Be sure to include the** ;** in front of it.

I had never paid any attention to this file before but i think this should work :)

Post back and let us know if this works and if it does don't ask me how ya did this. I have found nothing in the configuration editor that relates to this issue so I don't think that is it. :confused:

---

### Post by stylishpants on 2008-04-17
You've activated and then accidentally used Gnome's editable menu shortcut keys feature.

You have assigned the shortcut key for "enable logging" to be the letter k, by mousing over this menu option and simultaneously pressing "k".

To unassign it, open a chat window, mouse over the "enable logging" menu item (without clicking), which should display a "k" on the right side to indicate its keyboard shortcut, and press "backspace". 

The UI for the feature you enabled is in System->Preferences->Appearance:Interface:Editable Menu Shortcut Keys.  Uncheck the checkbox if you don't want this feature anymore.

---

### Post by darkazurka on 2008-04-17
Thank you for your replies, (I don't know why I didn't get any emails notifying of the replies, thinking getting no reply so I checked out elsewhere and found that info)

but your replies really show what to do in the case someone might accidentally use the System->Preferences->Appearance->Interface->Editable menu shortcut keys option and accidentally binding a key to a menu item.

---

### Post by darkazurka on 2008-04-17
y-lee , I would also like to thank you. Could you just correct the "k" so it doesn't look like this k"" ?

---

### Post by y-lee on 2008-04-17
> **darkazurka said:**
> y-lee , I would also like to thank you. Could you just correct the "k" so it doesn't look like this k"" ?



I think you need to just eliminate the k completely but I could be wrong.

---

### Post by darkazurka on 2008-04-18
I meant if you could change the post that had:
; (gtk_accel_path "<main>/Options/Enable Logging" k"")

if you could change it to

; (gtk_accel_path "<main>/Options/Enable Logging" "k")

---

### Post by ArielMT on 2008-05-03
Same thing happened to Pidgin when upgrading Ubuntu from 7.10 Gutsy to 8.04 Hardy:  The "e" key unmodified was configured to turn logging on and off, making it impossible to type "e" in conversations.

---

