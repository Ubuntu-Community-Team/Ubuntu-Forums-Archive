---
title: "Issues with file permissions / groups"
date: 2020-10-05
forum: General Help
---

### Post by HappyHappyJoy on 2020-10-05
I am running 16.04 64bit.  

I have had the only user account on my computer since installation, my account name is Bob.  I now need to add another user, called Alice, and I'd like to create a folder that we can both access.  I read online and created a new group called "sharedfiles".

$ groups
Bob adm cdrom sudo dip plugdev lpadmin sambashare

Ok, so I'm not in the group "sharedfiles".  

$ sudo usermod -a -G sharedfiles Bob

I type in my password, then nothing happens.  So I check and see what groups I'm in:

$ groups
Bob adm cdrom sudo dip plugdev lpadmin sambashare

No change.  

I read online for a bit - I can't figure out whats happening, so I decide to change tack, and just change "others" permissions for this directory.  There won't be anyone else on the machine and it isnt private. Through nautilus I change "others" permissions and then check in the terminal:

$ ls -l
drwxrwxrwx 2 Bob Bob 20480 Oct  4 18:28 2020 folderIWouldLikeToShare

But when I log into Alice's account - I see no way to view this folder or its contents.  


What am I doing wrong here?  Surely its something very obvious.

Thanks in advance!

---

### Post by TheFu on 2020-10-06
Groups are cached at login unless the program specifically looks for updates. Only group management tools would bother.  After modifying groups, you need to tell the current program running to refresh itself for the group list.  The **newgrp** command does that. Any child process for that terminal where newgrp was run would also see the updated group membership.  It only applies to the current window/shell. 

If you want to to apply everywhere, logout and login again. All future logins will see it as well.

Use the 'id' command to see current group membership.  Or you can just look in the /etc/group file. It is pretty bonehead.

---

### Post by TheFu on 2020-10-06
> **HappyHappyJoy said:**
>  
I read online for a bit - I can't figure out whats happening, so I decide to change tack, and just change "others" permissions for this directory.  There won't be anyone else on the machine and it isnt private. Through nautilus I change "others" permissions and then check in the terminal:

$ ls -l
drwxrwxrwx 2 Bob Bob 20480 Oct  4 18:28 2020 folderIWouldLikeToShare

But when I log into Alice's account - I see no way to view this folder or its contents.  

What am I doing wrong here?  Surely its something very obvious.

Probably obvious.  Go to ~Bob/ however you like ... in a shell, that would be **cd ~Bob**. This would work for any userid on the system, including Bob, though **cd** alone takes the current userid to her/his HOME.

If we make some assumptions that would be common on a typical Ubuntu system, then
```
**cd** === **cd ~** === **cd $HOME** == **cd /home/Bob**
```
Those are all the same for Bob.

For Alice, 
```
**cd ~Bob** === **cd /home/Bob**
```

Don't confuse **cd ~Bob** and **cd ~/Bob**.  Those are completely different places.

So ... now you can enter Bob's HOME as Alice and if Bob is allowing o+rx permissions, then Alice can see a list of files and subdirectories. That doesn't mean write access, just read.

Of you want Bob and Alice to share read-write access to the same directory, the steps are spelled out here: [https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965)

1 more thing, completely unrelated ... well, for now it is.  usernames and groupnames should be all lowercase, begin with a latin alpha character and can contain numbers, but cannot begin with a number.  There are lots of reasons for this, but the main one is that usernames often get compared and if a programmer doesn't perform a case insensitive comparison, then that code will likely fail.  In theory, it shouldn't be any problem, but not all programmers in the world write great code.  There is a mode in Unix systems that if the login username is all capitols, then only capitol letters will be used. This is left over from the 1970s when mainframes were more common and terminals didn't support lowercase.  Again, it may never be an issue, but when it is, nobody will remember this historical fact and things will break.  First time it happened to me, took a few days to figure out.

So ... some problems can just be avoided by doing things a certain way.  All these young whippersnappers programmers don't know these modes or the history.  Or perhaps I missed when it was solved and I'm an out-of-touch old gray-beard?

---

