---
title: "trash/Nautilus"
date: 2008-01-19
forum: General Help
---

### Post by free10 on 2008-01-19
Ok here is the problem. Normally when I move something large to trash like a movie, and then deleted it from there I can check the properties part of a folder and see the amount of free space has increased once again.

Now I have used photorec several times and recovered photos from a CF card or a section of drive and it then puts those in folders, and to get to them I open another terminal and use the "sudo nautilus" command to go to them and then move the new files to trash. Now those do not actually appear in the trash file, but do disappear from where they were, but the available size if I check the properties on a file do not go up afterwards, as though it was never actually moved to trash and deleted.

Even if I reboot it does not show the extra space on the drive I would think that should be created, after I have sent them to trash using nautilus. Anyone have any ideas if they are still their "hiding" or why it does not show up as more space on the drive after using nautilus to move them to trash. Well thanks for any insights on this--Dwight

---

### Post by nick_h on 2008-01-19
You should use:
```
gksudo nautilus
```
rather than:
```
sudo nautilus
```

Deleted files will be in /root/.Trash or on a plug-in card in /media/card/.Trash-root

---

### Post by free10 on 2008-01-19
> **nick_h said:**
> You should use:
```
gksudo nautilus
```
rather than:
```
sudo nautilus
```

Deleted files will be in /root/.Trash or on a plug-in card in /media/card/.Trash-root

Now that worked perfectly as soon as I remember to click on "show hidden files" over in /root/.Trash once I got there to delete them. I gained back 7.5 gigs of extra free space back once I completed deleting and I needed them. I sure do thank you and will save the helpful hints so I can remember them easily--Dwight

---

### Post by nick_h on 2008-01-19
> Now that worked perfectly as soon as I remember to click on "show hidden files"
It is also useful to know that CTRL+H toggles the "show hidden files" setting in nautilus.

---

### Post by free10 on 2008-01-19
> **nick_h said:**
> It is also useful to know that CTRL+H toggles the "show hidden files" setting in nautilus.


OK thanks. One of these days I will get real "gutsy" and see if I can learn to renumber my Ubuntu partions non destructively so another operating system on another drive I have can, once again read a none Linux partition on my Ubuntu drive too. Thanks again--Dwight

---

