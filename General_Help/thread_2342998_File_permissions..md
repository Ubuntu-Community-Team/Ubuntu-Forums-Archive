---
title: "File permissions."
date: 2016-11-12
forum: General Help
---

### Post by m-t-garcia1987 on 2016-11-12
Before there are any questions as to why I didn't post this in support forums I would like to share why.

I did not want to waste the time of the support forums for something that is not an issue.

If you feel that this should still be posted there mods, please let me know and I will do so.

On to my question. So I more or less understand the basic concept of permissions and how it is owner, group, world with 1-7 dictating which permissions are allowed. I had the thought while going through my book (it didn't really explain what I am asking here) to try setting file permissions to 006 for a file that I created, and see if I could access it. I set the permissions and tried to open the file with gedit and was given a permission denied message.

If the permissions that i set for the file (006) allow read and write by world, why would I not be able to access the file as the owner or another user in the group?

I know that the first two 0's dictate user and group, so it seems pretty obvious why I wouldn't be able to access the file but by giving world rw permission, you would think it would counteract those first two 0's.

Again I apologize if it feels like this should be posted in the support forum, it just really isn't important enough for me to merit wasting someones time over there when there are users that may actually be having a problem and need help.

Thanks.

---

### Post by wildmanne39 on 2016-11-12
*Thread moved to **General Help**.*

---

### Post by deadflowr on 2016-11-12
Other isn't world.
Other is anyone not the owner or in the group.

You set owner's permissions to none, so the file abides by that and says no rights to you, owner.
Same applies to group.

---

### Post by m-t-garcia1987 on 2016-11-12
Ok, the book I am using uses the term world rather than other for the third permission group.

I kind of had the idea that regardless of what other was set to, the permissions would stand regardless. Also being told that the third permission group is other (and your explanation of it) helps it make a lot more sense as to why the permissions would stand (because it is not world haha).

Thanks.

---

### Post by oldos2er on 2016-11-12
What book are you referring to?

---

### Post by m-t-garcia1987 on 2016-11-12
The Linux Command Line 
Internet Edition. 
William E. Shotts, Jr.

It is the reading material provided by my school.

---

### Post by oldos2er on 2016-11-12
Yeah,  that's a good  one.  It's been awhile since I've read it though; guess I never noticed the terminology.

---

### Post by TheFu on 2016-11-12
Yep. Good book, but unfortunate use of "world" in this situation.
OTOH, how else would you allow everyone to see a file except 1 group of people or 1 person?  Don't forget to try some odd permissions on directories too.  BTW, what you are doing is THE BEST WAY to learn permissions. Good job!

---

### Post by m-t-garcia1987 on 2016-11-16
Thanks for the replies. I feel like the book is pretty clear (minus that one word which is why I came here) and I'm glad to know that it is a good book to learn from.

---

