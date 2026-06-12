---
title: "[SOLVED] Managed to get my password eaten"
date: 2007-11-21
forum: General Help
---

### Post by CidBahamut on 2007-11-21
I recently changed the password for my account on my Dapper Drake partition. Now the new password seemed to take rather well, seeing as how I was off sudo-ing things a few hours after changing it. However, the next day I tried logging in to find that neither my new password nor my previous password would take. 
Now both of these passwords are ones that I've cycled for years, an unsafe practice to be sure but I know these passwords well enough that I'm certain I didn't mistype them during the login screen or during the changing process.
Currently I find myself locked out of my Linux partition with no obvious means of re-entry.
I think I should note that simultaneously my Windows system registry managed to corrupt itself. Needless to say I was quite panicked before I remembered my backup Fiesty Fawn hard drive.

So, how do I break into my own computer?

---

### Post by jflaker on 2007-11-21
I have had this issue.  If you used the number pad for numbers when changing your password, then you need to use the number pad to sign in.  For some reason, Ubuntu looks at the number pad as different than the number row.

If this works and you can sign in, then change your password again and use the number row.  Once you use the number row, you can THEN use the number pad also........BUG?  Possibly.

---

### Post by mikewhatever on 2007-11-21
First, make sure capslock is not on/off. You can reset the password from the recovery mode, usually the second boot option [https://help.ubuntu.com/community/LostPassword?highlight=%28password%29](https://help.ubuntu.com/community/LostPassword?highlight=%28password%29)

---

### Post by stunner on 2007-11-21
:)

---

### Post by CidBahamut on 2007-11-22
Thank you one and all.
The recovery command line worked like a charm. My system is back up and running. Now all I have to do is figure out how to get ntfs-config and that other one working so I can raid the windows partition, but that's for another thread and after another night of research.

I'm glad my computer blew up and I came here because I learned something from it.

---

