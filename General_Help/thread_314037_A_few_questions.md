---
title: "A few questions"
date: 2006-12-06
forum: General Help
---

### Post by Vasant56 on 2006-12-06
Hi, I recently installed Ubuntu, and I have a few questions.

My main one is about setting up permissions on my shared partition. I want to  secure a folder such that only my useraccount in windows and my user account in ubuntu have permissions to access it. Is this possible? 

Also on a minor note, I have rhythmbox installed but i'm unable to add music to my library (mp3s), although Amarok does it fine.. is there any reason why it doesn't? Lastly, when I minimize a windowa series of black squares (outlines of the window) show up momentarily as it closes.. is this normal? It seems like it's not. 

Thanks a lot for the help.

---

### Post by CoolHand on 2006-12-07
> **Vasant56 said:**
> Hi, I recently installed Ubuntu, and I have a few questions.

My main one is about setting up permissions on my shared partition. I want to  secure a folder such that only my useraccount in windows and my user account in ubuntu have permissions to access it. Is this possible? 


Thanks a lot for the help.

For the linux part do a chown youruser.youruser directory
then do chmod 700 directory
that gives you and your group ownership of that directory and only you read/write/exicute permissions.
For the windows part you will have a few more problems.  If it is a samba share you can lock it down through samba to only you but if you boot into windows then you have a problem and you may need a bigger win guru than me because I believe windows pretty much ignores linux permissions and you will have to set the perms in windows.  Having done that any "admin" user on windows will probably still have access.  I am not a windows expert though so you may want to wait for a more knowledgeable answer on that.  Also to consider is the filesystem type as windows cannot read all types of linux filesystems.  You will need to have the folder on a windows filsystem or as an option there is a tool to allow access to ext3 and possibly reiser but other than that you are out of luck.

---

### Post by Laryllan on 2006-12-07
If you're using a Gnome desktop, the black lines are window animations. Like in windows...

---

