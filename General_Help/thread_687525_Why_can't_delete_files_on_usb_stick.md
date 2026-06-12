---
title: "Why can't delete files on usb stick?"
date: 2008-02-04
forum: General Help
---

### Post by magnus0 on 2008-02-04
I can't delete files on an usb memory stick. I know, that they go to the .Trash folder on the stick, but the stick is full and there's no room for the .Trash folder. So how do I delete them?

---

### Post by slibuntu on 2008-02-04
Well you could cut and paste them to your harddrive and delete them from there, not the best solution, but it should do the trick

---

### Post by Tenken on 2008-02-04
In a terminal try

```
cd /path/to/usb/stick
rm filename
```

that should delete the files without sending them to the .Trash folder.

---

### Post by geirha on 2008-02-04
That's odd, when you "delete to trash" it just moves the files to the trash-folder, it shouldn't need any extra space for that. Though, to circumvent the trash, mark the files you want to delete, then hit SHIFT+Delete.

---

### Post by slibuntu on 2008-02-04
There ya go! 3 solutions to the problem, after 10 minutes! Thats why the forums are great!

---

### Post by geo909 on 2008-02-04
...and you can always go to the ".trash" folder of your USB stick and delete them the usual way. Then they will be deleted forever.

---

### Post by ugm6hr on 2008-04-26
Sorry to revive an old thread - but I found a (potentially) better solution:
[http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/](http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/)

This .trash issue seems to be more serious than I realised.

It appears that deleting files to .trash, and then emptying the trashcan on (X)ubuntu causes all the remaining files on the USB stick to be unreadable (files present on Windows Explorer, but unable to open correctly in relevant applications) from Windows XP on a fat32 formated USB stick.  Ubuntu seems to play nice with the USB stick though.

I have had problems like this just twice, and this is the only thing I can think that the 2 episodes had in common.

Only way to solve it was to reformat the sticks in Windows.

Anyone else had this issue?

---

