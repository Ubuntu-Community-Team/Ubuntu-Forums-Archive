---
title: "Need Assistance W/ CryptSetup (On Live CD)"
date: 2021-02-26
forum: General Help
---

### Post by onlineserv on 2021-02-26
Hello All,
I ne
I have a task where I've been asked to install Ubuntu 18.04 abd Encrypt the system. I'm following this article [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019) and at the point where I need to encrypt the disk, however when running this command cryptsetup luksFormat --type=luks1 ${DEVP}1 I'm met with an error message that basically tells me there is an input/output error. I get the same error when simply typing cryptsetup in a terminal window, which leads me to believe there's an error with the command itself. has anyone seen this before, if so can you provide some insight to this?

---

### Post by TheFu on 2021-02-26
How new to Linux are you? Need to know since there are many possible issues and if you have 5+ yrs as an admin, we won't bother with the simple mistakes.

BTW, you do know that encrypting the system as part of the install takes checking just 1 or 2 checkboxes, right?

---

### Post by HermanAB on 2021-02-26
That '2019' guide looks like a relic from the previous century.  

As mentioned above, installing with full disk encryption is trivial if you just let the installer do its thing.

---

### Post by onlineserv on 2021-02-26
I'm very new, I havent really worked on it till now...and was given this task to setup so I'm basically following the article and ran into a snag. I should also note that I've been instructed to encrypt with luks, not sure if that makes a difference in using the installer vs. doing what i'm trying to do.

---

### Post by HermanAB on 2021-02-26
LUKS == Linux Unified Key Setup

So, no worries, just go ahead.

---

### Post by TheFu on 2021-02-26
> **onlineserv said:**
> I'm very new, I havent really worked on it till now...and was given this task to setup so I'm basically following the article and ran into a snag. I should also note that I've been instructed to encrypt with luks, not sure if that makes a difference in using the installer vs. doing what i'm trying to do.

The intaller uses LUKS.  Just check the box during installation.  This  easy. Don't make it hard.

---

### Post by onlineserv on 2021-02-26
I just went through the install process and nowhere did it make mention of my encyrpting the system. I am installing 18.04LTS. am I missing something?

---

### Post by deadflowr on 2021-02-26
> **onlineserv said:**
> I just went through the install process and nowhere did it make mention of my encyrpting the system. I am installing 18.04LTS. am I missing something?

It should be on this page during the install:
[ATTACH=CONFIG]288019[/ATTACH]

This is an 18.04 install ISO image, ftr.

---

### Post by TheFu on 2021-02-26
> **onlineserv said:**
> I just went through the install process and nowhere did it make mention of my encyrpting the system. I am installing 18.04LTS. am I missing something?

It's there. 

I encrypt all my laptops and have for many years.  Attempting to encrypt the OS after an install is very difficult. Doing during the install is 1 checkbox and crazy easy.

If you don't want to have an install and want encryption for data partitions, we can also help with that. It is pretty easy, provided it isn't the OS or where HOME directories are located. Easy to do. Less easy to access, but you can.

The full OS encryption at install time has lots of added features which makes it good to protect data at rest - i.e. when the system is 100% powered off.  If the system isn't 100% powered off, no encryption is all that great.  It should go without saying, but if any encryption is used, excellent backups are needed.  Any issue with the storage can make access to all the files impossible, so consider yourself warned. If you encrypt, you'll need daily, automatic, versioned, backups. No excuses.

---

