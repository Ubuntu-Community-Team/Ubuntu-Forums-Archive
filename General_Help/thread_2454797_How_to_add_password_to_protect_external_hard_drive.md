---
title: "How to add password to protect external hard drive?"
date: 2020-12-06
forum: General Help
---

### Post by Richard_York on 2020-12-06
I would like to password protect two existing external hard drives, and can't yet find a route to do so. Ideally I'd like them to work with either Ubuntu (currently on 18.04) and also Windows, as long as the right password is entered.
We've had both for around 10 years or so, maybe more.

Thanks for any guidance.

---

### Post by dinkidonk on 2020-12-06
[VeraCrypt](https://www.veracrypt.fr/en/Home.html) is cross-platform and can do what you want.

---

### Post by Richard_York on 2020-12-07
Thanks, I'll try this. 
Only just seen your reply - ticking for email notifications seems to have failed, so my apologies for a slow response.

---

### Post by Richard_York on 2020-12-08
This at first sight looks rather intimidating - is it easy to use, or am I in danger of losing the lot if I make a simple error?
I confess to being a fairly technophobic user of Ubuntu -  I like it so much better than Windows, mainly.

---

### Post by CelticWarrior on 2020-12-08
You can use Veracrypt two ways.

One is to create a simple encrypted container file. It can be done in any file system and its only size limitation is the single file size limitation of the file system where it resides and, of course, the free space of said partition. This won't delete anything already there. Of course, anything not in that container won't be encrypted.

Another is to create an encrypted partition. This may or may not occupy the full disk's capacity, it's your choice. Make it a single encrypted partition if you want to have the full drive encrypted, of course. In this case make sure you have backups because creating a new partition will delete everything of the previous partitions or partitions in that drive.

---

### Post by Richard_York on 2020-12-11
Thanks for this, that helps. 
(Again, my apologies for a slow reply - still not getting notifications by email.)

I'll try it with an unimportant stick first so if I louse it up it's not the end of the world.

---

