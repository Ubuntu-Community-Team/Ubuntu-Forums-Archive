---
title: "Share partition with all users"
date: 2008-02-27
forum: General Help
---

### Post by SVT_Tour on 2008-02-27
I need to be able to share a partition with all the users on my computer.  This will be just for some documents and things that everyone needs to read and write.  It is my home computer, so not worrying about other malicious users.  I don't want to modify any permissions on individual files.  If I create it, I want my wife to be able to modify it and write it back.  What is the best way to accomplish this?  Ideas I have so far:

1. Make a FAT32 parition and mount with FMASK=777 (I know this would work, just not elegant using a FAT partition)
2. Someway setup group permissions so everyone can read/write each others files because they belong to the same group.

I will be creating a new partition, so pretty much can do anything.  This is Ubuntu 7.10 and a local hard drive.  I tried searching the forum already, but is kind of a vague topic.

Thanks for any help
Andrew

---

### Post by Ardrias on 2008-02-27
Well you could make a new partition and mount in say.... /opt/random/dir

Create a group and give that rights on the directory. Add the users to the group.

---

### Post by SVT_Tour on 2008-03-05
Thanks for the tip.  I did some more searching and found a solution that is just the next step after setting up a group and setting permissions.  It uses access control lists (ACL), detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

I do have one issue with it still.  If I create a file it has "no group" associated with it, so other users can't read it. Just need to work on it more, but I think that is exactly what I was looking for.

---

### Post by opositive on 2008-03-05
Hello,

     A few questions for clarification:

        1. Is this a dedicated Ubuntu machine or are you trying to dual boot to Windows and access the drive from both OSes?
        2. Are you attempting to share this via Samba or just create a shared user area on your disk for all Ubuntu users to use?

Thanks

---

