---
title: "Add Confirmation Box on Delete"
date: 2007-08-29
forum: General Help
---

### Post by Atypicas on 2007-08-29
I accidentally deleted my music folder while on Ubuntu (Feisty) while doing some cleaning (which is on a third partition, separate from XP and Ubuntu) and it seems that it is gone for good (after trying "Undo" to no avail, looking for trash etc, I just turned off my power supply, hoping it would magically come back -- all that came back was some of the other stuff I was deleting, in a .trash folder or something like that).

Anyhow, I would like to prevent this from happening again, so I'd be interested in a way to add a confirmation box when deleting things. Also, is there a way for files that are deleted outside of the Linux partition to be sent to a trash folder and perhaps add another box if there is no space in the trash folder and the file will be completely deleted?

Thank you for your time,

---

### Post by kellemes on 2007-08-29
From where have you done this deleting?
From the commandline there is no undelete.

---

### Post by Atypicas on 2007-08-29
I was running Ubuntu Linux and what I was deleting was on my 250gb NTFS partition where I keep my music, certain programs, personal files, but nothing more. By default, we can't modify anything on an NTFS partition, but I had found a program that changed configurations to allow me to do so.

I was using the GUI to delete things and accidentally selected something that I did not want deleted.

Keep in mind that I'm a linux noobie :p.

---

### Post by por100pre1 on 2007-08-29
Did you remove the folder with the file browser (Nautilus)? Did you check if there's a hidden Trash folder in that partition?

By default, delete is not enabled. Check in:

```
gconf-editor
```

under **/     apps    nautilus    preferences**

look for **enable delete**

uncheck it if it is checked.

---

### Post by Atypicas on 2007-08-29
It is not checked.

There is a .trash-accountname hidden folder containing most of what I was deleting, on the NTFS partition, but not the music folder. I imagine that it was deleted without going through the trash can system because it was too big to be kept there. If I look at the size of my partition, it is clear that the music can not be on it and it wouldn't fit on any other partition.

I am not sure if the reason it didn't go to trash was because of the size -- it is possible that it was completely my fault. It does not seem that the stuff in the .trash folder is counted in the partition stats so, while I looked at the size of the partition and saw a missing 100gb, this meant nothing. My harsh reboot (closing the PSU) may have screwed things up (I had not checked the trash folder before rebooting).

Whatever the case, it really seems like it is gone, unless there is a place where files rest before going through pure deletion ( :confused: ).

[COLOR="Red"]The important part, though:[/COLOR]

If my folder went straight to pure deletion because it was too big (how is "too big" determined?), which is something that happens on XP,  then I would like to add a confirmation box before such a deletion.

Even if the above assumption is true or If this was all a product of my stupidity, then I would still like to add confirmation boxes on deletes,  like the default Windows XP settings.

---

### Post by alvarogramirez on 2007-09-05
Hi. I have a question.....Im running Ubuntu Feasty 64 bit but can't get the confirm delete...i try in nautilus preferences, check confirm delete....also in gconf-editor in  /apps/nautilus/preferences/confirm_trash...is checked.. I run gconftool-2 -g /apps/nautilus/preferences/confirm_trash and it says True...but no confirmation for delete key...any ideas....????

---

