---
title: "Convert to Separate Home"
date: 2016-10-29
forum: General Help
---

### Post by Quarkrad on 2016-10-29
I've just done a clean install on a friends machine and the graphics is sort of messed up - looks like when the caja file manager is launched it is running in low graphics mode, but the Desktop looks OK (apart from the text is a little odd).  Anyway, I may need to reinstall but like a fool I installed everything under /.  As I have done a lot of work updating and configuring is it possible to convert to having a separate / and /home?  Obviously I need to create a new partition - is this feasible/worth it?

---

### Post by Dennis N on 2016-10-29
Yes, it is possible - you can find step-by-step guides. Here is one:
[http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

---

### Post by oldfred on 2016-10-29
This has the procedure to move /home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 
If you have installed lots of apps, best to export list of apps and use it to reinstall all of them.
      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

But I prefer a separate /mnt/data partition with all the user files, so then /home is essentially all the hidden files & folders only. And I move some of the large folders like Firefox & Thunderbird profiles also.
But /home is easier for newer users. It automatically has a mount point, and ownership & permissions. 

If creating a data partition you have to create mount point, edit fstab to automount it, edit ownership & permissions and set a procedures usually linking to use it. Easier for new user just to have /home.

---

### Post by kevdog on 2016-10-29
@oldfred -- I don't get why you recommend a /mnt/data partition?

---

### Post by bearlake on 2016-10-29
Wondering the same as kevdog.

This is my usual setup on one of my drives.

Use something else when you install and select something like so.

From the pic added you can see 2 different OS using the same /home.

Likely oldfred has a good reason for a different setup.

---

### Post by oldfred on 2016-10-29
I consider /mnt/data more advanced, since you have to manually do additional steps. For very new users standard install of / & swap is fine. Then when a bit more experienced, the separate /home makes backup and reinstalls slightly easier.

Main reason is I have many Ubuntu installs. And you should not share /home, but can easily share data.

The /home may have settings that are incompatible across versions. While it may work for a while, eventually you will have issues, unless exactly same install version with same configurations. 

I started with data partitions when sharing with XP, back then it was NTFS and that could not be /home.
But I find tiny /home inside / easy to back up. And I then separately backup my /mnt/data partition.

---

### Post by bearlake on 2016-10-29
> **oldfred said:**
> I consider /mnt/data more advanced, since you have to manually do additional steps. For very new users standard install of / & swap is fine. Then when a bit more experienced, the separate /home makes backup and reinstalls slightly easier.

Main reason is I have many Ubuntu installs. And you should not share /home, but can easily share data.

The /home may have settings that are incompatible across versions. While it may work for a while, eventually you will have issues, unless exactly same install version with same configurations. 

I started with data partitions when sharing with XP, back then it was NTFS and that could not be /home.
But I find tiny /home inside / easy to back up. And I then separately backup my /mnt/data partition.

Many thanks for the good explanation.

---

