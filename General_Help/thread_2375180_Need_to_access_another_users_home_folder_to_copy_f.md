---
title: "Need to access another users home folder to copy files in ubuntu 16.04"
date: 2017-10-22
forum: General Help
---

### Post by Dreadsen on 2017-10-22
i have two user accounts 
both users have admin privileges. 

the first account got screwed up. it only boots into wallpaper and mouse pointer. it cant access any desktop environments.  only ttyl
i created the 2nd account so i could retrieve the files from the first account by going through the root folder to access the 1st accounts home folder and copy files over to the 2nd accounts home folder. 

when trying to access the home folder it says 
"You do not have the permissions necessary to view the contents of “root”.

how do i gain access into this folder so i can copy files over?

---

### Post by Xian on 2017-10-22
If my understanding is correct you have basically this:

/home/<user1> 
/home/<user2>

Where you are wanting access to <user1> simply for the purpose of copying files to <user2>.

If you are the only user that has access to this system then run:
```
[COLOR=#111111][FONT=Ubuntu]sudo[/FONT][/COLOR] [COLOR=#111111][FONT=Ubuntu]chmod -R 777 /home/<user1>[/FONT][/COLOR]
```
Which should give you full permissions to all of <user1>

---

