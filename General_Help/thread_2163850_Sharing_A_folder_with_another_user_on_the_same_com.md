---
title: "Sharing A folder with another user on the same computer"
date: 2013-07-19
forum: General Help
---

### Post by wizlon on 2013-07-19
First, thanks for taking the time to read my scribe.

I am trying to do what I thought would be dead simple: sharing a folder (read/write) created by one user with another - on the same machine.  I have found a bunch of threads and videos both on here, youtube and elsewhere that discuss the use of Samba (which I have had very mixed success with) and/or sharing with Windows (which I have no interest in).  I can right-click on a folder created by user1, select sharing etc - seems easy, but I am unable to see the folder when I log on as user2.  It's driving me nuts, as I thought it would be simple.  I would like to do this as my wife and I "share" the same files on my Windoze PC (I am migrating to Ubuntu).

How do I see a shared folder created by user1 when I logon as user2?

Apologies for a potentially dumb question.

Andrew

---

### Post by HiImTye on 2013-07-19
[http://ubuntuforums.org/showthread.php?t=2163298](http://ubuntuforums.org/showthread.php?t=2163298)[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by wizlon on 2013-07-19
Thank you.  I did try this before but I couldn't seem to get it to work.  I shall try again as at least I now know it's the right solution (I was trying many things). Thanks again.

---

### Post by HermanAB on 2013-07-20
Howdy,

The correct way is to make a new user and group, say 'public'.  Make a new folder, say '/home/public'.  Set the user to 'public' and the group to 'public'.  Set the sticky bit on the folder so that the group will be enforced on all new files.  Now assign each person that needs access to that folder to group 'public'.

---

### Post by Morbius1 on 2013-07-20
** Samba is used to share folders across your home network not between local users so it won't do you much good in this situation.

** "Sharing" a folder unfortunately needs to be defined since it depends on how you want it shared. An example might help.

Let's say you create a new folder: /home/Common and you want user1 and user2 to have access to it:

** [1] This will allow all users to add to and delete files and read but not write to each others files:**
```
sudo chmod 0777 /home/Common
```
** [2] If you add a "sticky" bit to [1] you can ****[B]prevent one user from deleting files owned by another**:[/B]
```
sudo chmod 1777 /home/Common
```
** [3] This will allow both users to add to and delete each others files and allow both users to read and write to each others files:**
```
sudo chown :plugdev /home/Common
sudo chmod 2775 /home/Common
```
[COLOR=#0000cd]*Note: You may have to add user2 or user1 to the plugdev group:*[/COLOR]
```
sudo gpasswd -a user2 plugdev
```
** [4] Adding the sticky bit to [3] can prevent one user from deleting files owned by another:**
```
sudo chmod 3775 /home/Common
```

[COLOR=#0000cd]_**Notes:**_[/COLOR]

** The "1" in 1777 is the "sticky" bit which prevents one user from deleting files owned by another.
** The "2" in 2775 is the setgid bit which forces all new files and any files copied to [COLOR=#0000cd]*but not moved to*[/COLOR] the folder to inherit the group of that folder.
** The "3" in 3775 is a combination of the sticky ( 1 ) and the setgid ( 2 ) bit ( 1+2=3).

If you do a lot of moving of files into this folder then you might consider bindfs as a solution instead. You will lose the sticky bit however since bindfs has no concept of a sticky bit.

[COLOR=#0000cd]**EDIT**[/COLOR]: One more thing - If the folder you want to share is instead in your own home directory and your home directory is encrypted then all bets are off. You are forced at that point to share a folder outside of the home directory.

---

