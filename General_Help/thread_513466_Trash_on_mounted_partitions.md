---
title: "Trash on mounted partitions"
date: 2007-07-30
forum: General Help
---

### Post by herbster on 2007-07-30
I have a mounted partition named "extra" and it has a .Trash-extra folder. I have no problems emptying it or anything, but I'm wondering:

1. Can it be disabled so that files are just deleted permanently when being deleted?
2. Can I have all deleted files/folders go to the default trash at /home/user/.Trash instead so it all goes bye-bye when I empty trash on my gnome-panel ??

TIA!

---

### Post by fjgaude on 2007-07-30
Yes, you can. In Gnome File Browser, click Edit then Preferences. Click on Behavior. Then in Trash check "Include a Delete command that by passes Trash".

If you delete files while you are in root these files will go into the hidden file .Trash in /root.

Good luck.

frank

---

### Post by herbster on 2007-07-30
Thanks! I have done that.

However, is there any way to stop the .Trash-* when I am simply in file browser and hit DEL on a file/folder on my mounted partition? Just tried it again and it recreated .Trash-extra.

---

