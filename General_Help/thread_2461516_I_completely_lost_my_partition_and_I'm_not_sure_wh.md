---
title: "I completely lost my partition and I'm not sure what happened"
date: 2021-05-02
forum: General Help
---

### Post by t5404tmz on 2021-05-02
This is a very strange problem.

I don't know what happened to my partition.  One minute it was there, the next it was gone.  I'm sure it has something to do with my efforts to restore a clonezilla backup to it.  I got a message that partclone failed because "there is not enough free memory..."

I didn't really think that was a big problem, but maybe clonezilla deleted the partition and then had the error.  Here is what gparted says when I look at the information for that partition:
```

Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda7 is missing
```

I've done restores to that partition in the past and I've never had any problem with memory.

And I know I've done some really stupid things in the past which have had major repercussions, but this time I was just strolling along minding my own business and then I fell off a cliff.

Is there any way for me to recover from this?  

One thing I've noticed is that my clonezilla doesn't recognize any of my old backups on my external drives.  I tried two different versions, and I finally was able to see one of the backup files and then this happened when I tried to restore it.

---

### Post by tea for one on 2021-05-02
Assuming that this thread is a consequence of your earlier thread [https://ubuntuforums.org/showthread.php?t=2461299](https://ubuntuforums.org/showthread.php?t=2461299), it is apparent that the chronology of problems is difficult to follow and, therefore, it is almost impossible for forum members to offer suitable help.

Your previous thread did not have a satisfactory solution after 4 days and my gut feeling is that this thread will suffer the same outcome.

The best course of action is:-

Open a live Ubuntu session
Back up all your personal data
Re-install Ubuntu 20.04 (and Windows 10 if required)
Use GPT and UEFI mode throughout.

---

### Post by TheFu on 2021-05-02
I never found cloning to be a useful backup strategy. Too much storage required. Too much downtime. Too many hassles. Too inflexible at re-install time.

---

### Post by HermanAB on 2021-05-02
Cloning the whole kit and kaboodle is basically a Windows thing, where it is difficult to reinstall the system from scratch due to numerous licensing and registration hassles.  

With Linux, just backup your data and when the inevitable happens, install a fresh copy of Linux - it only takes about 20 minutes - then copy your data back from backup.

---

### Post by oldfred on 2021-05-02
I agree and basically follow all of the above advice.

Have you tried testdisk?
And if deeper search shows files, immediately copy to another drive.
If not then photorec may find data, but it takes forever, needs another large drive to copy data into, and only finds files by extension. I had multiple text files, and photorec found them all including deleted copies. Sorting and trying to find most recent or updated tooks weeks. Or now oldfred has better backups.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Other tools
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by t5404tmz on 2021-05-02
I apologize for costing so much time and energy with my grub problem.  It was all the result of an erroneous assumption I made regarding how root files work in a linux environment.  I admit that I was guilty of some fundamental ignorance, but I learned a great deal in the process thanks to the courtesy and support of this forum.  I greatly appreciate all of your time and effort expended to help a foolish man.  And at the end of four days, I was able to solve the original problem of changing my default grub option.

---

### Post by t5404tmz on 2021-05-02
> **HermanAB said:**
> Cloning the whole kit and kaboodle is basically a Windows thing, where it is difficult to reinstall the system from scratch due to numerous licensing and registration hassles.  

With Linux, just backup your data and when the inevitable happens, install a fresh copy of Linux - it only takes about 20 minutes - then copy your data back from backup.

I'm always looking for a better backup system, thanks for the advice.  My concern is that if I don't back up the image, I can reinstall Linux without any problem, but all of my customizations will also have to be reinstalled.  My desktop preferences and all of the additional apps I like to use will have to be reinstalled.

Do you have a work-around idea for that?

Clonezilla has always been there for me and it usually works and doesn't take that long.  In this case, I have no idea what happened, or why my old backups became unreadable, because that is what happened.  It is really strange because it's not just one file.  I have multiple clones I keep on various external drives, and none of them were being detected by Clonezilla.  And this was two different versions of Clonezilla, and multiple external drives.  I did a test backup just to see if I could restore anything, and that worked okay.  I felt like I was in the Twilight Zone.

I'll probably keep using Clonezilla, and back up my files with Back-In-Time.  But I'm open to any suggestions for a more efficient disaster recovery plan.

---

### Post by oldfred on 2021-05-02
/home has all your user settings, mostly in hidden .xxx files. And it has all your user data, unless you also use separate data partition(s). 

If you edit system files in /etc like grub, then you may want to backup /etc also. But typically not restore all if new version as settings may change. I only edit a couple of files in /etc & copy those into /home, so my normal backup includes those.

TheFu has many posts an backups in this forum. Some of his recent posts are here using google search:
site:ubuntuforums.org TheFu  backup

---

### Post by t5404tmz on 2021-05-02
> **oldfred said:**
> /home has all your user settings, mostly in hidden .xxx files. And it has all your user data, unless you also use separate data partition(s). 


So if I do a clean install of ubuntu and just restore my /home backup over it I'll have all my apps and customizations?  Like GIMP, and WPS, and a dozen other apps I like to install?  And if not the apps, will my xfce desktop be restored with my customized panels?

---

### Post by oldfred on 2021-05-02
You have all the settings for your apps.
But you have to export a list of apps to make it easy to reinstall any that you have added.
The new install will have all the normal defaults. Newer versions may add or delete one or two or change a default app.

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by t5404tmz on 2021-05-02
> **oldfred said:**
> You have all the settings for your apps.
But you have to export a list of apps to make it easy to reinstall any that you have added.
The new install will have all the normal defaults. Newer versions may add or delete one or two or change a default app.

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Thanks for the info! 

I was able to restore my partition with TestDisk.  I had to repair the superblock.

I'm guessing that the root cause of my problem is with Clonezilla.  I've opened a ticket on their forum to explore possible solutions.

Thanks for all of your help!  If I resolve my Clonezilla problem, I'll update this thread.

---

