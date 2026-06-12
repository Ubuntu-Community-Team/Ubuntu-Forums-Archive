---
title: "Backing up folder too big for 8G stick"
date: 2012-10-18
forum: General Help
---

### Post by grey1beard on 2012-10-18
Having successfully backed up two laptops, I turned to the main system and installed Deja Dup on that, and proceeded to backup my home folder( excluding various folders).
As I now wish to upgrade from 11.04 to 11.10, and then to 12.04 (following the route I took with the laptops) I want to save the backup folder to an 8G memory stick bought for the purpose.

Problem - the "Properties" of the stick show only 7.5G available, and the backup folder is 7.9G.

How do I get "a quart into a pint pot" ?

Is it possible/safe to store the backup folder across two sticks( I've got other smaller ones available) by merely saving one group of archives on a second folder.

Obviously doing a restore would be a bit complicated, but possible ?

John

PS No, I'd prefer not to buy a 16G stick at this stage, and yes, I realise I could lose about 400M of files before doing a smaller backup.

---

### Post by sienile on 2012-10-18
Can't you do a selective backup that includes only the /home directory (which is probably the big folder taking up all your space) and another for everything else?

---

### Post by 1clue on 2012-10-18
Are these systems based on UN*X?

Why not network copy?

---

### Post by wojox on 2012-10-18
Data compression?

---

### Post by grey1beard on 2012-10-18
Hi sienile,
It is only my Home folder that's 7.9G !

Hi 1clue,
Yes, all is Ubuntu here in various releases, but all slowly getting upgraded to 12.04LTS. Network a copy ? Mmm. That sounds a good way to go if I manage to get my three systems talking to each other. But then that would be a good idea anyway ;)

Hi wojox,
Another good idea if I knew how. Something more to learn. Don't remember seeing a reference to it in Deja Dup, so I assume this is a process I would perform separately, possibly to each folder ?

Regards all,
John

---

### Post by grey1beard on 2012-10-18
It now occurs to me (having had a plate of sprats and a beer), that I could just use the 8G stick to move half, then the other half, back to the now stable laptop, while I then try upgrading the desktop system to 12.04.

As that is a separate issue, I could work on it if anything went wrong, then when it was stable, import my two half files back by the same method into one folder, and restore from that afterwards.
Way to go ?
John

---

### Post by 1clue on 2012-10-18
scp -pr /my/local/folder me@myOtherComputer:/my/remote/destination/

where the destination is writable by me@myOtherComputer.

Much faster if you have ethernet going as opposed to wireless, but for 8g I'm not sure it would matter much.

Keep both hosts from hibernating while this happens.

---

### Post by grey1beard on 2012-10-19
A few minor hiccups later, and now the desktop has been upgraded to 12.04.
The 7.9G backup file was moved, as per #6, in two lumps, and recombined in one folder on the laptop. 
Bit of a squeeze, but it's done.

Thanks all,
John

---

