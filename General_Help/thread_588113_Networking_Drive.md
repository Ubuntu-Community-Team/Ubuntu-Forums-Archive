---
title: "Networking Drive"
date: 2007-10-23
forum: General Help
---

### Post by Ajjw on 2007-10-23
I installed Gusty Gibbon onto a formatted system, with two IDE hard discs.

I want to use my second IDE drive, which is currently unformatted, to use as a storage drive on my wired network of this Ubuntu system and two other Windows platforms.

So I am guessing I format the drive to FAT32? I done that, went to share the drive via the Shared Folders option in Administration, but when I try to access this drive via one of the Windows systems it prompts me to enter a user name and password, I do that, doesn't let me access the drive due to a cannot recognize user name and password error when they are correct. I am using my user name and password I created when installing Ubuntu for the first time.

Second problem, I get a cannot rename error when trying to rename my drive to my desired choice using Partition Editor via Administration.

Any ideas?

Thank you.

---

### Post by mahousaru on 2007-10-23
I don't normally share files via this way, so I am guessing you are sharing via samba. I manually configure my samba shares.  

When setting up samba you need to create a samba password that is tied into a real Linux account

```

sudo smbpasswd -a username

```

It will ask you for a password to access your share via samba and this does not need to match your login password.

Try this to see if it works

*Edit*
Just tested it and once you add a samba password it works.

---

### Post by seventyeights on 2007-10-23
If you are filesharing under linux, the filesystem doesn't matter. However, using a journaled fs like ext3 is better because the files are laid out in a way in anticipation of multiple users.

If you have trouble accessing, try going into smb.conf and change "security=user" to "security=share" (and get rid of that semicolon). I don't know why this isn't done automatically. (Anyone, feel free to warn me if I shouldn't do this).

---

