---
title: "Thunderbird can't delete messages"
date: 2008-07-07
forum: General Help
---

### Post by stwert on 2008-07-07
Hi, I am new to Linux and am trying to set up Thunderbird with my mail from the Thunderbird I had set up in Windows XP. I burned the Mail folder from my profile onto a disk and overwrote the new Mail folder in my Linux profile with my archived Mail (don't know if that was smart or not). Because now I think I have all my mail, plus some stuff that I thought I had deleted, but I'm not able to move anything to the trash. It says "...writing to folder failed" and then asks me to try compacting folders and emptying trash to get more space, which doesn't work.

I'm not sure exactly how to get a clean profile again, and what the problem is. I tried uninstalling, deleting everything in my Mail folder and reinstalling Thunderbird, but that just leaves me with and empty Mail folder which causes different problems. 
Any help is much appreciated.
Apologies if this problem has already been answered in another thread, I couldn't find anything.

---

### Post by stwert on 2008-07-07
Ok, so bizarrely all of a sudden I'm able to delete individual messages, and the only thing I changed was that I deleted a small sub-folder first.
Though everything seems to be relatively ok now, I am still curious as to the potential source of the problem. I don't think it was actually a space issue. There are other weird things that didn't really transfer properly too, like several copies of the same email being present, emails that I've read marked as unread etc.
Thanks

---

### Post by stwert on 2008-07-23
Just an update on my problem. I'm able to delete messages generally, but when I send a message, it is unable to transfer the message to the Sent box and as a result, I am unsure if the message is actually sent and I get a near unending stream of dialogue error boxes with Retry Send and return to compose window type options. 

If anyone has a way to just get a clean start on Thunderbird I'd be willing to try that, but last time I uninstalled it, it kept my accounts mail and junk.

---

### Post by Separ on 2008-07-23
You could completely remove thunderbird by doing
```
sudo apt-get purge thunderbird
sudo apt-get install thunderbird
```
It would probably be your best option.

---

### Post by stwert on 2008-07-25
To my knowledge, that didn't change anything...
did you mean -uninstall thunderbird?
Sorry if I'm misunderstanding. I guess what I'm wanting is to get rid of all my mail files and start with a fresh folder hierarchy and profile.

---

