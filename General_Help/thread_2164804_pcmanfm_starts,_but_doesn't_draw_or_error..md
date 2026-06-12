---
title: "pcmanfm starts, but doesn't draw or error."
date: 2013-08-01
forum: General Help
---

### Post by Adam_GUI on 2013-08-01
_System_: xubuntu 12.04.  _XFCE version_: 4.10.0

_pcmanfm version_: 0.9.10-0ubuntu2

_Behavior_: pcmanfm was set to be my default file manager in xfce.
XFCE Places locations stopped responding some time this afternoon.
Don't know what I've done different.

Manually launching PCManFM in terminal starts the process, but doesn't draw the program anywhere.
CTRL+C in terminal kills the program as expected.

Clicking on Places shortcuts create additional instances of pcmanfm.
No programs draws.  But, additional instances.  No terminal errors.

Tried to completely remove and reinstall in synaptic.
No change in behavior.

Photo attached.

---

### Post by Toz on 2013-08-01
> **Adam_GUI said:**
> _System_: xubuntu 12.04.  _XFCE version_: 4.10.0

_pcmanfm version_: 0.9.10-0ubuntu2

_Behavior_: pcmanfm was set to be my default file manager in xfce.
XFCE Places locations stopped responding some time this afternoon.
Don't know what I've done different.

Manually launching PCManFM in terminal starts the process, but doesn't draw the program anywhere.
CTRL+C in terminal kills the program as expected.

Clicking on Places shortcuts create additional instances of pcmanfm.
No programs draws.  But, additional instances.  No terminal errors.
Are there any error messages in $HOME/.xsession-errors?

> Tried to completely remove and reinstall in synaptic.
No change in behavior.

Photo attached.
How about renaming the config file/directory ($HOME/.config/pcmanfm) and trying again so that it creates a new basic config file? Maybe something corrupt in there.

---

### Post by Adam_GUI on 2013-08-01
Renamed "./config/pcmanfm/default/pcmanfm.conf" to pcmanfm.conf.old.  No change.
Deleted pcmanfm.conf.old.  No change.

xsession-errors is huge.  Here's just the part about pcman-fm.

```
(pcmanfm:4031): Gtk-CRITICAL **: IA__gtk_window_present_with_time: assertion `GTK_IS_WINDOW (window)' failed

(pcmanfm:4031): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.

```

---

### Post by Adam_GUI on 2013-08-01
Well, I went over to SourceForge after a little google-fu and found a deb file for 
PCManFM-Modified. _Link_: [http://sourceforge.net/projects/pcmanfm-mod/files/?source=navbar]("http://sourceforge.net/projects/pcmanfm-mod/files/?source=navbar").

Seems code is shifting from that to SpaceFM.  But, PCManFM-Mod is working fine.
Not a true fix.  But, at least it's a work-around.

Not sure if I should mark the thread as fixed or not from that.

---

### Post by Toz on 2013-08-01
How about $HOME/.config/libfm? Try renaming that directory as well. (libfm is a dependency of pcmanfm). Maybe also try reinstalling it.

EDIT: Sorry, missed your last post. I agree, not really solved, but a workaround. I'd leave the thread as it is.

---

### Post by vasa1 on 2013-08-02
> **Adam_GUI said:**
> ...
xsession-errors is huge.  ...
That's also something to worry about.

---

### Post by Adam_GUI on 2013-08-02
> **vasa1 said:**
> That's also something to worry about.

It's got everything from compiz arguing with XFCE for desktop control, to basero outputs, to creating menu entries for when I manually update LibreOffice.  

Wasn't really important to the issue at hand.

Updates on that issue, though.
PCManFM still doesn't start after deleting both conf files.

SpaceFM weirds out with permissions.  HAL version worked Okay, until I had to unmount a partition.
Then, all of a sudden, I didn't have permissions to do that.

I've fallen back to using Nautilus, even though I could be using Thunar.
Not sure It's a big deal unless someone else reports the same problem.

---

### Post by Adam_GUI on 2013-09-03
Well, now I just feel silly.
The easy answer was "reboot the system."
I don't know why it took me this long to try again.  But, launching PCManFM works.
I'll mark the issue as solved.

---

