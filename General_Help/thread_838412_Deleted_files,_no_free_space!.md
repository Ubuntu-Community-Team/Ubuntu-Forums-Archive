---
title: "Deleted files, no free space!"
date: 2008-06-23
forum: General Help
---

### Post by JohoTehAzn on 2008-06-23
Hello,

I currently have an External USB HD plugged into my computer running Ubuntu.  I only have several GB of free space left, so I Shift + Del'd a directory taking up around 100 GB of space, but it's still telling me that I have no space.

I revealed hidden files and couldn't find anything (no .Trash or nothing).  Searching any of these keywords brings up similar problems where the user merely needed to find the .Trash directory, but that isn't the case here.

Any help would be appreciated.  :(

---

### Post by llama320 on 2008-06-23
I'm not sure this will help, but it's worth a shot..

First try just restarting the computer and seeing if that helps...the files might be stuck in cache/swap/whatever limbo files go to before they're added/deleted

Also just try unmounting and remounting the HDD

Good Luck

---

### Post by cariboo on 2008-06-23
There is more then likely a hidden trashcan on your usb drive, Doing as llama320 says it may ask you if you want to empty the trash first before unmounting.

Jim

---

### Post by JohoTehAzn on 2008-06-23
I tried multiple times re-mounting and rebooting to no avail.

---

### Post by llama320 on 2008-06-23
have you tried plugging the HDD into another computer, maybe with a different OS running?

also, and this isn't a great option..kind of an I-give-up-and-hope-it-never-happens-again thing, but if you have somewhere else to put the data you want you can copy it to that place and then reformat the HDD

just a couple ideas..i really don't know what's going on with it though :(

---

### Post by Rocket2DMn on 2008-06-23
shift+del should skip over the trash bin, but you can check the .Trash-1000 folder (hidden, CTRL+H to show) to see if anything is in it.  That is assuming you are using Hardy.  If you are using an older version, the folder will be called .Trash-<username>

---

