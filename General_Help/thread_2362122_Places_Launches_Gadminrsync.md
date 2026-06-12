---
title: "Places Launches Gadminrsync"
date: 2017-05-24
forum: General Help
---

### Post by Quarkrad on 2017-05-24
Running Mate 16.04.....   have been playing with various ways of auto backing up a folder when an external USB is plugged in.  I did not write down all the things I did so I've messed something up and cannot undo it!   The issue is that when I click on **Places** / Home Folder, **Places** / Desktop, etc instead of launching caja it launches gadminrsync.  The only option that launches caja is **Places** / Computer.  I do remember changing something to open with gadmin but cannot remember what it was.  Any help appreciated - as I have yet to find what dictates what launches when you click on the various options under **Places**.

---

### Post by dragonfly41 on 2017-05-24
I'm not sure if this is the recommended way .. but it works in setting up Places  ..

(1) Install Thunar File Manager (you could try Nautilus first)

(2) View Side Pane -> Shortcuts

(3) You can remove Shortcuts by right click -> Remove Shortcut

(4) Add new items by navigating filesystem then drag folder or file into Side Bar to create menu item.

[added note]

To refresh your memory on historical commands you ran recently to get you in this state you can run this command
```
history
```
or
```
history | tail
```

---

### Post by Quarkrad on 2017-05-26
Thank you - in the end I did it by uninstalling nautilus so the only file manager on my system was caja.  I then went System/Preferences/Personal/Preferred Applications and then under the Systems tab assigned caja to the File Manager.

---

