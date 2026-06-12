---
title: "Oh, ****..... partially formatted one of my drives"
date: 2006-08-01
forum: General Help
---

### Post by wr0x2 on 2006-08-01
I have my old ubuntu install in an external hdd... it will not mount, so I ran fsck and found that it had a bad superblock. I ran mke2fs /dev/sdd, thinking that was the correct command to print out the backup superblock locations. Obviously, I was wrong, but I stopped the process while only a minority of the drive had been formatted. How can I get things back to normal on this drive so that I can have my data? Nothing was overwritten, and all the mke2fs said before I killed it was "writing innodes."

---

### Post by RAOF on 2006-08-01
Eeep!  Although most, if not all, of your data should still be there, the partial format will have removed the information about **where** and **what** the data is.  It probably won't be easy (or perhaps possible) to recover everything.

A quick google for "ext3 unformat" doesn't look to hopeful, but that's perhaps your best bet.  Unless you can get someone who **does** know/has done it in the past to post here :-|

---

### Post by RAOF on 2006-08-01
Eeep!  Although most, if not all, of your data should still be there, the partial format will have removed the information about **where** and **what** the data is.  It probably won't be easy (or perhaps possible) to recover everything.

A quick google for "ext3 unformat" doesn't look to hopeful, but that's perhaps your best bet.  Unless you can get someone who **does** know/has done it in the past to post here :-|

---

### Post by wr0x2 on 2006-08-01
Here's what I've got so far:

foremost - I don't want to make a 300gb disk image and then spend days recovering files that will be organized according to type, and not by heirarchy. Most of my data will be useless if it is not filenamed and organized hierarchically in folders.

e2salvage - Looks like I might have a fair shot with this one, but unfortunately I can't get it to compile on ubuntu live. If anyone has a link to a binary, please post.

e2retrieve - Haven't used. If anyone has had success with this, please post.

e2extract - Same as above.

If any data recovery / storage experts are reading, please feel free to offer your input.

---

