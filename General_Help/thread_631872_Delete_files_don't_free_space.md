---
title: "Delete files don't free space?"
date: 2007-12-04
forum: General Help
---

### Post by helbuns on 2007-12-04
i've looked at a couple posts about this, like goin into trash in /home and /root and making sure it's empty but they seems okay. here is the situation. i have a 500gb that i split windows and ubuntu, when one started getting full (ubuntu) i killed windows set it as ext3 and mounted it permanetly as /storage i believe. okay at this point i'm down to 1.5GB on sda2 and sda4 is my storage guy good to go. so of course i move my, i don't know, 100gb of music and movies over to storage and then delete them, i don't know if it matter but everything used to be in /var/www/ and i was trying to do some webpage streaming. so everything moved and seems to run fine, but my computer still registers low space even tho i go to nautilus and highlight all folders but storage and it only says 50gb. so i don't understand the problem or how to fix it, so just making sure.. i have 2 partition, i have data from one... then i thought i deleted it and it still registars are being used. i do that sweet df in terminal and get.

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2            192450748 178878904   3795892  98% /
varrun                 1037740       232   1037508   1% /var/run
varlock                1037740         0   1037740   0% /var/lock
udev                   1037740        76   1037664   1% /dev
devshm                 1037740         0   1037740   0% /dev/shm
lrm                    1037740     34696   1003044   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda4            282134116  65875612 201926920  25% /storage
/dev/scd0               275358    275358         0 100% /media/cdrom0

alright so if someone could give me some direction here, also.. while here if you know a good video streamer program like vibe streamer, but for video, like flumotion.. but i couldn't get that to work. but if someone knows a good one ubuntu 7.10 compatable please let me know. thank you for you time, i'm looking forward to being an ubuntu expert soon  (a.k.a. someone whom can delete files....) 

-helbuns

---

### Post by DirtDawg on 2007-12-05
I can't help you with the second probelm, but try this: In Nautilus, click View>ShowHiddenFiles and look for a file called ".Trash", or something similar. Chances are, when you trashed everything Nautilus put everything there. This happens regularly on USB drives and thumbdrives. If said folder exists, it must be destroyed.

One solution to this annoyance is located in the Nautilus prefrences. Open Nautilus, go to EDIT>PREFERENCES. Click the "Beahavior" tab, and check the option, "Include a delete command to bypass trash". Then, if you want to delete something permenantly, the delete option will be in your right-click menu. Use with caution!

Hope this helps.

---

### Post by helbuns on 2007-12-05
I can't help you with the second probelm, but try this: In Nautilus, click View>ShowHiddenFiles and look for a file called ".Trash", or something similar. Chances are, when you trashed everything Nautilus put everything there. This happens regularly on USB drives and thumbdrives. If said folder exists, it must be destroyed.

One solution to this annoyance is located in the Nautilus prefrences. Open Nautilus, go to EDIT>PREFERENCES. Click the "Beahavior" tab, and check the option, "Include a delete command to bypass trash". Then, if you want to delete something permenantly, the delete option will be in your right-click menu. Use with caution!

Hope this helps.



Thank you very much dirtdawg for your rapid response.. i didn't know that's where the hidden option was.. but i went in and looked around.. the root.trash is all empty and i don't see one in my home directory.. i looked around a bit and what. the main thing that throws me is when i go to the / directory in nautilus and select all the folder and him properties it only says 50gb, but on the df it shows... i don't know 180 or whatever. but anyone, that didn't seem to work, only further my knowledge but thank you very much.

-helbuns :)

---

### Post by bingoUV on 2007-12-05
Install baobab (from synaptic or add/remove) to analyze disk usage. See what is taking your disk space.

---

### Post by helbuns on 2007-12-05
wow, okay you both were right and i suck, i didn't see the .trash file in my home folder. but it was all here, that baobab form add/remove, synaptic, and terminal all said it was replaced by gnome-utils for anyone interested, but in you go to your terminal and type baobab it loads, then just scan your file system and follow the tree to your demon, god i love that thing and this OS, thank you so much guys now i better go mess up my OS some more.

-helbuns

---

