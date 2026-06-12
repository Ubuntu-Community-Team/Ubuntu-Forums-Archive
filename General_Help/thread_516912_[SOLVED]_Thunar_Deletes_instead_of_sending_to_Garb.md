---
title: "[SOLVED] Thunar Deletes instead of sending to Garbage Bin - How to Stop?"
date: 2007-08-03
forum: General Help
---

### Post by OzzyFrank on 2007-08-03
OK, I just found out the hard way that Thunar does not actually send files to the (Gnome/Ubuntu) Garbage Bin, but deletes them totally. Nautilus has an option in Preferences to include a Delete context-menu option that bypasses the Garbage Bin, but Thunar has no such thing (so it can't be that). I did a search for a file to see if Thunar sends files to a hidden Xfce trash folder, but could find nothing. Luckily, the accidentally deleted files were only some images I can download again, but I'd like to know how to get Thunar to send files to the Garbage Bin instead of deleting them. Can this be done? Cheers.

---

### Post by aysiu on 2007-08-03
Uh, actually, Thunar *does* send files to the trash. Maybe this is some kind of bug? Are you sure you checked the right trash can?

If you're using Thunar in Gnome, for example, the Gnome panel trash applet won't reflect changes in the Thunar trash.

---

### Post by OzzyFrank on 2007-08-03
If I delete a file in Nautilus, I can then see it in the trash; if I search for it, it will be found there. If I delete a file in Thunar, it does not show up in the trash, and then does not show up in a search. And yes, I am searching for hidden files and folders, too, etc.

OK, so you are saying Xfce and Gnome have different trash cans, which is what I suspected (which is why I mention "Gnome/Ubuntu"), but I can't find it, and you haven't mentioned where it is. Also, I'd like to know why the file doesn't show up in a search if it is indeed still on my drive somewhere, even in a hidden folder.

Oh, and I can confirm it isn't the Gnome trash panel applet not reflecting Thunar/Xfce deletions or anything (if the lack of search results isn't enough), as when I go to the .Trash folder it has all the same files (and none deleted by Thunar... which is why I ask if there is a separate Xfce trash, and where to find it).

---

### Post by aysiu on 2007-08-03
The files should be located in /home/*username*/.local/share/Trash/files

They may not come up in a search if the system hasn't been indexed recently.

If your deleted files are not in /home/*username*/.local/share/Trash/files, you should file a bug report on the issue:
[https://bugs.launchpad.net/ubuntu/+source/thunar](https://bugs.launchpad.net/ubuntu/+source/thunar)

---

### Post by OzzyFrank on 2007-08-03
Thanks. That's the answer I was looking for. If the dang files had come up in a search, I wouldn't have needed to even post this query. I have all sorts of issues with things not being found in searches, but the worst is doing a search in Nautilus, hehe (like will give me a list of a bunch of hidden and unrelated XML files but not actually give me files with the word in question within the name... how clever and useful!). So I see now that the .Trash folder directly inside the user's folder is only the Gnome trash that is accessed via the Gnome trash applet. Now I can make a link to the REAL garbage bin, so many thanks.

---

### Post by splintercellguy on 2007-08-03
I've always found locate to work great, and for some reason, the GUI search fails miserably.

---

### Post by OzzyFrank on 2007-08-03
Thanks. That's the answer I was looking for. If the dang files had come up in a search, I wouldn't have needed to even post this query. I have all sorts of issues with things not being found in searches, but the worst is doing a search in Nautilus, hehe (like will give me a list of a bunch of hidden and unrelated XML files but not actually give me files with the word in question within the name... how clever and useful!). So I see now that the .Trash folder directly inside the user's folder is only the Gnome trash that is accessed via the Gnome trash applet. Now I can make a link to the REAL garbage bin, so many thanks.

PS: Failed to even notice those screenshot thumbnails before, oops! I see I could have just accessed the deleted files via Thunar's Trash icon in the left pane... geez what a dumbo! Hehe... still, I wasn't expecting Thunar and Nautilus to have links to different places (but should have tried when I realised that might be the case). But at least I got to find out where the main trash folder is so I'll always know where ALL my deleted files are. Many thanks to you all; have a great weekend.

(Erm... why did this repeat my last post when I chose Edit? hehe... sorry for the repitition)

---

### Post by acl123 on 2008-07-05
Wow... I've just discovered so many old files in this mysterious second trash can. So that's where all my hard drive space is going!

---

