---
title: "Folder for all to share"
date: 2007-04-10
forum: General Help
---

### Post by Ginja_Ninja on 2007-04-10
Hi all.

I have setup a folder in "/home" named "shared". This is to sit between all the users on my system and provide a place were everyone can read write and execute providing they are in a group called "share"

I have made the folder as i have said, created the group and added the users i wish to have access to this folder. All is well, however, and here is were i am stuck, userA cant change/delete userB's files in this directory. I want everyone to have the ability to change create delete anybody else's files in this folder. (Again, this is controlled by these users being a member of the "share" group)

I know it has something to do with umask,  but i cant get it to work.
Could someone who knows what they are doing, show me (obviously doesnt know what i am doing) the ways in order to acheive this.
Trust me i have spent hours reading trying, google'ing. :(

I appreciate all your help and time.
Take Care

G_N

---

### Post by taurus on 2007-04-10
Umask is for ntfs & vfat filesystem.  You can use chmod if /home/shared is ext3.  What filesystem is /home/shared anyway?

```
ls -la /home
```

---

### Post by Ginja_Ninja on 2007-04-10
> **taurus said:**
> Umask is for ntfs & vfat filesystem.```
ls -la /home
```
ah, did'nt know that.

The system is running ext3.

Still can't work it out. I must be missing something easy. More coffee methinks!


Thanks 

Take Care
G_N

---

### Post by Ginja_Ninja on 2007-04-10
Ok, now i have the ability to delete other peoples files but folder are still an issue.

Any thoughts?


Thanks all

Take Care
G_N

---

