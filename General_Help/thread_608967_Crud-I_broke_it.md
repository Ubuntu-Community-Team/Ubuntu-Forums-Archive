---
title: "Crud-I broke it"
date: 2007-11-10
forum: General Help
---

### Post by kreuelt on 2007-11-10
This is what I get for being a newb and trying to be sweet.
So I was messing around with permissions on filefolders while I was logged in as root, and I tried giving my account permission to all the bin, system, boot folders-basically, everything. I went to the permissions dialog, made the changes, and tried to apply them. That took a while, and the dialog box froze up, so I forced quit it and tried to reboot. Voila, it couldn't even load GRUB. A few days later (today) I tried booting up again, and what do you know, it worked. However, when I tried to log in, it let me, but I also got the following error message:

User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $home directory must be owned by user and not writable by other users.

I then tried logged in as root, got the same message. I messed around and tried to fix what I had broken by setting the permissions back to the way they were, but, retarded me, I didn't remember what each folder's default permission setup was. However, I made a few changes, one of them at least worked (allowed me to connect to local wired network, which I hadn't been able to do) and I rebooted. Logged into my account, and everything seemed to be working fine, except for compiz-fusion. So I started up firefox and came here, seeking help.

I'm running Ubuntu 7.04 off an external hard drive (Windows is on the internal) (In case you need that info)
Thanks in advance.

---

### Post by ajgreeny on 2007-11-10
>  So I was messing around with permissions on filefolders while I was logged in as rootWhy on earth did you need to do that in the first place?  This is one of the problems of trying to make things as much like windows as you can ie. everything done as administrator (root).  It can be very dangerous, as you've found out.

If it was my system, I think I would start again from scratch, reinstall, but this time with 7.10, and not mess about with permissions when I'm not sure about the outcome or really what I'm doing.  There is a very good reason for using sudo for root actions and not logging in as root when things can go seriously wrong.

---

### Post by songshu on 2007-11-10
it can be easily fixed.

i agree with poster above, but if you want to play root you might want to read something about file permissions

[http://www.google.nl/search?q=unix+file+permissions&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.nl/search?q=unix+file+permissions&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

