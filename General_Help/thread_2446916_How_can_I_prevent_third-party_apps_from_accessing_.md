---
title: "How can I prevent third-party apps from accessing my personal files ?"
date: 2020-07-09
forum: General Help
---

### Post by EngineerStrange on 2020-07-09
How can I hide my personal files completely in computer so that noone other than me can access them ?

---

### Post by slickymaster on 2020-07-09
Thread reopened

---

### Post by kc1di on 2020-07-09
if you place a . in front of any file name it will be hidden and not show unless you ask the file manager to show hidden files.  Hope this helps. 
So say you have a file named mystuff in your home directory  rename it to .mystuff and it will be hidden.

---

### Post by ajgreeny on 2020-07-09
You need to get to understand unix/Linux permissions, and to simplify things make all your own folders and files unreadable to all except yourself.

Look at all the information at [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) as a start, and then come back here again to ask more specific questions if you have any, which I suspect you might have.  It may all look very complicated at the beginning but there really is no alternative if you have a need to stop others seeing your data.

Of course, any user who fully understands the Linux filesystem would know how to overcome those limitations added by permissions alone, and if you have real concerns and need total security of all data, encryption is the only foolproof answer, though I will have to leave others to discuss that with you as I have never had a need to use it.

---

### Post by ajgreeny on 2020-07-09
Threads merged as they are simply a rewording of the same question.

Please do not duplicate threads about the same query as it is confusing for all and makes it difficult to see where the discussions are going.

---

### Post by C.S.Cameron on 2020-07-09
You can make an encrypted partition, or put them in an encrypted zip file, 7zip works well for that.

---

### Post by GhX6GZMB on 2020-07-09
Change the permissions in your $HOME directory tree. If you remove all rights from "group" and "others" using chmod, no one except yourself can look at the directories and files. This may bring other problems, though.

---

### Post by TheFu on 2020-07-09
> **anuragpaathak said:**
> How can I hide my personal files completely in computer so that noone other than me can access them ?

Who are you trying to prevent from gaining access?  That more than anything else would determine the steps to be taken.  Blocking a 15 yr old is easier than blocking a Unix admin than blocking a nation-state trying to gain access.  

in short, the first is 1 simple thing, the 2nd is 15 careful things, and the last is 30 extremely careful things that you cannot screw up any one or they will gain access.   
So, what amount of hassle is worth the trouble? 
How careful can you be with details?

---

### Post by EngineerStrange on 2020-07-10
Using encryption do you mean that converting it into zip then adding a password?

---

### Post by TheFu on 2020-07-10
> **anuragpaathak said:**
> Using encryption do you mean that converting it into zip then adding a password?

ZIP encryption is pretty hackable, so that wouldn't be the method used except against a 15 yr old.  Because of the way that ZIP passwords are stored, hacking fairly large passwords is easier than for other formats.

When we say encryption, we usually mean dm-crypt + LUKS.  The strength is strong, but can be made effectively uncrackable using 2FA with sufficient length and care for about 15-20 details around the use of LUKS.  I use LUKS with 2FA and increase my paranoia level when traveling internationally, especially to parts of the world where govts don't provide any viable method to sue and win.

---

### Post by Dennis N on 2020-07-10
There is gpg encryption for individual files or collections of files. Ubuntu's file manager (Files) has a gpg plugin that encrypts and decrypts files easily once you set up your encryption key. Otherwise, you need to know the gpg terminal commands. Ubuntu MATE also has this ability with Caja file manager.

---

### Post by TheFu on 2020-07-10
> **Dennis N said:**
> There is gpg encryption for individual files or collections of files. Ubuntu's file manager (Files) has a gpg plugin that encrypts and decrypts files easily once you set up your encryption key. Otherwise, you need to know the gpg terminal commands. Ubuntu MATE also has this ability with Caja file manager.

I can confirm that Caja will recognize LUKS encrypted containers and access file systems inside, including LVM object + file systems. 

However, using this mode in an insecure environment or on an insecure network will allow attackers access to the data, depending on their level of cracking skills and effort they are willing to expend.  From an average 15 yr old, this would be extremely safe. From 50-80% Unix admins, this would be safe.  From a nation-state, well ... which nation and how bad do they want access?

In short, if the system is on any network, including bluetooth or a wireless mouse, all bets are off.

But LUKS access of an ext4 encrypted partition is probably the most secure and most convenient for us normal people provided we aren't foolish.

---

