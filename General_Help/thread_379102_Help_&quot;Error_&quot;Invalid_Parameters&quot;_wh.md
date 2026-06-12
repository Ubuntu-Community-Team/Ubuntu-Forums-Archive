---
title: "Help: &quot;Error &quot;Invalid Parameters&quot; while copying&quot;, &quot;Permissions&quot;"
date: 2007-03-08
forum: General Help
---

### Post by Unoone on 2007-03-08
"Error "Invalid Parameters" while copying.." pops up on all of my three Ubuntu installs. I name my web folders as "link_name", "home_name", etc. Nothing fancy yet later on as I want to backup directories that are full of these named folders to my fat32 drives I get "Error"Invalid parameters" while copying..... " with random folders in a directory.

I can transfer these directories to any of the ext3 drive with no problems. To test for errors I make a new folder with a name similar to the old folder name like-  "link_name" to "linked_name". I then transfer all of the contents from the old folder "link_name" to "linked_name". Now the the folder named "linked_name" copies without error to the fat32 drive.  It's an error that effects the way data is written to ext3 drives.

I'm also getting folder permission errors on certain files that I copy from my fat32 usb drives to ext3 drives. I have to manually give myself permissions on each of these folders. I never had these types of errors in Ubuntu until I installed Edgy. I have to boot to windows and use "Explore2fs" to back up my web work from my ext3 drives. "Explore2fs" is a life saver.  Is there a way to fix these  problems?:(

---

### Post by Unoone on 2007-03-09
The ext3 partitions keep corrupting my file transfers to fat432 drives in my Ubuntu installs. This may be due to some strange "root" permission settings in Ubuntu. I can transfer these same "Error" files with Knoppix to a fat32 drive. So my solution is to stop using ext3 partitions in Ubuntu for important data backup. It's a weird but working solution.:(

In the proccess of digging around for solutions I found out that "root" can't give any "real" "user" write permissions to fat32 drives in Linux. So the "chown", etc commands only work if you let the fstab setting mount the fat32 drives. Commands like "sudo mount -a" must not be performed after setting up a fat32 drive in fstab. You must reboot the computer and let fstab allow the chown settings to take effect. Then your fat32 drive is now under your ownership as user. 

Now that's one I never read in the Ubuntu docs for "basic" newbie level fat32 drive settings. Knowing this would have made my whole life easier. It's a common Linux function. It seems strange that such common Linux fat32 drive information like this is disregarded in the Ubuntu docs.

---

### Post by philidox on 2008-02-25
Look at this post and let me know what you think: [http://ubuntuforums.org/showthread.php?p=4405606#post4405606](http://ubuntuforums.org/showthread.php?p=4405606#post4405606)

---

