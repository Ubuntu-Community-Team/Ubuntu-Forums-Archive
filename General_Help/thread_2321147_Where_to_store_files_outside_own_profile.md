---
title: "Where to store files outside own profile?"
date: 2016-04-20
forum: General Help
---

### Post by nodnolse1 on 2016-04-20
Sometime I need to save few important files outside the home folder and often I use the "/home/myextrafiles/" because I don't know exactly which folder are system reserved or may be that the system can delete these files like in "/tmp/" for instance. As well I am afraid to put files in directories that can interfere or disturb the regular system functions. So, does exist a folder candidate to store file securely? Thank for reading and helping, Paolo

---

### Post by Impavidus on 2016-04-20
If you want to put them on a separate partition, it is common to mount it on a subdirectory of /mnt. If you just want to put some files on your root partition, /usr/local would be a safe place. No packages should install themselves there, it's completely free for your own use.

---

### Post by nodnolse1 on 2016-04-20
Thanks, great suggestion even if I'm afraid that once moved from root should be file permissions, groups, share etc symlink that can make few trouble. Basically the idea of "/root/myExtraUserProfileFiles/" it is probably the best for protection etc. Basing on my previous errors I think that I'll use root from now as personal extra store bur I'll always compress each file before to move it, in this manner I'm sure to conserve the original permissions etc. Thanks again, Paolo

PS: Even if this question seem banal and quite stupid, I think that should clear the ideas to many people because the unix-like Filesystem Hierarchy even if I have read about it many times, it is difficult to memorize and totally understand in the real world

---

### Post by Bucky Ball on 2016-04-20
Any symlinks you created to any files you intend to move will be broken when you move the files/folders. The rest should be fine.

I have /home in / but only symlinks in /home linking to folders on another partition on another drive altogether. There are no 'actual' folders in my /home, only symlinks.

---

### Post by bab1 on 2016-04-20
> **nodnolse1 said:**
> Thanks, great suggestion even if I'm afraid that once moved from root should be file permissions, groups, share etc symlink that can make few trouble. Basically the idea of "/root/myExtraUserProfileFiles/" it is probably the best for protection etc. Basing on my previous errors I think that I'll use root from now as personal extra store bur I'll always compress each file before to move it, in this manner I'm sure to conserve the original permissions etc. Thanks again, Paolo

PS: Even if this question seem banal and quite stupid, I think that should clear the ideas to many people because the unix-like Filesystem Hierarchy even if I have read about it many times, it is difficult to memorize and totally understand in the real world
There are a couple of misconceptions here.  All of the file system is one hierarchy starting at  (the root of the file system) the directories below that are all of equal utility.  The only difference is the ownership and permissions of those directories and their subsequent subdirectories.  You get to pick where you place the data.  This means you can create a directory below / such as /data and set the ownership to you (sudo chown <you>:<your-group> /data) and the correct default permissions (sudo chmod 775 /data) .  Then you can place data in it as if it was in your home directory.  Problem solved.

It should be pointed out that the root directory is NOT the same as the root users directory (/root).  The root users directory is the home directory and should not hold your data (e.g. /root/myExtraUserProfileFiles/).  If you want that data stored outside of your home direrctory and protected by root ownership and permissions I would add a directory under / such as /creds or /profiles and make sure the permissions that satisfied your access requirements.

The system is really not hard to understand at all.  It may be new to you but it is simple and logical.  See the [Linux File System Hierarchy ]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") or [these graphics]("https://www.google.com/search?q=linux+file+system+hierarchy&biw=1229&bih=673&tbm=isch&tbo=u&source=univ&sa=X&sqi=2&ved=0ahUKEwjK6-ij6Z7MAhXHPCYKHdZFC8EQsAQIJg").

---

### Post by mcduck on 2016-04-21
I can't really think of any good reason why you'd need to save any personal files outside of your own home if it's still going to be on the same hard drive. Apart from if you wish to hide some files. In which case I'd definitely recommend using something like EncFS instead, as that would give you *actual* security, and also allow keeping the files in your home and accessing them more conveniently.

Take a look at Gnome EncFS Manager for a nice graphical interface for creating & managing EncFS directories:
[https://launchpad.net/gencfsm]("https://launchpad.net/gencfsm")
[http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html]("http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html")

---

### Post by buzzingrobot on 2016-04-21
> **nodnolse1 said:**
> Sometime I need to save few important files outside the home folder and often I use the "/home/myextrafiles/" because I don't know exactly which folder are system reserved or may be that the system can delete these files like in "/tmp/" for instance. As well I am afraid to put files in directories that can interfere or disturb the regular system functions. So, does exist a folder candidate to store file securely? Thank for reading and helping, Paolo

Nothing in your home directory is "system reserved". The "system" will work just fine without your home folder.  You won't, of course.

  Applications you use will store their configuration data in files there.  Your mail client will store your mail messages there. 

You'll need to define "securely", but there's really no upside to storing files you create outside your home folder, plus some downsides.

---

