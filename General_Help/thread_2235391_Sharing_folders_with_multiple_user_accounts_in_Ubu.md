---
title: "Sharing folders with multiple user accounts in Ubuntu 14.04"
date: 2014-07-20
forum: General Help
---

### Post by fEr3UHfnwvmz on 2014-07-20
Hello,

I have been using Ubuntu for several years (at a beginner level) but for the first time I have done a fresh install (14.04) on a new computer with no Windows partition.  My understanding is that it is best to set up user accounts rather than use the admin account for everyday use.  As such, and so that we can access our various internet accounts from our individually customized desktops, I am trying to set up user accounts for my husband and me.  I would like for us both to have access to the same music, documents, and pictures without having to save them twice on the hard drive, and so that we could each edit the same documents from separate accounts.  

My research so far has taught me that the default account (let's call it 'zsmith') that is created at set up is not root but is automatically an adminstrator, and that I need to use it to set up a group (let's call it 'main') with the desired users (let's call them xsmith and ysmith) in it and then give that group "create and delete files" access.  I tried this using the home/zsmith/Documents folder.  Looking under user accounts in settings, it does show that the group has create and delete access but when I log in as xsmith or ysmith, I do not have access to the folder (I can't even see the files in it).  I tried restarting the computer, and I tried creating a separate folder in /home/zsmith called "shareddocuments" in case the preset Documents folder had special restrictions. Neither of these seemed to work.

Perhaps I'm going about this all wrong? Any suggestions?

---

### Post by grahammechanical on 2014-07-20
I have several installations of Ubuntu each on their own partition on both of my hard drives. I also have one very large partition formatted as Ext4 that I call Data (I have given it that label) and I have folders in that Data partition. Each folder has the following permissions

Owner: Root Access: Create and delete files
Group: Root Access: Create and delete files
Others: Access: Create and delete files

And I can read and write to any of the folders and the files in the folders from any installation that I happen to be logged into. I would suggest that you need to do something similar. That is have a Data partition. It is a safer way of having data. We can re-install Ubuntu without risking our data in the /home folder because the data is on a separate partition.

Regards.

---

### Post by oldfred on 2014-07-20
I also think a separate data partition makes sense. I do not think you have to make 2 new users, but just one. Only the admin can use sudo or you can give sudo access also if desired to the second user.

 Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

### Post by fEr3UHfnwvmz on 2014-07-21
I ended up setting up  shared folders at the /home level (as opposed to the /home/zsmith level)  as outlined in the useful links that oldfred provided.  Everything seems to be working well.  Much appreciated!

I  did have a separate data partition on my old computer to share files  between Ubuntu and Windows but I didn't make one at set up this time  because I didn't think that I'd need it given that I don't have Windows  anymore.  In addition, I have now spent many hours setting up the system  (installing software) and transferring all of my files, so I would rather  not do a fresh install right now to create the partition.  I'm sure  there must be a way to create a partition after installation but I don't  have time to research it at the moment.  I use an external hard drive  to back up my data before re-installing Ubuntu, so I'm not too worried about that.  Next time I do an installation, I will set one up.

Thanks very much to you both for your help!

---

