---
title: "How to move two user profiles home directories to seperate drives"
date: 2021-11-14
forum: General Help
---

### Post by bobsone on 2021-11-14
Hi
 I am working on an AMD Ubuntu mate 20.04 desktop.
 I am trying to move the home directories of two users (A & B) to individual-separate storage drives.

 I have found a procedure using a TTY prompt that has worked correctly with the home directory of profile A,  [https://www.youtube.com/watch?v=INhYP5piqws](https://www.youtube.com/watch?v=INhYP5piqws)  .

 
 
 However, I have run into a problem when I tried to move profile B’s home directory being that when I try to move the home directory ( **sudo mv /home /home.orig** ) I am informed that it cant be moved because it is busy.  

 
 
 How can I resolve this…


 Any suggestions appreciated

---

### Post by ajgreeny on 2021-11-14
Is ***user B*** logged in?  Are you currently running the system as ***user B***?  Is the ***/home/B*** folder mounted at present?

I've never tried to do what you are doing but I suspect it may be easiest to do everything you are wanting to if using a live system, ie, booting from a USB live OS.

---

### Post by bobsone on 2021-11-15
Thanks for the reply and suggestion algreeny

Yes userB was logged in, working in the TTY prompt I followed the same steps that were successful when I moved the userA home directory.
I haven't yet tried working through the whole process from a live USB.
The live USB tip was useful, I found that when working with userA, I got to the stage where I needed to copy the home directory ( **sudo cp -rp /home/* /mnt/tmp**  ) and as with the TTY prompt it copied both of the users home directories to the new drive. it appears this is why I get the "*cant be moved because it is busy*" message when I move userA and then try to move the home directory of userB.

So after a reinstall I started at the beginning of the instructions, logging in to userA and dropped to the the TTY prompt.  This time I tried adding userA to the relevant parts of the instructions (  e.g.  **sudo cp -rp /home/userA/* /mnt/tmp   **and**               sudo mount /dev/sda1 /home/userA**  etc  ) and set the /etc/fstab accordingly (  e.g.  **/home/userA**  ). This appears to "*almost work*", the userA home folders were on the new drive and the boot to login process looked normal but while the userB login worked, the userA login failed :o 
I then reinstalled and repeated the process, this time only adding userB to the relevant parts of the instructions, I could complete the steps but userB had the same login fail that I had when I tried this with userA.

Any thoughts -ideas are welcome

---

### Post by TheFu on 2021-11-15
Do you have 2 or 3 physical partitions?  
Are you using a volume manager?
If you want 2 users on different storage (partitions or LVs or subvolumes), then you will need a mount entry for each user in the fstab to keep it clean.

a - /  ... this would be where the OS is 
and there would be
 a /home/userA subdirectory, which will be the "mount point" for the file system used by userA 
and
 a /home/userB subdirectory, which will be the "mount point" for the file system used by userB.

Using partitions will almost certainly cause problems in the future, which could be solved by using a volume manager like btrfs, zfs or LVM+ext4.

If you don't want users to have access to any snaps, you can put the users' HOME directories outside /home/.  This  is very common in corporate setups.  There is nothing magical about /home as far as Linux is concerned, it is only snap packages which seem to care.  You can put HOME directories anywhere you like, provided the passwd DB points to the correct location.  /u1/userA and /u2/userB would be examples where /u1 and /u2 are different physical disks with separate partitions.

As long as the storage locations and passwd db match where things are in the directories mounted, that's all that matters.  So LDAP can be used for the passwd DB and NFS storage can be used for the HOME directories, just as easily as the /etc/passwd text file and local partitions. Unix/Linux doesn't care.

---

### Post by bobsone on 2021-11-26
Thanks for the replies
I have 3 drives, one for the OS and the other two for userA and userB home folders. 

I have solved my issue (and used it for a while) by creating two /home folders on partitions on the respective drives during the (Something else) Mate install. I differentiated each /home partition with a username,  /home/usernameA and /home/usernameB, 
Mate then took care of the fstab file for me, assigned the installed /home/usernameA folder to the partiton with the matching name and did the same with the second drives partition ( /home/usernameB) when I created the usernameB profile.

Thanks again for the help
Bob

---

### Post by TheFu on 2021-11-26
Please use the thread-tools button near the top to mark it SOLVED. This helps the community.

Glad you found a solution. Reinstalling seems a little excessive just to avoid adding 2 lines to the /etc/fstab.
Also, please be cautious about using the term "drive" when it is really a "partition".  I honestly hope you didn't mount the entire drive device for each user. If you did, problems are in the future for this setup.

Also, whenever adding new partitions for access, be certain to choose a native file system and format it. Missing that little detail would break attempts by future lurkers trying to recreate the success above.

---

### Post by Tadaen_Sylvermane on 2021-11-27
Another potential solution without needing to enable root or live boot is create a sudo user which has no purpose other than to move what needs moving and then delete this user once all is well. 

I keep an admin user for this exact purpose. It's only used when I'm expecting to do stuff like you mentioned.

---

### Post by bobsone on 2021-11-29
> **TheFu said:**
>  Reinstalling seems a little excessive just to avoid adding 2 lines to the /etc/fstab.
This is true, but this isn't windows... a reinstall only take 20-30 minutes.  The reinstall was because I had been messing with the system and a reinstall is the simplest way (I know of) to get a clean base to organize the system on.

R.e. mounting the entire drive device for each user; If you did, problems are in the future for this setup
uhoh... when I was installing I just pointed the /home/userA etc at the relevant drive.
Am I correct in concluding the home folders are in partitions if they are labeled /dev/sdb1  /dev/sdc1 and running lsblk identifies their Type as "part" ?

---

