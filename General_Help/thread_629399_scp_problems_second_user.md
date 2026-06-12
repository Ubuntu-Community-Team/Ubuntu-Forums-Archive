---
title: "scp problems second user"
date: 2007-12-02
forum: General Help
---

### Post by psitham on 2007-12-02
Hello Everybody,

I've read a few posts on the forum but not able to find out my particular problem. 
I have two users on my machine, say for example A and B. I have my personal stuff with user A and tools installed with user B. I log in every time into A and then su - B in the terminals to work normally with the tools. 

I'm trying to connect to my university server where the user name is same as my user A. Every time I try to scp it from user B for example like: hostname:userB~> scp -r userA@server:/home/userA/directoryToCopy /home/userB/ it FAILS !!! 
It only works if I try hostname:userA~> scp -r userA@server:/home/userA/directoryToCopy /home/userA/. Right now, I'm having to copy all files to user A and then copy back to B and change ownership each time. Any solutions ? Any help in this regard is greatly appreciated. Thank you all.

~Prassanna

---

### Post by p_quarles on 2007-12-02
My hunch is that the hangup here has to do with the permissions on userB's home folder. Your system may be seeing userA's name on the incoming files, and thereby refusing to write them to userB's folder. 

If that's the case, this might be a solution: First, add userA to userB's "group" (each user is both a user and a group):
```
sudo addgroup userA userB
```
Then, you'll probably need to change the permissions on userB's home folder. The default is 755, but you'll want group members to be able to write files to the folder:
```
sudo chmod 775 /home/userB
```
It think this will work, but you might wind up with these files still being owned by userA (user) and userB (group).

---

