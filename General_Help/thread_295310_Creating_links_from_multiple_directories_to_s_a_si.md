---
title: "Creating links from multiple directories to s a single directory"
date: 2006-11-07
forum: General Help
---

### Post by madtinkerer on 2006-11-07
Hi,

I want to link the contents of multiple directories to a single directory.  For example, I have 4 users, each with an MP3 directory in their /home directory.  I would like to link those mp3 directories  to a directory in each users' home directory.  Like this

/home/user1/MP3

/home/user2/MP3  --]
/home/user3/MP3  --]-linked to-> /home/user1/OtherMP3
/home/user4/MP3  --]
/home/user5/MP3  --]

Is that possible?  If it is, how does the ln command handle name conflicts between the different directories?

Thanks for the help.

---

### Post by po0f on 2006-11-07
madtinkerer,

Oh, ok, I get what your saying.  You'd be better off just creating a global shared folder, say, in /usr/share/MP3 and just giving everyone write access.

---

### Post by madtinkerer on 2006-11-07
I can't create a globally shared folder because I don't want write access given to all users for all files in the directory.  I just want to make it easier to browse the different directories.  Currently, users have to look in each /home/user* directory to find what they are looking for.  I want to link all those directories to one directory in each users /home/ directory to make browsing those  files easier.

---

### Post by J_Man on 2008-03-30
I'm bumping up this post as I would like to be able to do something similar.
I have Ubuntu running as a media centre in our living room, although it only has a small hard drive.  It would be nice to be able to open a directory called "Music" or "Videos" and have it list the contents of selected directories on the network.  Can it be done?

---

