---
title: "Installing applications adds two icons to the dashboard."
date: 2014-06-18
forum: General Help
---

### Post by iarenoob on 2014-06-18
I recently noticed that some icons are appearing twice in my dashboard, as can be seen bellow:

[[IMG]http://s7.postimg.org/u8a9ayh53/screen1.jpg[/IMG]]("http://postimg.org/image/u8a9ayh53/")

The three applications for which this happens, Pidgin, Skype, and Eclipse, are all applications I recently installed through the software center.  So it seems to be a recent problem.

For each icon "pair", when I right-click one of them this happens:
[[IMG]http://s7.postimg.org/4o7z4ivrb/screen2.jpg[/IMG]]("http://postimg.org/image/4o7z4ivrb/")

This is the information you would normally expect from the application icon.  Left-clicking this icon launches the application normally.  However, when I right-click the "other" icon it only shows a generic file image with little information like this:
[[IMG]http://s7.postimg.org/fmj8mpkcn/screen3.jpg[/IMG]]("http://postimg.org/image/fmj8mpkcn/")

The word in small font seems to always be the first word in whatever command is normally in used to execute that application.  In this case it's "pidgin", for Skype it is "env".  Left-clicking this "other" icon does absolutely nothing as far as I can tell. 

I have checked my /usr/share/applications folder as well as my ~/local/share/applications folder and there doesn't seem to be any duplicate files as far as I can tell(in fact my ~/loca/share/applications is empty except for mimeapps.list).

Is there a way to fix this and remove the second icon?  Thanks.

Edit:  Oh yea, uninstalling the application removes the "good" icon but does nothing about the second do-nothing icon.

---

### Post by iarenoob on 2014-06-18
Uninstalled everything, rebooted(this gets rid of the phantom icons that persist after uninstalling it seems), then reinstalled everything through synaptic and the problem seems to have gone away.  Is this a problem with the software center?

---

