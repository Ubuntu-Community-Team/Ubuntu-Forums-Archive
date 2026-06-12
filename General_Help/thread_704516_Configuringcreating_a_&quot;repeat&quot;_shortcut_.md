---
title: "Configuring/creating a &quot;repeat&quot; shortcut in Amarok"
date: 2008-02-22
forum: General Help
---

### Post by Fafnir on 2008-02-22
I'm trying to create a keyboard shortcut in AmaroK 1.4.5 to set the track currently playing to repeat.  The standard procedure seems to be:

- Go to Tools->Configure Global Shortcuts (or Shortcuts if you only want it to bind when AmaroK has focus).

- Select the relevant action from the dialog box, possibly using the search bar.

- Enter the key you'd like to use.

- Enjoy.

In principle this works fine (and I have a shortcut set up to get AmaroK to stop after the end of current track), but in practice I seem to be hitting a snag around step two - there doesn't seem to be any action defined for repeating a track in either Global Shortcuts or Shortcuts. Considering you can set a shortcut to *configure your shortcuts* (at least when AmaroK has focus) I'd be a little surprised if it wasn't possible to create one to repeat a track - I don't see how, though. 

Can anyone give me a hint? Failing that, would it be possible to write a script to do it?

Thanks in advance!

---

### Post by kwilliam on 2008-02-22
I'll be darned!  It appears they left that action out.  :-(
Luckily, they didn't leave it out of the DCOP interface.  (Although they appear to have left Repeat Album out!)

Assuming you have dcop installed, the script would be:
```
#
if [ `dcop amarok player repeatTrackStatus` = 'false' ]; then
   dcop amarok player enableRepeatTrack 1;
else
   dcop amarok player enableRepeatTrack 0;
fi

```
That should toggle repeat track.  You can make a global shortcut in Gnome or KDE to execute the script, which should do the trick.

---

### Post by Fafnir on 2008-02-25
Yup - that works perfectly. Thanks! dcop looks like a pretty nice piece of software too...

---

