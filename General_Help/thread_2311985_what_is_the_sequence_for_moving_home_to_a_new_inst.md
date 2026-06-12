---
title: "what is the sequence for moving /home to a new install"
date: 2016-01-31
forum: General Help
---

### Post by ross4 on 2016-01-31
My present computer is failing and I have a new-to-me used one which I would like to set up to replace the old one. On the old one one I am using Xubuntu (14.04.3 LTS) and I want to instal this on the new  one along with the various programs I have been using. On the old one I have  “/home”,  “/” and “swap” partitions and intend to set the same up on the new computer.  

 I have used Rsync to backup the /home partition.  
 

 My question regards the sequence of the steps I will have to take.  After I partition the new computer and instal Xubuntu, what should I do first, install the several programs I use (LibreOffice, Firefox, Thunderbird etc.) and then restore the /home from the old computer or the other way around... or does it matter? 

Also, am I correct in assuming that I can simply reverse the rsync command to move the backed up /home (it's on a separate hard drive) into the new /home.

 Regards,

 Ross

---

### Post by bab1 on 2016-02-01
> **ross4 said:**
> My present computer is failing and I have a new-to-me used one which I would like to set up to replace the old one. On the old one one I am using Xubuntu (14.04.3 LTS) and I want to instal this on the new  one along with the various programs I have been using. On the old one I have  “/home”,  “/” and “swap” partitions and intend to set the same up on the new computer.  

 I have used Rsync to backup the /home partition.  
 

 My question regards the sequence of the steps I will have to take.  After I partition the new computer and instal Xubuntu, what should I do first, install the several programs I use (LibreOffice, Firefox, Thunderbird etc.) and then restore the /home from the old computer or the other way around... or does it matter? 

Also, am I correct in assuming that I can simply reverse the rsync command to move the backed up /home (it's on a separate hard drive) into the new /home.

 Regards,

 Ross
I have just done what you are talking about here.  I provisioned 2 machines.  In both cases I installed the OS on the root partition (sda1= /) and the home directory on a separate partition (sda2 = /home).  Both worked fine with no problems after transferring only the data.  Are you aware that the users home directory also holds the personalized configuration files (hidden files)?

You shiuld be aware that the personalized configuration files can affect the user experience.  Some older configuration files will work with the new install.  For instance, I always transfer the saved Thunderbird the .mozilla file to my home directory.  This file holds all of my email data.  I have transfered it 3 times when upgrading from Ubuntu 10.04 to 12.04 and then 14.04.  On the other hand, some configuration files no longer are applicable or are not needed any more due to not installing the application.  The point is, there is no cookie cutter approach to using a users personal configuration files

A sane approach would be to just transfer the backed up data initially (files for docs, pictures, video and music, etc).  Then be prepared to get that users saved older configuration files if needed

---

### Post by SeijiSensei on 2016-02-01
I don't think it matters much whether you transfer /home back before or after you update the software.  As BAB says, your home directory contains a number of personalizations for the software you use, but just installing or updating the associated applications won't touch those files.  They are created when you first run an application, so don't use any applications until you transfer /home back.  If you do, the configuration files created in your home directory will disappear once the old /home partition is mounted on top of them.  I'd install the new system, update the software, then transfer /home.

---

### Post by ross4 on 2016-02-02
Thank you both very much. What you say makes sense. I've run into other problems related to installing Xubuntu on my new/old computer but when I get things working, I'll come back to this thread and up-date it with my experiences.
Cheers,
Ross

---

