---
title: "access HFS+ drive to transfer files to Ubuntu"
date: 2014-09-22
forum: General Help
---

### Post by Bhakti108 on 2014-09-22
OK, I trashed my hackintosh today, because I decided to reinstall Ubuntu and have a dual boot. (I moved away from linux six months ago, but haven't been enjoying the experience!) 

So using Mac OSX disk utility I shrank the SSD (system drive) to half its orignal size, and it said it was rebuilding the necessary boot parametres etc. But it woild not boot, and I was totally unable to reinstall or fix the darn thing. 

Long story short, I am over other OS's and want to move back 100% to Ubuntu. I have wiped the entire SSD and installed 14.04 - works a treat!. I have a seperate 3TB drive with my "home" dir from Mac that is of course a HFS+ format. I want to be able to access it and move all my user files to my home directory here, and be able to read/write to thos files on this OS.

Now just to be clear -- I cannot boot mac and change the journaling because the OS no longer exists. What are my other options to access and move my files?

Thanks
Doug

---

### Post by Lars Noodén on 2014-09-22
Have you tried mounting the HFS+ partition as read-only?

---

### Post by Bhakti108 on 2014-09-22
Yes, - I did foind out that there are folders that I created that I can copy, but the folders created by the OS x system, ie Documents, Library, Music etc, cannot be opened or copied because I do not have the correct permissions. ie when created on the hack, the user ID is xxx but the User id in Linux is yyy --- therefore they are not "owned" by me. 

I am not sure of the terminal commands to take ownership etc.

---

### Post by Bhakti108 on 2014-09-22
The problem seems to be that the user ID is 501 and Ubuntu doesn't use any id lower than 1000 -- so the sudo chown command doesn't work. I need to somehow change the user ID of the directory, without having access to a mac. hmmm

Any ideas? (I will start a new thread as well I think, cos its a different subject - sort of)

---

### Post by Lars Noodén on 2014-09-22
> **Bhakti108 said:**
> Yes, - I did foind out that there are folders that I created that I can copy, but the folders created by the OS x system, ie Documents, Library, Music etc, cannot be opened or copied because I do not have the correct permissions. ie when created on the hack, the user ID is xxx but the User id in Linux is yyy --- therefore they are not "owned" by me. 

I am not sure of the terminal commands to take ownership etc.

If the partition is read-only then you cannot take ownership regardless of UID.  However, you could use root to copy the files and directories and then take ownership of what was copied.  It could go something like this:

```

mkdir /home/bhakti/Foo/
cd /home/bhakti/Foo/

sudo rsync -av /meda/path/to/some/hfs/ /home/bhakti/Foo/
sudo chown -R bhakti:bhakti /home/bhakti/Foo/

```

Mind the slash at the end of the paths.

---

### Post by Bhakti108 on 2014-09-28
Solved by taking drive to another mac and changing the dir and files permissions as needed. laborious but it worked. Thanks

---

